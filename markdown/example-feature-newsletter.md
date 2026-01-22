# RHOAI 2.36 - What's New in This Sprint

**Sprint:** December 2025
**Version:** 2.36.0
**Team:** Dashboard Platform Team

---

## Sprint Highlights

This sprint brings powerful new tools for comparing models, building pipelines visually, and monitoring deployment health. Plus major performance improvements across the board!

### ✨ New This Sprint

- 🔍 **Model Comparison View** - Compare multiple models side-by-side
- 🎨 **Pipeline Visual Editor** - Build ML pipelines with drag-and-drop
- 📊 **Deployment Health Dashboard** - Monitor your models in real-time
- ⚡ **62% Faster Dashboard** - Optimized performance everywhere
- 💾 **54% Less Memory** - More efficient handling of large catalogs

---

## 🔍 Model Comparison View

**Compare models side-by-side to make better decisions**

No more switching between tabs! The new comparison view lets you evaluate up to 4 models at once with unified metrics.

### What You Can Do

✅ **Compare Multiple Models** - View up to 4 models side-by-side

✅ **Unified Metrics** - See latency, throughput, and accuracy in one view

✅ **Export Results** - Download comparisons as PDF or JSON

✅ **Save Comparisons** - Keep your analysis for later reference

✅ **Share with Team** - Send comparison links to colleagues

### How to Use It

1. **Open Model Catalog** → Browse available models
2. **Select Models** → Check the boxes on models you want to compare (up to 4)
3. **Click "Compare"** → Opens the comparison view
4. **Analyze Metrics** → Review performance side-by-side
5. **Export or Save** → Keep your findings

### Perfect For

- Choosing between similar models for production
- Evaluating model upgrades before deployment
- Creating documentation for model selection decisions
- Team discussions about model tradeoffs

![Model comparison view showing 3 models with performance metrics](https://i.imgur.com/PLACEHOLDER1.png)

---

## 🎨 Pipeline Visual Editor

**Build ML pipelines without writing code**

The new visual editor makes pipeline creation intuitive. Drag components, connect them, and run your pipeline with one click.

### What You Can Do

✅ **Drag-and-Drop Design** - Build pipelines visually

✅ **Component Library** - Pre-built blocks for common tasks

✅ **Real-Time Validation** - Catch errors before running

✅ **One-Click Execution** - Run pipelines instantly

✅ **YAML Export** - Get generated code for advanced use

### How to Use It

1. **Go to Pipelines** → Click "Create Pipeline"
2. **Open Visual Editor** → Switch to visual mode
3. **Add Components** → Drag from the component library
4. **Connect Nodes** → Draw lines between inputs and outputs
5. **Configure Each Step** → Click nodes to set parameters
6. **Validate** → Check for errors with the validate button
7. **Run** → Execute your pipeline

### Perfect For

- Quickly prototyping ML workflows
- Non-developers building data pipelines
- Visualizing complex pipeline logic
- Teaching pipeline concepts to new team members

![Pipeline visual editor with connected nodes](https://i.imgur.com/PLACEHOLDER2.png)

---

## 📊 Deployment Health Dashboard

**Monitor your models in real-time**

Stay on top of your deployed models with the new health dashboard. See request patterns, latency trends, and error rates at a glance.

### What You Can Do

✅ **Real-Time Status** - See deployment health instantly

✅ **Latency Graphs** - Track response times over time

✅ **Error Monitoring** - Catch issues before users do

✅ **Auto-Scaling View** - Watch replicas scale up and down

✅ **Alert Configuration** - Set up notifications for issues

### How to Use It

1. **Navigate to Deployments** → Select a deployed model
2. **Open Health Tab** → View the health dashboard
3. **Review Metrics** → Check latency, throughput, errors
4. **Set Alerts** → Configure notification thresholds
5. **Monitor** → Keep the dashboard open or check periodically

### Perfect For

- Production model monitoring
- Identifying performance degradation
- Capacity planning decisions
- Incident response and debugging

![Deployment health dashboard with metrics graphs](https://i.imgur.com/PLACEHOLDER3.png)

---

## ⚡ Platform Performance Improvements

**Everything runs faster and uses less memory**

We've optimized the entire platform for speed and efficiency. These improvements apply automatically - no action needed!

### Speed Improvements

| What You're Doing | Before | After | Improvement |
|-------------------|--------|-------|-------------|
| Opening the dashboard | 2.1s | 0.8s | **62% faster** |
| Loading model lists | 450ms | 120ms | **73% faster** |
| Running search queries | 800ms | 200ms | **75% faster** |

### Memory Efficiency

| Scenario | Before | After | Improvement |
|----------|--------|-------|-------------|
| Catalog with 1000+ models | 2.4 GB | 1.1 GB | **54% reduction** |
| Large dataset rendering | Baseline | 40% faster | **40% improvement** |
| Background sync ops | Baseline | 60% less | **60% reduction** |

### Developer Experience

- 📋 **Better Error Messages** - API errors now include request IDs for easier debugging
- 🔧 **Debug Logging** - New logging levels for troubleshooting
- 🔄 **Faster Hot-Reload** - 3x faster refresh in development mode

---

## 🎓 Getting Started

### Try These Features Now

1. **Compare Your Models**
   - Go to Model Catalog
   - Select 2-3 models and click "Compare"
   - Explore the unified metrics view

2. **Build a Visual Pipeline**
   - Navigate to Pipelines → Create Pipeline
   - Try the visual editor mode
   - Drag a few components and connect them

3. **Check Deployment Health**
   - Open any active deployment
   - Click the Health tab
   - Set up an alert threshold

---

**Dashboard Platform Team**
Red Hat OpenShift AI
rhoai-dashboard@redhat.com
