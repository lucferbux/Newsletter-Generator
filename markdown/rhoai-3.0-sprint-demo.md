# RHOAI 3.0 - What's New in This Sprint

**Sprint:** November 2025  
**Version:** 3.0.0 Development Preview  
**Team:** Dashboard Platform Team

---

## Sprint Highlights

This sprint brings exciting new capabilities to RHOAI 3.0! We've focused on making AI development easier, faster, and more intuitive. Here's what's new.

### ✨ New This Sprint

- 🤖 **Gen AI Chat Playground** - Test language models in real-time
- 📓 **Notebooks 2.0** - Redesigned workbench management
- 🔧 **Hardware Profiles** - Simplified GPU configuration
- 🚀 **Model Deployment Wizard** - Deploying models is easier than ever
- 📊 **Model Catalog Filters** - Find the perfect model faster
- 🗂️ **Feature Store Integration** - Connect workbenches to your data

---

## 🤖 Gen AI Chat Playground

**Chat with AI models directly in the dashboard**

Test language models without writing code! The new chat playground lets you experiment with prompts, compare models, and fine-tune settings all in one place.

### What You Can Do

✅ **Try Different Models** - Switch between Granite, Llama, and more

✅ **Adjust Settings** - Control temperature, max tokens, and other parameters

✅ **Save Conversations** - Keep track of your best prompts and responses

✅ **Compare Responses** - See how different models answer the same question

✅ **RAG** - Add Retrieval-Augmented Generation by connecting to document stores

### How to Use It

1. **Open Gen AI Studio** → Click "Chat Playground" in the navigation
2. **Select a Model** → Choose from available AI models or MaaS providers
3. **Start Chatting** → Type your prompt and see real-time responses
4. **Tune Settings** → Adjust temperature, max tokens, and system prompts
5. **Save & Share** → Export your conversation or share with teammates

### Perfect For

- Testing prompts before production deployment
- Comparing model quality and speed
- Prototyping chatbot conversations
- Learning what different models can do

