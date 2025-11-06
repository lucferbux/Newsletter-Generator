# RHOAI 2.35 - What's New

**Release Date:** January 15, 2025  
**Version:** 2.35.0  
**Type:** Major Feature Release

---

## Release Highlights

RHOAI 2.35 introduces exciting new features that make managing AI models easier and faster. This release focuses on helping you organize, discover, and deploy models with less effort.

### ✨ What's New

- 📝 **Model Registry** - Keep track of all your model versions in one place
- 📚 **Model Catalog** - Browse and deploy pre-trained models instantly
- 🧩 **Component Marketplace** - Extend your workflows with custom components
- ⚡ **40% Faster Dashboard** - We've optimized everything for speed
- 🎨 **Improved UI** - Cleaner interface with better navigation

---

## 📝 Model Registry

**Organize and version your models like a pro**

The new Model Registry helps you keep track of every version of your models, making it easy to deploy, roll back, or compare different versions.

### What You Can Do

✅ **Track Versions** - Every model change is saved automatically

✅ **Search Easily** - Find models by name, tags, or custom metadata

✅ **See Deployment History** - Know which versions are deployed where

✅ **Roll Back Instantly** - Quickly revert to previous versions if needed

✅ **Collaborate** - Share models across your team

### How to Use It

1. **Register a Model**
   - Navigate to "Model Registry" in the dashboard
   - Click "Register New Model"
   - Upload your model file or connect to your cloud storage
   - Add descriptive tags (like "production", "fraud-detection", "v2")
   - Click "Register" - done!

2. **Deploy a Registered Model**
   - Browse your registered models
   - Select the version you want to deploy
   - Click "Deploy"
   - Choose your deployment settings (resources, replicas)
   - Your model is live!

3. **Track and Compare**
   - View deployment history in the model details page
   - See performance metrics and usage statistics
   - Compare different versions side-by-side
   - Roll back to any previous version with one click

**Screenshot:** *Model Registry dashboard showing registered models with version tags, deployment status, and quick action buttons*

---

## 📚 Model Catalog

**Start faster with pre-trained models**

Browse hundreds of pre-trained models ready to deploy. No need to train from scratch - find a model that fits your use case and get started in minutes.

### Available Models

| Category | Examples | What You Can Do |
|----------|----------|-----------------|
| **Computer Vision** | ResNet50, EfficientNet, YOLO v8 | Classify images, detect objects, analyze visual content |
| **Natural Language** | BERT, GPT-2, T5 | Analyze text, build chatbots, translate languages |
| **Tabular Data** | XGBoost, LightGBM | Make predictions, classify data, analyze patterns |
| **Time Series** | LSTM, Prophet | Forecast trends, detect anomalies, predict values |

### How to Deploy from Catalog

1. **Browse the Catalog**
   - Go to "Model Catalog" in the navigation
   - Use filters to find models by category, framework, or task
   - Click on any model to see details and performance metrics

2. **Deploy Instantly**
   - Click "Deploy" on your chosen model
   - Configure deployment settings (CPU, memory, replicas)
   - Click "Deploy Model"
   - Get your endpoint URL immediately
   - Start making predictions!

3. **Test Your Model**
   - Use the built-in testing tool
   - Send sample data and see results
   - Verify everything works before going live

### Model Performance Metrics

Every validated model shows real performance data so you know what to expect:

- ⚡ **TTFT (Time to First Token)** - How quickly responses start streaming
- 📊 **Throughput** - How many predictions per second
- ✅ **Accuracy** - Validated performance scores on test datasets
- 💻 **Resource Usage** - Required CPU, memory, and GPU

**Screenshot:** *Model Catalog showing validated models with performance badges, filter sidebar, and deploy buttons*

---

## 🧩 Component Marketplace

**Extend your workflows with custom components**

The Component Marketplace lets you discover and install community-created components to enhance your ML pipelines without writing code.

### What You Can Do

✨ **Browse Components** - Explore data processors, validators, and custom operators

⚡ **One-Click Install** - Add components to your workspace instantly

🔧 **Create Your Own** - Build and share components with the community

📊 **Manage Versions** - Update components without breaking existing pipelines

### Popular Components

**Data Validators**
- Automatically check data quality before training
- Detect missing values, outliers, and inconsistencies
- Save time with pre-built validation rules

**Custom Preprocessors**
- Clean and transform data your way
- Apply custom transformations without coding
- Reuse preprocessing steps across projects

**Model Evaluators**
- Get advanced metrics and visualizations
- Compare multiple models side-by-side
- Generate reports automatically

