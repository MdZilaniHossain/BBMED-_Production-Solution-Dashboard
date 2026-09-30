# 📊 BBMED Final Dynamic Insight Dashboard

An interactive web-based analytics dashboard for **BBMED packaging and production operations**, combining production, MES, Excel, energy, stoppage, staffing, and processing-cost information into a single analytical environment.

The project demonstrates an **end-to-end data analytics workflow**, from raw operational data and data cleaning to interactive dashboard development, GitHub version control, and Vercel deployment.

---

## 📊 Dashboard Preview

<p align="center">
  <img src="./public/project-architecture.png"
       alt="BBMED Project Architecture"
       width="100%">
</p>
The dashboard provides interactive filtering and operational KPIs across:

- Machine
- Product
- Order Size
- MES ↔ Excel status
- Shift
- Production Orders
- Energy & Processing Cost

### Key Operational Indicators

| KPI | Value |
|---|---:|
| Orders | 430 |
| Produced | 11,632,839 units |
| Usage Time | 16,280.2 h |
| Production Time | 5,921.3 h |
| Median Rate | 14.19 u/min |
| Median Availability | 42.4% |
| Median OEE Proxy | 38.6% |
| Matched Excel Orders | 263 |

---

# 🏗️ Project Architecture & Data Workflow

The BBMED project follows a complete analytics pipeline from **raw operational data to a deployed interactive dashboard**.

<p align="center">
  <img src="public/project-architecture.png"
       alt="BBMED Project Architecture and Data Workflow"
       width="100%">
</p>

### End-to-End Architecture

**Data Sources → Data Cleaning & Preparation → Cloud Storage → Dashboard Development → GitHub → Vercel → Live Dashboard**

The cleaned datasets can additionally be analyzed using **Python, SQL/Data Query tools, and AI/Machine Learning**.

### 1️⃣ Data Sources

The analytical process begins with multiple operational data sources:

- Excel files (`.xlsx`)
- CSV files
- Google Sheets
- MES / Production databases
- Manual reports
- Other operational sources

### 2️⃣ Data Cleaning & Preparation

Raw datasets are processed before being used for analysis.

The preparation process includes:

- Removing duplicates
- Handling missing values
- Standardizing formats
- Combining tables
- Creating relationships
- Checking data quality
- Preparing analysis-ready datasets
- Exporting cleaned data

### 3️⃣ Structured Data Storage

Cleaned datasets can be organized centrally into areas such as:

```text
Cleaned Data/
├── Production/
├── Energy/
├── Stoppages/
├── Staff/
└── Products/
```

This creates a structured analytical layer between the original source data and the dashboard.

### 4️⃣ Dashboard Development

The interactive dashboard is developed using:

- HTML
- CSS
- JavaScript
- JSON
- SVG visualizations

The dashboard provides:

- Dynamic KPI cards
- Interactive charts
- Filters
- Operational diagnostics
- MES ↔ Excel comparison
- Energy analysis
- Cost scenarios
- Responsive desktop/mobile design

### 5️⃣ GitHub Version Control

GitHub is used to:

- Store project code
- Track changes
- Maintain version history
- Manage project files
- Support deployment

### 6️⃣ Vercel Deployment

The GitHub repository is connected to **Vercel** for production deployment.

This provides:

- Automatic deployment
- HTTPS
- Static hosting
- Production environment
- Deployment history
- Fast web access

### 7️⃣ Live Dashboard

The final result is a dynamic and interactive web dashboard accessible through a browser.

It supports:

- Interactive KPI monitoring
- Dynamic filtering
- Operational analysis
- Production diagnostics
- Energy analysis
- Mobile and desktop access

### 8️⃣ Advanced Data Analysis

The cleaned datasets can additionally support advanced analytical workflows.

**Python**
- Data processing
- Additional calculations
- Automation
- Reporting
- Data preparation

**SQL / Query Tools**
- Data exploration
- Table relationships
- Data-quality checks
- Analytical queries
- Insight extraction

**AI / Machine Learning**
- Pattern identification
- Trend analysis
- Anomaly detection
- Predictive analysis
- Recommendation generation
- Decision support

---

# 🚀 Active Application

The main page at `/` contains the **BBMED Final Dynamic Insight Dashboard**.

The application contains three major analytical areas.

## 1. Operations & Data Reliability

Production and operational performance analysis including:

- Order-level production
- MES ↔ Excel reconciliation
- Production rate
- Availability
- OEE proxy
- Stoppage analysis
- Order-size effects
- Shift analysis
- Machine analysis

## 2. Energy & Processing Cost

Energy and processing analysis including:

- Meter consumption
- Energy allocation
- Daily energy trends
- Production-energy relationships
- Disturbance percentages
- Idle percentages
- Electricity tariff scenarios
- Processing-cost scenarios

## 3. Calculation / Validation / Model

Provides transparency into:

- Calculation logic
- Data relationships
- Model validation
- Order traces
- Meter relationships
- Data provenance

---

# 📁 Project Structure

```text
BBMED_Packaging_Dashboard/
│
├── index.html
├── app.js
├── styles.css
├── vercel.json
├── README.md
│
├── data/
│   └── dashboard.json
│
├── public/
│   ├── dashboard-preview.png
│   ├── project-architecture.png
│   ├── vercel-deployment.png
│   ├── semantic-model.png
│   └── data-workflow.png
│
├── scripts/
│   ├── build_dashboard_data.py
│   └── build_legacy_dashboard_data.py
│
├── source-data/
│   └── 21.update_energy_data.xlsx
│
├── reference/
│   ├── BBMED_Final_Dynamic_Insight_Dashboard.html
│   └── legacy-dashboard.json
│
└── tests/
```

---

# 🧩 Main Application Files

| File | Purpose |
|---|---|
| `index.html` | Main three-page interactive dashboard |
| `app.js` | Filters, SVG charts, scenarios, order traces and asynchronous data loading |
| `styles.css` | Dashboard styling, accessibility and responsive layout |
| `data/dashboard.json` | Main dashboard analytical dataset |
| `public/semantic-model.png` | Semantic/data relationship model |
| `public/data-workflow.png` | Data workflow diagram |
| `scripts/build_dashboard_data.py` | Python data-build and validation process |
| `vercel.json` | Vercel deployment configuration |

There are **no npm dependencies, external chart services, or runtime database connections**.

The browser loads the required JSON dataset and PNG assets locally.

---

# 💻 Run the Dashboard Locally

Clone or download the repository and open a terminal inside the project directory.

Run:

```bash
python -m http.server 8080 --bind 127.0.0.1
```

Then open:

```text
http://127.0.0.1:8080/
```

> **Important:** Use an HTTP server because the application loads JSON asynchronously. Opening `index.html` directly as a local file may result in a loading error.

---

# ⚙️ Data Build

To rebuild the dashboard dataset:

```bash
python scripts/build_dashboard_data.py
```

The default build imports the embedded `D` and `EN` data from the preserved final dashboard snapshot.

The build validates:

- Normalized order uniqueness
- MES ↔ Excel reconciliation
- Meter relationships
- Energy totals
- Order relationships
- Dashboard JSON schema

### Energy Dataset

```text
Source Rows:        1,417,704
Total Energy:       8,426.286 kWh
Allocated Orders:   80 KM1 orders
```

**Important:** This command imports the supplied dashboard calculations. It does not independently reprocess the complete 1.42M raw meter readings.

The updated workbook is retained at:

```text
source-data/21.update_energy_data.xlsx
```

Editing the workbook alone does not automatically refresh the dashboard snapshot.

### Import a New Dashboard Export

```bash
python scripts/build_dashboard_data.py --source /path/to/new-dashboard-export.html
```

The supplied export remains the authority for:

- Calculations
- Canonical meter aliases
- Timestamp allocations
- kWh confirmation

`meta.sourceSha256` identifies the exact imported HTML source.

---

# 🔗 Data Relationships

The dashboard uses normalized relationships between operational and energy datasets.

### Operations Model

Normalized order keys connect:

- **565-order MES/Excel union**
- **263 MES ↔ Excel comparisons**
- Manual loss records
- MES reason records

### Energy Model

**80 KM1 energy orders** are connected to the order union.

Their `meter_kwh` keys connect to **five canonical energy meters**.

The analytical model supports:

- Order-level analysis
- Meter-level analysis
- Daily energy consumption
- Production-energy relationships
- Disturbance analysis
- Idle-time analysis

---

# 🔎 Relationships & Filter Scope

Operations date filters select complete orders using:

```text
order_date
```

Machine, product, and shift are treated as order-level attributes.

Energy product and size filters select allocated orders.

