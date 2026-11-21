# 3-Month Roadmap: Intermediate Machine Learning for Software Engineers

**Assumptions:** You can code comfortably (Python helps), and you can commit roughly 6-8 hours per week. The goal is working exposure, not mastery: by the end you should be able to frame a problem, build and evaluate a model, and know which areas to dive into.

---

## Month 1: Foundations and Classical ML

**Goal:** Build the mental model of how ML works and get fluent with the standard toolkit.

### Weeks 1-2: Tooling and math essentials
- Python data stack: NumPy, pandas, Matplotlib
- Just-enough math: vectors and matrices, derivatives and gradients, probability basics (distributions, Bayes' rule), mean/variance
- Resource: Andrew Ng's *Machine Learning Specialization* (Course 1), 3Blue1Brown's linear algebra and neural network videos

### Weeks 3-4: Core supervised learning
- Linear and logistic regression, decision trees, random forests, gradient boosting (XGBoost/LightGBM)
- The ML workflow: train/validation/test splits, cross-validation, overfitting vs. underfitting, bias-variance tradeoff
- Metrics: accuracy, precision/recall, F1, ROC-AUC, RMSE
- Resource: *Hands-On Machine Learning* (Géron), early chapters; scikit-learn docs

**Mini-project:** Predict something from a tabular dataset (e.g., house prices or customer churn from Kaggle). Compare at least three models and justify your choice using proper validation.

---

## Month 2: Deeper Modeling and Deep Learning

**Goal:** Move beyond tabular data and understand how neural networks work.

### Weeks 5-6: Feature engineering and unsupervised learning
- Feature engineering, encoding categoricals, scaling, handling missing data and imbalanced classes
- Regularization (L1/L2), hyperparameter tuning
- Clustering (k-means), dimensionality reduction (PCA, t-SNE/UMAP)

### Weeks 7-8: Neural networks
- Backpropagation, activation functions, optimizers (SGD, Adam), batch size and learning rate
- Build a small network from scratch in NumPy once, then move to PyTorch
- CNNs for images; basics of text embeddings
- Resource: fast.ai *Practical Deep Learning*, Karpathy's *Neural Networks: Zero to Hero*

**Mini-project:** Train an image classifier or text classifier using transfer learning (a pretrained model fine-tuned on a small dataset).

---

## Month 3: Modern ML and Production Exposure

**Goal:** Touch the areas that matter most in industry today and learn how models live in real systems.

### Weeks 9-10: Transformers and LLMs
- Attention mechanism, transformer architecture at a conceptual level
- Using Hugging Face: pretrained models, tokenizers, fine-tuning
- Embeddings, semantic search, and retrieval-augmented generation (RAG)
- Prompting and evaluating LLM outputs

### Weeks 11-12: MLOps and a capstone
- Experiment tracking (MLflow or Weights & Biases), model serving (FastAPI), containerizing with Docker
- Monitoring, data drift, reproducibility, versioning data and models
- **Capstone:** Build and deploy an end-to-end project, such as a semantic search app over your own documents, or a prediction API with a simple front end. Write a short README covering data, approach, metrics, and limitations.

---

## Key Skills to Study Further for Depth

| Area | Why it matters | Go deeper with |
|---|---|---|
| **Statistics and experimentation** | Underpins evaluation, A/B testing, and sound conclusions | Causal inference, Bayesian methods, hypothesis testing |
| **Deep learning theory** | Debugging and designing architectures | Optimization, regularization, *Deep Learning* (Goodfellow) |
| **NLP and LLMs** | Highest demand right now | Fine-tuning (LoRA), evaluation, agents, RAG systems |
| **Computer vision** | Distinct tooling and techniques | Object detection, segmentation, diffusion models |
| **MLOps and ML systems design** | Where software engineers have an edge | Feature stores, pipelines, scaling, *Designing Machine Learning Systems* (Huyen) |
| **Recommender systems** | Common production use case | Matrix factorization, two-tower models, ranking |
| **Reinforcement learning** | Specialized but growing | Sutton & Barto, policy gradients |
| **Data engineering** | Most ML failures are data failures | SQL, Spark, data quality and pipelines |

---

## Tips for Making It Stick

1. **Build more than you watch.** Aim for roughly 70% hands-on time. Each mini-project teaches more than another lecture.
2. **Use Kaggle** for datasets, notebooks, and benchmarks to compare against.
3. **Write as you go.** A short blog post or README per project forces understanding.
4. **Lean on your engineering strengths.** Testing, version control, and clean code make your ML work more reproducible than most beginners'.
5. **Pick a specialization by Month 3.** Whichever project you enjoyed most is a good signal for where to go deep next.