**Integration Connectors**
- Connect to external services (Salesforce, Snowflake, etc.)
- Stream data from APIs
- Export results to dashboards

### Installing a Component

1. Go to "Component Marketplace"
2. Search or browse available components
3. Click "Install" on any component
4. The component appears in your workspace
5. Use it in your pipelines immediately - no setup required!

**Screenshot:** *Component Marketplace showing featured components with ratings, install counts, and one-click install buttons*

---

## ⚡ Performance Improvements

**Everything is faster**

We've optimized the dashboard from top to bottom. Here's what you'll notice:

### Speed Improvements

| What You're Doing | Before | After | Improvement |
|-------------------|--------|-------|-------------|
| Opening the dashboard | 2.5s | 1.5s | **40% faster** |
| Loading model lists | 850ms | 320ms | **62% faster** |
| Viewing model details | 450ms | 180ms | **60% faster** |
| Searching the catalog | 1200ms | 450ms | **63% faster** |

### What This Means for You

- **Faster Navigation** - Switch between pages instantly, no waiting
- **Quicker Searches** - Find models in milliseconds instead of seconds
- **Smoother Experience** - Everything feels snappier and more responsive
- **Better Productivity** - Spend less time waiting, more time working

**No setup required** - these improvements are automatic when you upgrade!

---

## 🎨 User Experience Enhancements

**Easier to use, nicer to look at**

We've redesigned key parts of the dashboard to make your daily workflow smoother and more intuitive.

### What's Improved

🎯 **Cleaner Interface**
- Simplified navigation menu - find what you need faster
- Better visual hierarchy - important info stands out
- Consistent spacing and alignment throughout
- Less clutter, more focus on your work

📱 **Mobile-Friendly**
- Responsive design works great on tablets
- Touch-optimized controls for touchscreens
- Better readability on smaller screens
- Review models and deployments on the go

🔍 **Smarter Search**
- See results instantly as you type
- Advanced filters that are easy to use
- Save your favorite searches for quick access
- Search across models, deployments, and projects

⚡ **Faster Actions**
- Quick deploy buttons right on model cards
- Batch operations - deploy multiple models at once
- New keyboard shortcuts for power users
- Fewer clicks to get things done

### New Keyboard Shortcuts

Save time with these handy shortcuts:

- `Cmd/Ctrl + K` - Quick search (find anything instantly)
- `G then M` - Go to Model Registry
- `G then C` - Go to Model Catalog  
- `N` - Create new model or deployment
- `?` - Show all available shortcuts

**Screenshot:** *New dashboard interface showing cleaner design, improved navigation menu, and modern card layouts*

---

## 🎓 Getting Started

### For New Users

**Your First Steps:**

1. **Log in to RHOAI Dashboard** - Use your OpenShift or Kubernetes credentials
2. **Explore the Model Catalog** - Find a pre-trained model to try (we recommend starting with image classification)
3. **Deploy Your First Model** - Follow the simple deployment wizard
4. **Make Predictions** - Use the provided endpoint URL to test your model

**Estimated time:** 10-15 minutes from login to your first working model!

### For Existing Users

**Check Out These New Features:**

- **Migrate to Model Registry** - Move your existing models for better organization and version control
- **Browse the Catalog** - Discover pre-trained models you might not know about
- **Try the Marketplace** - Install components to improve your existing workflows
- **Update Your Bookmarks** - We've reorganized the navigation for better usability

### Learning Resources