![Chat playground interface showing conversation with GPT-4 and model settings panel](https://imgur.com/EOLq9A2.png)

---

## 📓 Notebooks 2.0

**Workbench management made simple**

We've completely redesigned the notebooks experience with better status tracking, hardware profiles, and connection management.

### What's New

🎯 **Clear Status Indicators**

- See exactly what state your workbench is in
- Starting, Running, Stopping, Stopped - no more guessing!
- Error states show helpful troubleshooting tips

💻 **Hardware Profile Integration**

- Select GPU configurations from dropdown
- See resource allocation at a glance
- No more manual YAML editing

🔗 **Connection Management**

- Attach databases, S3 buckets, and Git repos
- Visual connection indicators
- Easy setup wizards for each connection type

### Using Notebooks 2.0

**Starting a Workbench:**

1. Navigate to "Workbenches" in your project
2. Click your workbench name
3. Hit the "Start" button
4. Watch the status change from "Starting" to "Running"
5. Click "Open" when ready

**Configuring Hardware:**

1. Click "Edit" on any workbench
2. Select a hardware profile from the dropdown
3. Preview resource allocation (CPU, Memory, GPU)
4. Save and restart

**Adding Connections:**

1. In workbench settings, go to "Connections"
2. Click "Add Connection"
3. Choose type (Database, S3, Git)
4. Fill in connection details
5. Connection is automatically available in your notebook

![Workbench card showing status badge, hardware profile, and connection count](https://imgur.com/mRzQGaF.png)

---

## 🔧 Hardware Profiles (General Availability)

**GPU configuration without the complexity**

Hardware Profiles are now GA! Configure GPU, CPU, and memory allocations with pre-built templates instead of writing YAML.

### What Are Hardware Profiles?

Pre-configured resource templates that you can apply to workbenches and model deployments. Think of them as presets for different hardware needs.

### Available Profiles

| Profile | CPU | Memory | GPU | Best For |
|---------|-----|--------|-----|----------|
| **Small** | 2 cores | 8 GB | - | Development, testing |
| **Medium** | 4 cores | 16 GB | 1x NVIDIA T4 | Training small models |
| **Large** | 8 cores | 32 GB | 1x NVIDIA A100 | Training large models |
| **XLarge** | 16 cores | 64 GB | 4x NVIDIA A100 | Distributed training |

### Creating Custom Profiles

1. Go to "Settings" → "Hardware Profiles"
2. Click "Create Hardware Profile"
3. Fill in display name and description
4. Set CPU, memory, and GPU requirements
5. Choose visibility (workbenches, model serving, or both)
6. Save

### Using Profiles

**For Workbenches:**

- Create new workbench → Select hardware profile → Done!

**For Model Serving:**

- Deploy model wizard → Hardware step → Select profile → Continue

![Hardware profile selection dropdown showing available profiles with resource details](https://imgur.com/xnZowuj.png)

---

## 🚀 Model Deployment Wizard

**Deploying models is easier than ever**

The new deployment wizard walks you through every step of deploying a model, from selection to going live.

### The 5 Steps

**Step 1: Select Model Details**
- Choose model runtime from a list
- Add a connection to get the stored model

**Step 2: Configure Model Deployment**
- Set deployment name and description
- Select hardware profile for serving
- Define autoscaling parameters (min/max replicas)
- Set environment variables if needed

**Step 3: Advance settings & Deploy**
- Add authentication
- Configure playground settings
- Review and confirm deployment


### After Deployment

✅ **Get Endpoint URL** - Copy your model's API endpoint

✅ **Test It** - Use built-in testing tool

✅ **Monitor** - Watch request counts and latency

✅ **Scale** - Adjust replicas as needed

![Deployment wizard showing step 3 with autoscaling configuration](https://imgur.com/EOLq9A2.png)

---

## 📊 Model Catalog Filters

**Find the perfect model faster**

We've enhanced the model catalog with advanced filters and performance metrics so you can find exactly what you need.

### New Filters

🔍 **Search by:**

- Category (Vision, NLP, Time Series, etc.)
- Provider (Hugging Face, OpenAI, Meta)
- Framework (PyTorch, TensorFlow, ONNX)
- Performance (Latency, Throughput)
- Validation status

### Performance Metrics

Each validated model now shows:

**Speed Metrics:**

- ⚡ **TTFT** - Time to First Token (how quickly it responds)
- 🔄 **ITL** - Inter-Token Latency (streaming smoothness)
- 📈 **Throughput** - Tokens per second

**Quality Badges:**

- ✅ **Validated** - Tested and approved
- 🏆 **Recommended** - Top performers in category
- 🔥 **Popular** - Most deployed by users

### Using Filters

1. Go to "Model Catalog"
2. Click "Filters" in the sidebar
3. Select categories, providers, or frameworks
4. Set performance requirements (optional)
5. Click "Apply Filters"
6. Browse filtered results

![Model catalog showing filter sidebar and model cards with performance badges](https://imgur.com/crWOG6D.png)

---

## 🗂️ Feature Store Integration

**Connect workbenches to your feature store**

Automatically generate Python code to connect your notebooks to feature store repositories. No more manual configuration!

### What This Does

The feature store integration generates a ready-to-use Python script that connects your workbench to your feature store, loads entities and feature views, and gets you started with example code.

### How It Works

1. **Connect Your Repository**
   - Enter your feature store repository URL
   - Select entities and feature views to include

2. **Choose Your Workbench**
   - Pick which notebook needs access
   - The integration will inject the connection

3. **Generated Script Includes:**
   - Feature store initialization
   - Entity loading code
   - Feature view setup
   - Example queries to get you started

4. **One-Click Deploy**
   - Click "Inject into Workbench"
   - Script is automatically added to your notebook
   - Start using features immediately

![Feature store integration UI showing repository connection and generated script preview](https://imgur.com/oh5BTIK.png)

---

## 🎯 Navigation Improvements

**Find what you need faster**

We've reorganized the navigation menu with clearer sections and better grouping.

### New Navigation Structure

**AI Hub**

- Model Catalog
- Model Registry

**Gen AI Studio**

- Chat Playground
- Prompt Library (coming soon)

**Develop & Train**

- Projects
- Workbenches
- Data Connections

**Deploy**

- Model Deployments
- Endpoints

![New navigation menu showing organized sections](https://imgur.com/8oLYegW.png)

---

## 🎓 Getting Started

### Try These Features Now

1. **Test the Chat Playground**
   - Go to Gen AI Studio → Chat Playground
   - Pick a model and start chatting
   - Try adjusting temperature and max tokens

2. **Create a Workbench with Hardware Profiles**
   - Projects → Create Workbench
   - Select a hardware profile (try "Medium")
   - See how easy GPU configuration can be

3. **Browse Model Catalog with Filters**
   - Model Catalog → Filters
   - Select "Computer Vision" category
   - Check out the performance metrics

---

**Dashboard Platform Team**  
Red Hat OpenShift AI  
rhoai-dashboard@redhat.com
