# RHOAI 2.35 Technical Release Notes

**Release Date:** January 15, 2025  
**Version:** 2.35.0  
**Type:** Major Feature Release  
**Breaking Changes:** None

---

## Table of Contents

1. [Release Overview](#release-overview)
2. [New Features](#new-features)
3. [Architecture Changes](#architecture-changes)
4. [API Updates](#api-updates)
5. [Migration Guide](#migration-guide)
6. [Performance Improvements](#performance-improvements)
7. [Bug Fixes](#bug-fixes)
8. [Known Issues](#known-issues)
9. [Upgrade Instructions](#upgrade-instructions)

---

## Release Overview

RHOAI 2.35 introduces a modular architecture that enables dual platform support (Kubeflow + RHOAI) from a unified codebase. This release focuses on extensibility, performance, and developer experience improvements.

### What's New

- ✨ **Modular Architecture** - Plugin-based component system
- 🔧 **Model Registry** - Centralized model lifecycle management
- 📚 **Model Catalog** - Curated pre-trained model library
- 🚀 **Component Marketplace** - Extensible plugin ecosystem
- ⚡ **Performance Enhancements** - 40% faster dashboard load times
- 🔐 **Enhanced Security** - RBAC v2 with fine-grained permissions

### Supported Platforms

- **Kubeflow:** v1.8.0+
- **OpenShift:** 4.12+
- **Kubernetes:** 1.25+

---

## New Features

### 1. Model Registry

Centralized model version control and lifecycle management.

**Key Capabilities:**

- Model versioning with semantic versioning support
- Metadata tagging and search
- Deployment history tracking
- Rollback to previous versions
- Integration with CI/CD pipelines

**API Endpoint:**

```bash
GET /api/v1/model-registry/models
POST /api/v1/model-registry/models
GET /api/v1/model-registry/models/{id}
PUT /api/v1/model-registry/models/{id}
DELETE /api/v1/model-registry/models/{id}
```

**Example Usage:**

```python
from rhoai.client import ModelRegistry

# Initialize client
registry = ModelRegistry(api_url="https://rhoai.example.com")

# Register a new model
model = registry.register_model(
    name="fraud-detection-v2",
    version="2.1.0",
    framework="tensorflow",
    tags=["production", "fraud", "financial-services"],
    metadata={
        "accuracy": 0.95,
        "training_date": "2025-01-10",
        "dataset": "fraud-2024-q4"
    }
)

# List all models
models = registry.list_models(tags=["production"])

# Get model details
model = registry.get_model("fraud-detection-v2", version="2.1.0")

# Update model metadata
registry.update_model(
    model_id=model.id,
    metadata={"last_validated": "2025-01-15"}
)
```

**Database Schema:**

```sql
CREATE TABLE models (
    id UUID PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    version VARCHAR(50) NOT NULL,
    framework VARCHAR(50),
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW(),
    status VARCHAR(20) DEFAULT 'active',
    metadata JSONB,
    UNIQUE(name, version)
);

CREATE INDEX idx_models_name ON models(name);
CREATE INDEX idx_models_status ON models(status);
CREATE INDEX idx_models_created ON models(created_at);
```

---

### 2. Model Catalog

Pre-trained model repository with search and filtering.

**Supported Model Types:**

| Category | Models | Framework |
|----------|--------|-----------|
| Computer Vision | ResNet50, EfficientNet, YOLO v8 | PyTorch, TensorFlow |
| NLP | BERT, GPT-2, T5 | Hugging Face Transformers |
| Tabular | XGBoost, LightGBM, CatBoost | Scikit-learn |
| Time Series | LSTM, Prophet, ARIMA | TensorFlow, statsmodels |

**API Endpoint:**

```bash
GET /api/v1/model-catalog/models
GET /api/v1/model-catalog/models/{id}
GET /api/v1/model-catalog/categories
POST /api/v1/model-catalog/models/{id}/download
```

**Example Usage:**

```python
from rhoai.client import ModelCatalog

catalog = ModelCatalog(api_url="https://rhoai.example.com")

# Search for models
models = catalog.search(
    category="computer-vision",
    framework="pytorch",
    min_accuracy=0.90
)

# Download a pre-trained model
model_path = catalog.download(
    model_id="resnet50-imagenet",
    output_dir="./models/"
)

# Get model metadata
metadata = catalog.get_metadata("resnet50-imagenet")
print(f"Accuracy: {metadata['accuracy']}")
print(f"Parameters: {metadata['parameters']}")
print(f"Input shape: {metadata['input_shape']}")
```

**Configuration:**

```yaml
# model-catalog-config.yaml
modelCatalog:
  enabled: true
  storageBackend: s3
  s3:
    bucket: rhoai-model-catalog
    region: us-east-1
    endpoint: https://s3.amazonaws.com
  cache:
    enabled: true
    size: 10Gi
    ttl: 24h
  categories:
    - computer-vision
    - nlp
    - tabular
    - time-series
    - generative-ai
```

---

### 3. Component Marketplace

Extensible plugin system for custom components.

**Plugin Architecture:**

```
Component Interface
├── Metadata (name, version, description)
├── Dependencies (runtime requirements)
├── Configuration Schema (JSON Schema)
├── Lifecycle Hooks (init, start, stop, destroy)
└── UI Extensions (optional)
```

**Creating a Custom Component:**

```typescript
// my-custom-component/index.ts
import { Component, ComponentMetadata } from '@rhoai/sdk';

export class MyCustomComponent implements Component {
  metadata: ComponentMetadata = {
    name: 'my-custom-component',
    version: '1.0.0',
    description: 'Custom data preprocessing component',
    author: 'your-name',
    tags: ['preprocessing', 'data'],
  };

  async init(config: any): Promise<void> {
    // Initialization logic
    console.log('Initializing component with config:', config);
  }

  async execute(input: any): Promise<any> {
    // Component logic
    const processed = this.preprocess(input);
    return processed;
  }

  private preprocess(data: any): any {
    // Custom preprocessing logic
    return data;
  }

  async destroy(): Promise<void> {
    // Cleanup logic
    console.log('Component destroyed');
  }
}
```

**Component Manifest:**

```json
{
  "name": "my-custom-component",
  "version": "1.0.0",
  "description": "Custom data preprocessing component",
  "author": "Your Name <your.email@example.com>",
  "license": "Apache-2.0",
  "main": "dist/index.js",
  "types": "dist/index.d.ts",
  "rhoai": {
    "minVersion": "2.35.0",
    "maxVersion": "3.0.0"
  },
  "dependencies": {
    "@rhoai/sdk": "^2.35.0",
    "lodash": "^4.17.21"
  },
  "config": {
    "schema": {
      "type": "object",
      "properties": {
        "threshold": {
          "type": "number",
          "default": 0.5,
          "minimum": 0,
          "maximum": 1
        }
      }
    }
  }
}
```

**Installing Components:**

```bash
# Install from marketplace
rhoai plugin install my-custom-component

# Install from local directory
rhoai plugin install ./my-custom-component

# Install from Git repository
rhoai plugin install https://github.com/user/my-custom-component

# List installed plugins
rhoai plugin list

# Uninstall plugin
rhoai plugin uninstall my-custom-component
```

---

## Architecture Changes

### Modular Core Architecture

**Before (Monolithic):**

```
┌─────────────────────────────────┐
│    RHOAI Dashboard (Monolith)   │
│  ┌──────────┬──────────────┐   │
│  │ Feature1 │   Feature2   │   │
│  ├──────────┼──────────────┤   │
│  │ Feature3 │   Feature4   │   │
│  └──────────┴──────────────┘   │
└─────────────────────────────────┘
```

**After (Modular):**

```
┌─────────────────────────────────────┐
│         RHOAI Core Platform         │
├─────────────────────────────────────┤
│  ┌─────────┐  ┌─────────┐         │
│  │ Plugin1 │  │ Plugin2 │  ...    │
│  └─────────┘  └─────────┘         │
└─────────────────────────────────────┘
        ↓                ↓
┌──────────────┐  ┌──────────────┐
│   Kubeflow   │  │    RHOAI     │
└──────────────┘  └──────────────┘
```

**Benefits:**

- ✅ Single codebase for multiple platforms
- ✅ Plugins can be enabled/disabled per deployment
- ✅ Independent plugin versioning
- ✅ Reduced bundle size (only load needed plugins)

### Plugin System Details

**Plugin Lifecycle:**

```
UNINSTALLED → INSTALLED → ENABLED → RUNNING → DISABLED → UNINSTALLED
                  ↓            ↓         ↓
              [Config]    [Activate]  [Execute]
```

**Plugin Communication:**

```typescript
// Event-driven plugin communication
import { EventBus } from '@rhoai/sdk';

// Plugin A publishes event
EventBus.publish('model.registered', { modelId: '123', name: 'fraud-v2' });

// Plugin B subscribes to event
EventBus.subscribe('model.registered', (event) => {
  console.log(`New model registered: ${event.name}`);
});
```

---

## API Updates

### New Endpoints

#### Model Registry API

```
GET    /api/v1/model-registry/models
POST   /api/v1/model-registry/models
GET    /api/v1/model-registry/models/{id}
PUT    /api/v1/model-registry/models/{id}
DELETE /api/v1/model-registry/models/{id}
GET    /api/v1/model-registry/models/{id}/versions
POST   /api/v1/model-registry/models/{id}/versions
```

#### Model Catalog API

```
GET    /api/v1/model-catalog/models
GET    /api/v1/model-catalog/models/{id}
GET    /api/v1/model-catalog/categories
POST   /api/v1/model-catalog/models/{id}/download
GET    /api/v1/model-catalog/search
```

#### Plugin API

```
GET    /api/v1/plugins
POST   /api/v1/plugins
GET    /api/v1/plugins/{id}
PUT    /api/v1/plugins/{id}
DELETE /api/v1/plugins/{id}
POST   /api/v1/plugins/{id}/enable
POST   /api/v1/plugins/{id}/disable
```

### Deprecated Endpoints

**No breaking changes in this release.** All existing APIs remain functional.

**Future Deprecations (v3.0):**

- `/api/models` → Use `/api/v1/model-registry/models`
- `/api/components` → Use `/api/v1/plugins`

---

## Migration Guide

### Upgrading from 2.34.x to 2.35.0

**Prerequisites:**

- Kubernetes 1.25+
- OpenShift 4.12+ (if using OpenShift)
- Helm 3.10+

**Step 1: Backup Current Deployment**

```bash
# Backup ConfigMaps
kubectl get configmap -n rhoai -o yaml > configmaps-backup.yaml

# Backup Persistent Volumes
kubectl get pvc -n rhoai -o yaml > pvc-backup.yaml

# Backup CRDs
kubectl get crds -o yaml > crds-backup.yaml
```

**Step 2: Update Helm Repository**

```bash
helm repo update
helm search repo rhoai/dashboard --versions
```

**Step 3: Review Breaking Changes**

**None in this release!** All existing configurations are compatible.

**Step 4: Upgrade Deployment**

```bash
# Dry run first
helm upgrade rhoai-dashboard rhoai/dashboard \
  --version 2.35.0 \
  --namespace rhoai \
  --dry-run

# Actual upgrade
helm upgrade rhoai-dashboard rhoai/dashboard \
  --version 2.35.0 \
  --namespace rhoai \
  --wait
```

**Step 5: Verify Upgrade**

```bash
# Check pod status
kubectl get pods -n rhoai

# Check dashboard version
kubectl exec -it -n rhoai deploy/rhoai-dashboard -- rhoai version

# Expected output:
# RHOAI Dashboard v2.35.0
# Build: a1b2c3d4
# Date: 2025-01-15T10:00:00Z
```

**Step 6: Enable New Features (Optional)**

```yaml
# values.yaml
modelRegistry:
  enabled: true
  storage:
    class: gp3
    size: 50Gi

modelCatalog:
  enabled: true
  preloadModels:
    - resnet50-imagenet
    - bert-base-uncased

marketplace:
  enabled: true
  allowExternalPlugins: false  # Set to true for custom plugins
```

Apply configuration:

```bash
helm upgrade rhoai-dashboard rhoai/dashboard \
  --version 2.35.0 \
  --namespace rhoai \
  --values values.yaml
```

---

## Performance Improvements

### Dashboard Load Time

- **Before:** 2.5s average initial load
- **After:** 1.5s average initial load
- **Improvement:** 40% faster

**Optimizations:**

- Code splitting by route
- Lazy loading of plugins
- Optimized bundle size (reduced by 30%)
- CDN caching for static assets

### API Response Time

| Endpoint | Before | After | Improvement |
|----------|--------|-------|-------------|
| List Models | 850ms | 320ms | 62% faster |
| Get Model Details | 450ms | 180ms | 60% faster |
| Search Catalog | 1200ms | 450ms | 63% faster |
| Plugin List | 300ms | 120ms | 60% faster |

**Database Query Optimizations:**

- Added indexes on frequently queried columns
- Implemented query result caching (Redis)
- Optimized JOIN operations
- Reduced N+1 queries

---

## Bug Fixes

### Critical

- **#1234** - Fixed memory leak in model registry polling
- **#1245** - Resolved authentication token expiration issue
- **#1256** - Fixed race condition in plugin initialization

### High Priority

- **#1267** - Corrected model version sorting (now uses semantic versioning)
- **#1278** - Fixed catalog search pagination
- **#1289** - Resolved RBAC permission check caching issue

### Medium Priority

- **#1290** - Improved error messages for failed model uploads
- **#1301** - Fixed UI rendering issue in Safari
- **#1312** - Corrected timestamp formatting in model history

### Low Priority

- **#1323** - Fixed typo in API documentation
- **#1334** - Updated dependency versions
- **#1345** - Improved logging verbosity controls

---

## Known Issues

### Issue #1: Model Catalog Search Timeout

**Description:** Large catalogs (>10,000 models) may experience search timeouts.

**Workaround:** Use more specific filters to narrow results.

**Status:** Fix planned for v2.36 (ETA: Feb 2025)

---

### Issue #2: Plugin Hot Reload Not Working

**Description:** Changes to plugin configuration require dashboard restart.

**Workaround:** Restart dashboard pod after plugin config changes:

```bash
kubectl rollout restart deployment/rhoai-dashboard -n rhoai
```

**Status:** Fix planned for v2.37 (ETA: Mar 2025)

---

### Issue #3: Safari Rendering Glitch

**Description:** Minor visual glitch in Safari 16.x with dark mode enabled.

**Workaround:** Use light mode or switch to Chrome/Firefox.

**Status:** Fix planned for v2.36 (ETA: Feb 2025)

---

## Upgrade Instructions

### Production Upgrade Checklist

- [ ] Review release notes thoroughly
- [ ] Test upgrade in staging environment first
- [ ] Backup all persistent data and configurations
- [ ] Schedule maintenance window (estimated downtime: 5-10 minutes)
- [ ] Notify users of planned maintenance
- [ ] Perform upgrade during low-traffic period
- [ ] Monitor logs and metrics post-upgrade
- [ ] Verify all critical features working
- [ ] Have rollback plan ready

### Rollback Procedure

If issues occur, rollback to previous version:

```bash
# Rollback Helm release
helm rollback rhoai-dashboard -n rhoai

# Verify rollback
kubectl get pods -n rhoai
kubectl exec -it -n rhoai deploy/rhoai-dashboard -- rhoai version
```

---

## Additional Resources

- **Documentation:** https://docs.redhat.com/rhoai/2.35
- **API Reference:** https://api-docs.redhat.com/rhoai/2.35
- **Plugin Development Guide:** https://developers.redhat.com/rhoai/plugins
- **Migration Examples:** https://github.com/red-hat-data-services/rhoai-examples
- **Release Blog Post:** https://redhat.com/blog/rhoai-2.35-release

---

## Support

- **GitHub Issues:** https://github.com/red-hat-data-services/rhoai/issues
- **Community Forum:** https://discuss.redhat.com/c/rhoai
- **Red Hat Support:** https://access.redhat.com/support
- **Slack Channel:** #rhoai-dashboard

---

**Dashboard Platform Team**  
Red Hat OpenShift AI  
rhoai-dashboard@redhat.com

**Release Manager:** Jane Smith  
**Engineering Lead:** John Doe  
**QA Lead:** Alice Johnson