The energy date filter selects complete orders by order date and does not clip their energy or output calculations to midnight boundaries.

Energy daily charts use:

```text
Calendar Date + Meter Selection
```

State percentages use **all five meters** for the selected calendar dates because meter-level state breakdowns are not supplied.

---

# 💰 Processing Cost Scenarios

Processing costs use manual processing minutes for selected complete orders.

Meter selection does not modify those minutes.

Users can modify scenario parameters including:

- Electricity tariff
- Line-hour cost

These are **user-entered analytical scenarios** and should not be interpreted as booked financial/accounting costs.

---

# 📈 Operational Diagnostics

The dashboard supports analytical investigation of:

- MES vs Excel data reliability
- Production performance
- Production delays
- Stoppage reasons
- Order-size effects
- Machine utilization
- Availability
- OEE proxy
- Energy consumption
- Processing costs
- Production-energy relationships

Pareto totals and cumulative shares use all selected reasons even when only the largest categories are displayed.

Missing percentages or correlations are not automatically converted into zero observations.

---

# 🧪 Legacy Analysis

The previous workbook ETL process is retained as:

```text
scripts/build_legacy_dashboard_data.py
```

It writes only:

```text
reference/legacy-dashboard.json
```

The legacy process cannot overwrite the active dashboard schema.

This allows the previous transformation logic and short energy pilot to remain available for auditing and regression testing.

---

# ✅ Validation & Testing

Run the Python tests using:

```bash
python -m unittest discover -s tests -v
```

Check JavaScript syntax using:

```bash
node --check app.js
```

Testing covers:

- Snapshot reproducibility
- Active asset references
- Order relationships
- Meter relationships
- Energy totals
- Meter-delta validation
- Allocation checks
- Dashboard tabs
- Filters
- Reset functionality
- Tariff scenarios
- Order traces
- Diagrams
- Mobile layout

---

# ▲ Vercel Deployment

<p align="center">
  <img src="public/vercel-deployment.png"
       alt="BBMED Dashboard Vercel Deployment"
       width="90%">
</p>

The dashboard can be deployed directly as a static Vercel project.

### Recommended Configuration

```text
Framework: Other
Build Command: None
Output Directory: .
Entry Point: index.html
```

`vercel.json` explicitly sets `outputDirectory` to `.` and disables framework/build auto-detection.

The deployment configuration also provides:

- Security headers
- Data revalidation
- Legacy URL redirects
- Static asset handling

`.vercelignore` excludes unnecessary development resources from production deployment, including:

- Source workbooks
- Reference snapshots
- Development scripts
- Tests

---

# 🛠️ Technology Stack

| Area | Technology |
|---|---|
| Data Sources | Excel, CSV, MES / Production Data |
| Data Cleaning | Python |
| Data Analysis | Python, SQL / Query Logic |
| Frontend | HTML5 |
| Styling | CSS3 |
| Interactivity | JavaScript |
| Data Exchange | JSON |
| Visualization | JavaScript / SVG |
| Version Control | Git & GitHub |
| Deployment | Vercel |
| Analytics | Production, Operations & Energy Analytics |

---

# 🎯 Project Objective

The objective of the **BBMED Dynamic Insight Dashboard** is to transform fragmented production and operational datasets into an integrated analytical environment.

The dashboard supports:

- 📊 Data reliability
- 🏭 Production transparency
- 🔄 MES ↔ Excel reconciliation
- 📈 Production performance monitoring
- 🔍 Root-cause analysis
- ⚡ Energy-consumption analysis
- 💰 Processing-cost scenarios
- 🎯 Operational decision support

---

# 🔄 End-to-End Analytics Pipeline

```text
Raw Operational Data
        ↓
Data Cleaning & Validation
        ↓
Structured Analytical Data
        ↓
Python / SQL Analysis
        ↓
JSON Data Model
        ↓
HTML + CSS + JavaScript Dashboard
        ↓
GitHub Version Control
        ↓
Vercel Deployment
        ↓
Interactive Web Analytics
```

---

## 📌 Summary

The **BBMED Final Dynamic Insight Dashboard** demonstrates an end-to-end data analytics and dashboard-development workflow.

It combines **data engineering, data-quality validation, production analytics, energy analytics, web development, version control, and cloud deployment** into a lightweight and auditable analytical application.

The result is an interactive environment for exploring **BBMED production performance, data reliability, operational losses, energy consumption, and processing performance**.