📚 **Full Documentation** - [docs.redhat.com/rhoai/2.35](https://docs.redhat.com/rhoai/2.35)

🎥 **Video Tutorials** - [youtube.com/@redhatopenshift](https://youtube.com/@redhatopenshift)
   - "Getting Started with RHOAI 2.35" (15 min)
   - "Model Registry Deep Dive" (20 min)
   - "Deploying from the Model Catalog" (10 min)

💬 **Community Forum** - [discuss.redhat.com/c/rhoai](https://discuss.redhat.com/c/rhoai)
   - Ask questions and get help from the community
   - Share your use cases and solutions
   - Request new features

🐛 **Report Issues** - [github.com/red-hat-data-services/rhoai/issues](https://github.com/red-hat-data-services/rhoai/issues)

---

## 🔮 What's Coming Next

### Planned for RHOAI 2.36 (February 2025)

🤖 **Gen AI Studio**
- Chat playground for testing language models in real-time
- Compare multiple models side-by-side
- Save and share your best prompts
- No code required - just chat and test!

📊 **Advanced Analytics Dashboard**
- Real-time insights into model performance
- Drift detection alerts
- Usage analytics and cost tracking
- Custom reports and visualizations

🔄 **Visual Pipeline Builder**
- Drag-and-drop workflow designer
- Build ML pipelines visually - no code needed
- Reusable pipeline templates
- Share pipelines with your team

🌐 **Multi-Region Deployment**
- Deploy models closer to your users globally
- Automatic failover and load balancing
- Centralized management for all regions

### Looking Further Ahead (Q1 2026)

- **A/B Testing Platform** - Test model versions with real traffic
- **AutoML Integration** - Automated model training and tuning
- **Cost Optimization Tools** - Recommendations to reduce cloud costs
- **Federated Learning Support** - Train on distributed data securely

### We Want Your Feedback!

Help us prioritize! Tell us:
- Which upcoming features are you most excited about?
- What problems do you face today that we should solve?
- What features would make your job easier?

**Share your thoughts:**
- Join our [community forum](https://discuss.redhat.com/c/rhoai)
- Email us at rhoai-feedback@redhat.com
- Vote on feature requests in [GitHub Discussions](https://github.com/red-hat-data-services/rhoai-dashboard/discussions)

---

## 📞 Support & Resources

### Need Help?

**📚 Documentation**
- User Guide: [docs.redhat.com/rhoai/2.35/guide](https://docs.redhat.com/rhoai/2.35/guide)
- Tutorials: [docs.redhat.com/rhoai/2.35/tutorials](https://docs.redhat.com/rhoai/2.35/tutorials)
- FAQ: [docs.redhat.com/rhoai/2.35/faq](https://docs.redhat.com/rhoai/2.35/faq)

**💬 Community Support**
- Community Forum: [discuss.redhat.com/c/rhoai](https://discuss.redhat.com/c/rhoai)
- Slack Channel: #rhoai-dashboard
- Stack Overflow: Tag your questions with `rhoai`

**🎫 Enterprise Support**
- Red Hat Support Portal: [access.redhat.com/support](https://access.redhat.com/support)
- Open a support case for priority assistance
- 24/7 support available for critical issues

**🎥 Video Resources**
- YouTube Channel: [youtube.com/@redhatopenshift](https://youtube.com/@redhatopenshift)
- Webinar recordings and demos
- Office hours - live Q&A every Thursday at 2pm ET

### Stay Updated

**📰 Newsletter**
- Subscribe to RHOAI updates
- Monthly feature highlights
- Tips and best practices

**🐦 Social Media**
- Follow [@RedHatAI](https://twitter.com/RedHatAI) on Twitter
- Join our LinkedIn group
- Watch for announcements on the Red Hat Blog

---

## 📋 Upgrade Checklist

### Before You Upgrade

- [ ] Review these release notes completely
- [ ] Check platform requirements (Kubernetes 1.25+, OpenShift 4.12+)
- [ ] Test the upgrade in a staging environment first
- [ ] Back up your data and configurations
- [ ] Schedule a maintenance window (typical downtime: 5-10 minutes)
- [ ] Notify your users about the planned upgrade

### After Upgrading

- [ ] Verify the dashboard loads correctly
- [ ] Test key features (model deployment, registry access)
- [ ] Check that your existing models still work
- [ ] Enable new features (Model Registry, Catalog, Marketplace)
- [ ] Share this newsletter with your team!
- [ ] Explore new features and provide feedback

### Rollback Plan

If you encounter issues, you can easily roll back to the previous version. Detailed rollback instructions are available in the [upgrade documentation](https://docs.redhat.com/rhoai/2.35/upgrade).

---

## 🎉 Thank You!

Thank you for using RHOAI! This release represents months of work from our team and valuable feedback from our community.

**Special thanks to:**
- Our community contributors who submitted feedback and feature requests
- Beta testers who helped us find and fix issues early
- Everyone who participates in our forums and discussions

**Built with ❤️ by the Dashboard Platform Team**  
Red Hat OpenShift AI

---

**Questions? Feedback? Ideas?**  
We'd love to hear from you: rhoai-feedback@redhat.com

**Stay Connected:**
- 🌐 Website: [redhat.com/rhoai](https://redhat.com/rhoai)
- 💬 Forum: [discuss.redhat.com/c/rhoai](https://discuss.redhat.com/c/rhoai)
- 🐙 GitHub: [github.com/red-hat-data-services/rhoai-dashboard](https://github.com/red-hat-data-services/rhoai-dashboard)
- 📧 Email: rhoai-dashboard@redhat.com
