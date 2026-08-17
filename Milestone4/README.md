# Agentic AI for Franchise Management System with Performance Monitoring Assistance

## FranchiseOps AI

> **An agentic decision-support copilot for multi-outlet franchise networks — grounded, never fabricated.**

**Infosys Springboard Internship — Batch 1**

---

## Table of Contents

* [Program & Team Context](#program--team-context)
* [Overall Project Explanation](#overall-project-explanation)
* [Architecture Overview](#architecture-overview)
* [The 9 Specialised Agents](#the-9-specialised-agents)
* [Authentication, OTP & Security](#authentication-otp--security)
* [Admin Dashboard](#admin-dashboard)
* [Application Screenshots](#application-screenshots)
* [Installation & Run Instructions](#installation--run-instructions)
* [requirements.txt](#requirementstxt)
* [Demo Video](#demo-video)
* [Known Limitations & Future Scope](#known-limitations--future-scope)
* [Acknowledgements](#acknowledgements)

---

## Program & Team Context

### Internship

**Infosys Springboard Internship — Batch 1**

### Mentor

| Name                   | Designation              |
| ---------------------- | ------------------------ |
| **Mohamedsipli M** | **Infosys Springboard Mentor** |

### Team Members

| Name                | Role / What They Built | GitHub Handle        |
| ------------------- | ---------------------- | -------------------- |
| **Shivaram Ponnam** | **AI/ML Model Development**     | **@Shivaram Ponnam** |
| **Kuldeepreddy** | **Admin Dashboard & Data Feed Center**     | **@Kuladeepreddy** |
| **Roshini Rajput** | **UI/Fronted Development**     | **@roshanirr2006-wq** |
| **Bhavya Sree** | **Authentication and Login Module**     | **@bhavyasreegujjula** |
| **Boddu Mounika** | **System Integration & Analytics**     | **@Mounika-boddu** |


# Overall Project Explanation

## Problem Statement

Managing a franchise network with multiple outlets requires continuous monitoring of workforce performance, outlet revenue, inventory, marketing campaigns, customer feedback and compliance.

Traditional dashboards mainly display historical information but do not always help managers understand **why a problem is occurring, which area requires attention, or what action could be considered next**.

**FranchiseOps AI** addresses this problem by combining operational data, machine-learning model comparisons, interactive analytics, an AI Copilot, multilingual SOP translation, document analysis and administrative monitoring in a single Streamlit-based application.

## Solution Summary

FranchiseOps AI provides a central decision-support platform for franchise owners, managers, staff and administrators. The application reads operational information from a SQLite database and routes business questions to the appropriate intelligence module. Specialised agents provide analytics and predictions for workforce, outlets, inventory, marketing, customer sentiment and compliance. An AI Copilot can generate responses using retrieved application data and contextual information rather than relying only on free-form generation.

The application also includes authentication, role-based access, OTP-based password recovery, an Admin Dashboard, multilingual translation, PDF/SOP analysis, operational alerts and reporting utilities.

---

# Architecture Overview

The project follows a layered architecture:

<img width="462" height="508" alt="Screenshot 2026-08-17 143107" src="https://github.com/user-attachments/assets/09a03296-cd6a-425c-8cb8-6b12ca2336ac" />


### Architecture Diagram

The final repository should contain the exported architecture image here:
<img width="1536" height="1024" alt="Image Aug 17, 2026, 12_56_35 AM" src="https://github.com/user-attachments/assets/57617161-61d4-48f0-94b5-b7a770d33f69" />


---

# Technology Stack

| Layer             | Technology                          | Purpose                                          |
| ----------------- | ----------------------------------- | ------------------------------------------------ |
| Frontend          | Streamlit                           | Interactive web application and dashboards       |
| UI Navigation     | Streamlit Option Menu               | Application navigation                           |
| Data Processing   | Python, Pandas, NumPy               | Data processing and analytics                    |
| Database          | SQLite                              | Local operational data storage                   |
| Machine Learning  | Scikit-learn                        | Classification, regression and anomaly detection |
| Visualisation     | Plotly                              | Interactive charts and analytics                 |
| Maps              | Folium, Streamlit-Folium            | Outlet/location visualisation                    |
| LLM               | Qwen2.5-Coder-1.5B-Instruct         | AI Copilot and executive assistance              |
| LLM Runtime       | PyTorch, Transformers               | Model loading and inference                      |
| Translation       | NLLB-200 distilled 600M             | Multilingual SOP/text translation                |
| API Layer         | FastAPI                             | Optional local model/translation service         |
| Authentication    | JWT/session-oriented Streamlit flow | User authentication and session management       |
| Password Security | bcrypt / hashing support            | Credential protection                            |
| Email             | Gmail SMTP                          | OTP delivery                                     |
| PDF Processing    | pdfplumber                          | PDF text extraction                              |
| Reporting         | ReportLab                           | PDF report generation                            |
| Environment       | Google Colab / Local Python         | Development and execution                        |

---

# Key Differentiators

### Grounded AI Assistance

The AI Copilot receives operational context from the application's database and business modules before generating responses.

### Transparent ML Comparison

Several agents display comparative model-performance tables so that users can see how different models perform instead of receiving an unexplained prediction.

### Role Awareness

The application supports different user roles and provides different levels of access.

### Fail-Soft AI Design

The application can continue displaying operational analytics while the LLM service is loading or unavailable.

### Multilingual Support

Agent 8 provides multilingual SOP and text translation using the NLLB-200 model.

### Document Intelligence

Agent 9 allows users to upload PDF, TXT and Markdown documents and search their extracted content.

---

# The 9 Specialised Agents

## Agent Overview

| Agent      | Business Function                        |
| ---------- | ---------------------------------------- |
| 👥 Agent 1 | Workforce & Retention Intelligence       |
| 🏬 Agent 2 | Outlet Expansion & Revenue Analytics     |
| 📦 Agent 3 | Inventory & Supply Chain Intelligence    |
| 📢 Agent 4 | Marketing & Campaign Intelligence        |
| 💬 Agent 5 | Customer Sentiment & Feedback            |
| 📋 Agent 6 | Audit, Compliance & FSSAI Safety         |
| 📧 Agent 7 | Executive Franchise Intelligence Digest  |
| 🌐 Agent 8 | Multilingual SOP Translation             |
| 📄 Agent 9 | PDF SOP & Franchise Agreement RAG Studio |

---

## Agent 1 — Workforce & Retention Intelligence
<img width="1912" height="888" alt="image" src="https://github.com/user-attachments/assets/969c2ff3-a29f-4a84-9c7d-7604b86c288b" />

**Business function:** Employee workforce analysis and attrition-risk monitoring.

The agent reads from the `staff` table and analyses employee salary, overtime, job satisfaction, role and predicted attrition probability.

### ML Model Comparison

The application displays a 10-model comparison:

* Random Forest Classifier — **96% Accuracy / 95% F1 — Optimal Best**
* Gradient Boosting Classifier
* Logistic Regression
* Support Vector Classifier
* Decision Tree Classifier
* MLP Neural Network
* Multinomial Naive Bayes
* K-Means Cluster Classifier
* Ridge Classifier
* Isolation Forest Outlier Guard

**Selected model:** Random Forest Classifier.

**Selection reason:** It has the highest displayed Accuracy and F1 Score in the application's comparative model table.

### Data

Primary source:

```text
staff
```

### Outputs

* Attrition-risk KPIs
* Role-wise attrition chart
* Salary vs job-satisfaction analysis
* High-risk employee roster
* ML model comparison chart
* Retention/compensation simulator
* AI workforce advisory

---

## Agent 2 — Outlet Expansion & Revenue Analytics
<img width="1906" height="910" alt="image" src="https://github.com/user-attachments/assets/3962113c-52c0-4831-93e9-58ce5f5bae88" />

**Business function:** Franchise outlet performance, revenue and margin analysis.

The agent reads from the `outlets` table and calculates revenue, operating costs, customer satisfaction and net margin.

### ML Model Comparison

* Random Forest Regressor — **R² 0.96 — Optimal Best**
* Gradient Boosting Regressor
* Linear Regression
* Ridge Regression
* Lasso Regression
* Support Vector Regressor
* Decision Tree Regressor
* MLP Neural Network
* K-Means Cluster Model
* Isolation Forest Outlier Guard

**Selected model:** Random Forest Regressor.

**Selection reason:** It has the highest displayed R² score in the model comparison.

### Data

```text
outlets
```

### Outputs

* Outlet revenue analysis
* Operating-cost comparison
* Revenue and CSAT visualisation
* Tier performance matrix
* Revenue prediction comparison
* Outlet expansion simulator
* Payback-period calculation
* AI outlet advisory

---

## Agent 3 — Inventory & Supply Chain Safety Stock Intelligence
<img width="1912" height="917" alt="image" src="https://github.com/user-attachments/assets/7e0f7d54-b4d4-41d3-8681-4624e8fcc31c" />

**Business function:** Inventory monitoring, stockout-risk analysis and safety-stock planning.

The agent reads from the `inventory` table.

### ML Model Comparison

* Random Forest Regressor — **R² 0.95 — Optimal Best**
* Gradient Boosting Regressor
* Linear Regression
* Ridge Regression
* Lasso Regression
* Support Vector Regressor
* Decision Tree Regressor
* MLP Neural Network
* K-Means Cluster Model
* Isolation Forest Outlier Guard

**Selected model:** Random Forest Regressor.

**Selection reason:** It has the highest displayed R² score in the comparison table.

### Data

```text
inventory
```

### Outputs

* Current stock analysis
* Weekly-demand analysis
* Stockout-risk ledger
* Stockout prediction model comparison
* Safety-stock calculation
* Reorder-point calculation
* Holding-cost simulation
* AI inventory advisory

---

## Agent 4 — Marketing AI & Campaign Intelligence

<img width="1902" height="903" alt="image" src="https://github.com/user-attachments/assets/0616d155-c6ef-4453-ba2f-1c5f449ef1b6" />

**Business function:** Marketing campaign performance, ROI and customer-acquisition analysis.

The agent reads from the `marketing` table and calculates campaign-level CAC using budget and conversions.

### ML Model Comparison

* Random Forest Regressor — **R² 0.94 — Optimal Best**
* Gradient Boosting Regressor
* Linear Regression
* Ridge Regression
* Lasso Regression
* Support Vector Regressor
* Decision Tree Regressor
* MLP Neural Network
* K-Means Cluster Model
* Isolation Forest Outlier Guard

**Selected model:** Random Forest Regressor.

**Selection reason:** It has the highest displayed R² score in the comparison table.

### Data

```text
marketing
```

### Outputs

* Channel ROI comparison
* Campaign spend vs conversions
* Campaign ledger
* ROI model comparison
* Marketing budget simulator
* Customer Acquisition Cost analysis
* AI marketing advisory

---

## Agent 5 — Customer Sentiment & Feedback Analytics

<img width="1880" height="791" alt="image" src="https://github.com/user-attachments/assets/a600b5b8-e264-48f9-b961-8c60adaf58fd" />
<img width="1917" height="867" alt="image" src="https://github.com/user-attachments/assets/09ffd678-d614-4f5c-9ac0-9dabacf39b91" />

**Business function:** Customer feedback, sentiment and service-quality analysis.

The agent reads from the `feedback` table and also provides real-time text analysis.

### ML Model Comparison

The application displays a 10-model sentiment comparison:

* Random Forest Classifier — **94% Accuracy / 93% F1 — Optimal Best**
* Gradient Boosting Classifier
* Logistic Regression
* Support Vector Classifier
* Multinomial Naive Bayes
* Decision Tree Classifier
* MLP Neural Network
* Ridge Classifier
* K-Means Cluster Classifier
* Isolation Forest Outlier Guard

**Selected model:** Random Forest Classifier.

**Selection reason:** It has the highest displayed Accuracy and F1 Score.

### Data

```text
feedback
```

### Outputs

* Customer rating distribution
* Sentiment analysis
* Aspect extraction
* Outlet sentiment comparison
* Sentiment model comparison
* CSAT recovery simulator
* Customer feedback ledger
* AI sentiment advisory

---

## Agent 6 — Audit, Compliance & FSSAI Safety Intelligence

<img width="1917" height="906" alt="image" src="https://github.com/user-attachments/assets/d972dfdc-954a-40b6-ae9e-5d3a22d1b4a8" />

**Business function:** Audit monitoring, compliance analysis and anomaly detection.

The agent reads from the `audits` table and provides compliance analysis and FSSAI-related checks.

### ML Model Comparison

* Random Forest Classifier — **96% Accuracy / 95% F1 — Optimal Best**
* Gradient Boosting Classifier
* Logistic Regression
* Support Vector Classifier
* Decision Tree Classifier
* MLP Neural Network
* Naive Bayes Classifier
* K-Means Compliance Cluster
* Linear Ridge Classifier
* Isolation Forest Outlier Guard

**Selected model:** Random Forest Classifier.

**Selection reason:** It has the highest displayed Accuracy and F1 Score.

### Data

```text
audits
```

### Outputs

* Audit-score dashboard
* Compliance pass rate
* Audit ledger
* Isolation Forest anomaly detection
* FSSAI compliance checklist
* Hygiene/penalty simulator
* ML comparison
* AI audit advisory

---

## Agent 7 — Executive Franchise Intelligence Digest

<img width="1917" height="860" alt="image" src="https://github.com/user-attachments/assets/b7b254dd-41ff-4693-af0b-b8f8aeb30fb5" />

**Business function:** Network-wide executive summary.

Agent 7 combines information from the main operational datasets.

### Data

```text
outlets
staff
inventory
marketing
feedback
audits
alerts
```

### Outputs

* Total outlet KPI
* Revenue KPI
* Network CSAT
* Workforce risk
* Inventory stockout risk
* Marketing ROI
* Audit score
* Customer sentiment
* Health gauges
* Outlet-tier performance
* Active-alert summary
* AI-generated executive summary

Agent 7 does not introduce a separate classical ML benchmark. It consumes outputs and KPIs from the other intelligence modules.

---

## Agent 8 — Multilingual SOP Translation

<img width="1897" height="867" alt="image" src="https://github.com/user-attachments/assets/a5d4417c-d342-43a1-ac1a-722a1a15407f" />

**Business function:** Translate franchise SOPs, policies and operational text.

The application uses:

```text
facebook/nllb-200-distilled-600M
```

### Capabilities

* Free text translation
* SOP translation
* Batch translation
* Franchise glossary
* Language selection
* Translation download

Agent 8 uses NLLB-200 rather than a classical classification/regression benchmark.

---

## Agent 9 — PDF SOP & Franchise Agreement RAG Studio

<img width="1917" height="906" alt="image" src="https://github.com/user-attachments/assets/9a3a1495-7502-4723-ba7d-d8ef8782b389" />

**Business function:** Document upload and document-grounded information retrieval.

Users can upload:

* PDF
* TXT
* Markdown

The application extracts document text and indexes it into the application's document knowledge collection.

### Retrieval

The current notebook implements lightweight document retrieval based on text matching and relevance scoring. It should therefore be described as the **current document retrieval implementation**, rather than claiming a production FAISS + sentence-transformers pipeline unless that implementation is added before submission.

### Outputs

* Document upload
* Extracted-text preview
* Document search
* Relevance score
* Retrieved document passages
* SOP and compliance information

---

# Authentication, OTP & Security

## Authentication Flow

The application provides an authentication portal with login, signup and password-recovery functionality.

The intended security flow is:

```text
Signup
   │
   ▼
Login
   │
   ▼
Authenticated Session
   │
   ├───────────────► Application Dashboard
   │
   ▼
Forgot Password
   │
   ▼
OTP Verification
   │
   ├───────────────► Security Question Fallback
   │
   ▼
Password Reset
```

OTP delivery is configured through Streamlit/Colab secrets and Gmail SMTP.

**Never commit real email credentials, passwords, API tokens or `.env` files to GitHub.**

---

## Role-Based Access Control

| Role                | Typical Access                                                     |
| ------------------- | ------------------------------------------------------------------ |
| **Admin**           | Full application, Admin Dashboard, user management and agent suite |
| **Franchise Owner** | Operational agents and AI Copilot                                  |
| **Store Manager**   | AI Copilot and operational functionality                           |
| **Staff**           | AI Copilot and relevant operational functionality                  |

> Verify the exact role-access rules in the final application before submission if the RBAC implementation is changed.

---

# Environment Variables & Secrets

The following secret/configuration values should be supplied through environment variables or platform secrets rather than committed to GitHub.

| Variable                | Purpose                                                                | Where to get it                           |
| ----------------------- | ---------------------------------------------------------------------- | ----------------------------------------- |
| `HF_TOKEN`              | Hugging Face authentication/access token if required                   | Hugging Face account settings             |
| `HUGGINGFACE_TOKEN`     | Alternative Hugging Face token variable                                | Hugging Face account settings             |
| `EMAIL_ID`              | Project OTP sender email                                               | Dedicated project mailbox                 |
| `EMAIL_PASSWORD`        | Gmail App Password used for SMTP                                       | Google Account → Security → App Passwords |
| `JWT_SECRET_KEY`        | JWT/session signing secret if enabled by the final auth implementation | Generate locally                          |
| `FRANCHISEOPS_DATA_DIR` | Optional local data/database directory                                 | Set locally if required                   |

### Generate a local secret

```bash
python -c "import secrets; print(secrets.token_hex(32))"
```

### Security Rules

Never commit:

* Hugging Face tokens
* Kaggle API keys
* Gmail passwords
* Gmail App Passwords
* JWT secrets
* Real `.env` files
* Real personal customer/staff data
* Private database dumps
* Real OTP information

If a secret is accidentally committed, **revoke and regenerate it immediately**. Deleting it from the latest commit is not sufficient because Git history may still contain it.

---

# Admin Dashboard

The application includes an **Admin Dashboard — FranchiseOps Command Center**.

The Admin Dashboard provides:

### Platform KPIs

* Total active outlets
* Total workforce
* Network revenue
* Average customer satisfaction
* Active alerts
* Registered users
* High-attrition staff
* PyTorch accelerator status

### GPU & VRAM Telemetry

* CUDA availability
* GPU device information
* Device count
* VRAM allocation
* VRAM utilisation

### Outlet Map

Interactive map showing franchise outlet locations and revenue-based status indicators.

### User Management

* View registered users
* Create users
* Assign roles
* Manage authorised platform users

### Database Maintenance

* SQLite database maintenance
* VACUUM/optimisation
* Database re-seeding

### Chat Monitoring

* View recent AI Copilot chat history
* Monitor user/role information
* Clear chat history

---

# Application Screenshots

### 1. Login Screen

<img width="938" height="413" alt="Screenshot 2026-08-16 235213" src="https://github.com/user-attachments/assets/303af516-a12c-4a68-92cf-df2ddc2a15c8" />

### 2. Main Dashboard
<img width="932" height="420" alt="Screenshot 2026-08-16 235551" src="https://github.com/user-attachments/assets/f28467b1-2f22-48a7-920e-fd4940bc333d" />
<img width="944" height="412" alt="Screenshot 2026-08-16 235610" src="https://github.com/user-attachments/assets/7ea52f7f-2d4b-46d8-ad05-7c252f9f4d08" />

### 3. Agent Screen
<img width="933" height="419" alt="Screenshot 2026-08-16 235925" src="https://github.com/user-attachments/assets/1420ac52-da00-4d9a-8a7b-ca2024c4c537" />

### 4. AI Copilot
<img width="935" height="416" alt="Screenshot 2026-08-17 000255" src="https://github.com/user-attachments/assets/db2a745f-85af-4090-b0de-cc65a7f77bbd" />


### 5. Admin Dashboard
<img width="926" height="408" alt="Screenshot 2026-08-17 000414" src="https://github.com/user-attachments/assets/febdf920-8b76-4b86-8dcd-8df7db922db8" />

### 6. OTP / Password Recovery
<img width="1600" height="695" alt="WhatsApp Image 2026-08-16 at 8 38 54 PM (1)" src="https://github.com/user-attachments/assets/6e754bc7-1ae2-4c24-8bfa-131f5841c1c6" />

---

# Installation & Run Instructions

## Option 1 — Run Locally

### 1. Clone the repository

```bash
git clone https://github.com/<YOUR-USERNAME>/<YOUR-REPOSITORY>.git
cd <YOUR-REPOSITORY>
```

### 2. Create a virtual environment

#### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

#### Linux/macOS

```bash
python -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure secrets

Create a local `.env` or configure Streamlit/Colab secrets according to the final authentication implementation.

Do **not** upload `.env` to GitHub.

Example:

```bash
cp .env.example .env
```

Then add your own local values.

### 5. Initialise the database

The application includes database initialisation and sample-data seeding through `db.py` and `seed_data.py`.

Run:

```bash
python seed_data.py
```

If using the notebook, execute the cells from top to bottom so that the application files, database and supporting resources are created in the correct order.

### 6. Start Streamlit

```bash
streamlit run app.py
```

The application will normally become available at:

```text
http://localhost:8501
```

---

# Run on Google Colab

The final project is packaged in:

```text
FranchiseOps_AI.ipynb
```

The notebook creates the application files under:

```text
franchise_app/
```

### Recommended execution order

1. Open `FranchiseOps_AI.ipynb`.
2. Run the cells from top to bottom.
3. Install the required Python packages.
4. Configure Google Colab Secrets.
5. Allow Google Drive access if requested.
6. Initialise/seed the SQLite database.
7. Start the model backend if required.
8. Start the Streamlit application.
9. Open the generated Streamlit URL.

### Colab Secrets

Configure project secrets such as:

```text
HF_TOKEN
EMAIL_ID
EMAIL_PASSWORD
```

Never place the actual secret values directly inside the notebook before committing it to GitHub.

---

# Hardware Requirements

The application contains machine-learning and LLM components.

### Recommended

* Python 3.10+
* 8 GB RAM minimum
* 16 GB RAM recommended
* NVIDIA CUDA-capable GPU recommended for faster LLM/translation inference
* Several GB of disk space for model weights and caches

### CPU Mode

The application can run without a CUDA GPU, but LLM and translation operations may be significantly slower.

### Model Runtime

The current final notebook uses:

```text
Qwen/Qwen2.5-Coder-1.5B-Instruct
```

and:

```text
facebook/nllb-200-distilled-600M
```

The project also contains a FastAPI model service for local generation and translation.

---

# Expected Installation Time & Disk Usage

Installation time depends on internet speed, CPU/GPU and whether model weights are already cached.

The LLM and translation models can require **several GB of storage**, especially after downloading model weights and dependencies.

The first model load may take several minutes. Subsequent runs can be faster when cached.

---

# requirements.txt

The repository must contain:

```text
requirements.txt
```

The current notebook includes dependencies for:

* Streamlit
* Streamlit Option Menu
* Streamlit-Folium
* Deep Translator
* Transformers
* PyTorch
* SentencePiece
* Accelerate
* pdfplumber
* ReportLab
* bcrypt
* Flask
* Plotly

### Important final-submission requirement

Before final submission, regenerate `requirements.txt` from a clean virtual environment:

```bash
pip freeze > requirements.txt
```

Then remove packages that are not actually required by the final application and verify the result in a brand-new environment.

All final package versions should be **pinned using `==`**.

Example:

```text
streamlit==<tested-version>
pandas==<tested-version>
numpy==<tested-version>
plotly==<tested-version>
scikit-learn==<tested-version>
torch==<tested-version>
transformers==<tested-version>
```

Do not claim that `requirements.txt` has been clean-venv tested until this has actually been completed.

---

# Operating-System Dependencies

Some environments may require additional system packages.

For video compression:

```text
HandBrake or FFmpeg
```

For PDF processing, the Python application primarily uses `pdfplumber`, but system-level PDF tooling may be required if additional PDF workflows are introduced.

For GPU execution:

```text
NVIDIA driver
CUDA-compatible PyTorch installation
```

must be compatible with the target environment.

---

# Demo Video

Recommended location:





https://github.com/user-attachments/assets/d8e05e07-5ac2-4571-a000-efdb39c2cf2c








### Suggested demo sequence

```text
1. Login
2. Dashboard
3. Forgot Password / OTP flow
4. Workforce or Outlet Agent
5. Inventory/Marketing/Customer Agent
6. AI Copilot grounded question
7. Multilingual translation
8. PDF/document analysis
9. Admin Dashboard
```

### Demo Security

Use a **fresh dummy account**.

Never display:

* Personal Gmail credentials
* Real Gmail inbox
* Real OTP messages
* API tokens
* Hugging Face tokens
* Personal customer information
* Private database information

If the MP4 is larger than GitHub's file limit, host it externally and place the link in this section.

Example:

```markdown
[Watch the FranchiseOps AI Demo](<DEMO-LINK>)
```

---

# Repository Structure

Recommended final repository structure:

```text
franchiseops-ai/
│
├── README.md
├── requirements.txt
├── .env.example
├── .gitignore
│
├── docs/
│   ├── architecture-diagram.png
│   ├── screenshots/
│   │   ├── login.png
│   │   ├── dashboard.png
│   │   ├── agent.png
│   │   ├── copilot.png
│   │   ├── admin-dashboard.png
│   │   └── otp.png
│   │
│   └── demo/
│       └── demo.mp4
│
├── milestone-1/
├── milestone-2/
├── milestone-3/
├── milestone-4/
│
├── app.py
├── auth.py
├── db.py
├── seed_data.py
├── config.py
├── intent_router.py
├── llm_engine.py
├── rag_engine.py
│
├── agent1_franchise.py
├── agent2_franchise.py
├── agent3_franchise.py
├── agent4_marketing.py
├── agent5_sentiment.py
├── agent6_audit.py
├── agent7_digest.py
├── agent8_translation.py
└── agent9_pdf_rag.py
```

The **root `README.md` is the single overall README**.

Milestone-specific README files are optional and supplementary.

---

# `.gitignore`

The repository should contain a `.gitignore` similar to:

```gitignore
# Environment
.env
.env.*
!.env.example

# Python
__pycache__/
*.py[cod]
*.pyo
*.pyd

# Jupyter
.ipynb_checkpoints/
*.ipynb_checkpoints

# Virtual environments
venv/
.venv/
env/

# Databases
*.db
*.sqlite
*.sqlite3

# Runtime data
runtime_data/
*.log

# Model/cache files
.cache/
huggingface/
hf_models/

# Secrets
secrets.toml
.streamlit/secrets.toml

# OS
.DS_Store
Thumbs.db

# IDE
.vscode/
.idea/
```

---

# `.env.example`

Commit only variable names/placeholders.

Example:

```env
HF_TOKEN=
HUGGINGFACE_TOKEN=

EMAIL_ID=
EMAIL_PASSWORD=

JWT_SECRET_KEY=

FRANCHISEOPS_DATA_DIR=
```

Never commit the real `.env`.

Verify that Git ignores it:

```bash
git check-ignore -v .env
```

---

# Security Warning Before Git Push

The final repository must be searched for:

```text
password
token
secret
api_key
key
EMAIL_ID
EMAIL_PASSWORD
HF_TOKEN
```

Use:

```bash
git grep -n -i "password"
git grep -n -i "token"
git grep -n -i "secret"
```

and inspect notebooks as well as Python source files.

### Critical

The current development notebook contains demo authentication credentials in its sample-data seeding logic.

**Those credentials must be removed or replaced with a secure environment/secret-based mechanism before the notebook or generated source files are pushed to the public repository.**

Do not rely on deleting the visible line after committing it. If credentials were previously committed, rotate/revoke them and clean the Git history where appropriate.

---

# Known Limitations & Future Scope

## Current Limitations

1. **Synthetic/demo data**
   The project uses generated/sample franchise datasets for demonstration and development.

2. **SQLite database**
   SQLite is suitable for a demonstration or small deployment but is not the ideal production database for a large multi-user franchise network.

3. **Local model execution**
   LLM and translation performance depends heavily on available CPU/GPU hardware.

4. **Document retrieval implementation**
   The current notebook provides a lightweight document retrieval implementation. A production deployment can replace it with a fully persistent vector database and embedding-based retrieval pipeline.

5. **Single application deployment**
   The current architecture is primarily designed around a Streamlit application and local/Colab execution.

## Future Improvements

1. Migrate SQLite to PostgreSQL or another production-grade database.

2. Add a production vector database and embedding-based RAG pipeline.

3. Introduce automated model training pipelines with real historical franchise data.

4. Deploy the LLM and AI services using scalable cloud infrastructure.

5. Add advanced monitoring, observability and automated model-performance tracking.

6. Integrate real-time enterprise data sources such as POS, ERP, inventory and CRM systems.

7. Strengthen production authentication with enterprise SSO/OAuth and more comprehensive RBAC policies.

---

# Acknowledgements

We sincerely thank **Infosys Springboard** for providing the internship opportunity, learning environment and project platform.

We also thank our mentor **Mohamedsipli M**, **Infosys Springboard Mentor**, for guidance, technical feedback and continuous support throughout the project.

---


# FranchiseOps AI

### Agentic AI for Franchise Management System with Performance Monitoring Assistance

**Infosys Springboard Internship — Batch 1**

> **An agentic decision-support copilot for multi-outlet franchise networks — grounded, never fabricated.**

