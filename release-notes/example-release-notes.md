# RHOAI 2.36 Sprint Release Notes

**Sprint:** December 2025
**Version:** 2.36.0
**Team:** Dashboard Platform Team

---

## UI Features

### Model Comparison View
Compare multiple models side-by-side with unified metrics display.

**Screenshot:** https://i.imgur.com/PLACEHOLDER1.png

- Compare up to 4 models simultaneously
- See performance metrics (latency, throughput, accuracy) in unified view
- Export comparison results as PDF
- Save comparisons for later reference

### Pipeline Visual Editor
Drag-and-drop interface for building ML pipelines without code.

**Screenshot:** https://i.imgur.com/PLACEHOLDER2.png

- Visual node-based editor
- Pre-built component library
- Real-time validation
- One-click pipeline execution
- Auto-generated YAML export

### Deployment Health Dashboard
New health monitoring interface for model deployments.

**Screenshot:** https://i.imgur.com/PLACEHOLDER3.png

- Real-time health status indicators
- Request/response latency graphs
- Error rate monitoring
- Auto-scaling visualization
- Alerting configuration

---

## Platform Improvements

### API Response Time Optimization
Optimized backend queries and caching layer.

- Dashboard load time: 2.1s → 0.8s (62% faster)
- Model list API: 450ms → 120ms (73% faster)
- Search queries: 800ms → 200ms (75% faster)

### Memory Efficiency
Reduced memory footprint for large model catalogs.

- Memory usage for 1000+ models: 2.4GB → 1.1GB (54% reduction)
- Page rendering with large datasets: 40% faster
- Background sync operations: 60% less memory

### Developer Experience
Improved tooling and debugging capabilities.

- API error messages now include request IDs
- New debug logging levels for troubleshooting
- Faster hot-reload in development mode (3x improvement)

---

## Bug Fixes

- Fixed: Model Registry pagination breaking after 100 items
- Fixed: Hardware profile dropdown not showing custom profiles
- Fixed: Workbench connection status not updating in real-time
- Fixed: Chat playground losing context after page refresh

---

## Known Issues

- Model comparison PDF export may timeout for very large models (workaround: export as JSON)
- Pipeline editor drag-and-drop not working in Safari 16.x (use Chrome or Firefox)

---

## Migration Notes

- No breaking changes from 2.35
- New hardware profiles automatically available after upgrade
- Existing pipelines compatible with visual editor
