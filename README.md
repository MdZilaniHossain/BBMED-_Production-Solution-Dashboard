
# 📊 BBMED Final Dynamic Insight Dashboard

An interactive, web-based analytics dashboard for **BBMED packaging and production operations**.

The project combines production, MES, Excel, energy, stoppage, staffing, and processing-cost information into a single dynamic dashboard for operational analysis and decision support.

The dashboard is built as a lightweight static web application using **HTML, CSS, JavaScript, JSON, and Python-based data preparation**, and can be deployed directly through **Vercel**.

---

## 🌐 Live Dashboard

The application is deployed as a static web dashboard through Vercel.

> The dashboard provides interactive filtering, operational KPIs, MES ↔ Excel comparison, production analysis, energy analysis, processing-cost scenarios, and calculation/model validation.

### Deployment Preview

![BBMED Dashboard Vercel Deployment](docs/images/vercel-deployment.jpeg)

---

## 📊 Dashboard Preview

The main dashboard provides interactive filters for:

- Machine
- Product
- Order size
- MES ↔ Excel status
- Shift
- Production orders

Key operational indicators include:

- **430 Orders**
- **11,632,839 Produced Units**
- **16,280.2 h Usage Time**
- **5,921.3 h Production Time**
- **14.19 u/min Median Production Rate**
- **42.4% Median Availability**
- **38.6% Median OEE Proxy**
- **263 MES ↔ Excel Matched Orders**

![BBMED Operations Dashboard](docs/images/dashboard-preview.jpeg)

---

## 🏗️ Project Architecture

The complete workflow follows a structured analytics pipeline:

**Raw Data → Data Cleaning → Cloud Storage → Dashboard Development → GitHub → Vercel → Live Dashboard**

Additional analysis can be performed using **Python, SQL/Data Query tools, and AI/ML techniques**.

![BBMED Project Architecture](docs/images/project-architecture.jpeg)

### Workflow

1. **Data Sources**
   - Excel files
   - Google Sheets
   - MES / production databases
   - CSV files
   - Manual reports and other sources

2. **Data Cleaning & Preparation**
   - Remove duplicates
   - Handle missing values
   - Standardize formats
   - Combine tables
   - Create relationships
   - Validate data quality
   - Prepare analysis-ready datasets

3. **Cloud Storage**
   - Cleaned datasets can be centrally organized
   - Production
   - Energy
   - Stoppages
   - Staff
   - Products

4. **Dashboard Development**
   - HTML
   - JavaScript
   - CSS
   - JSON
   - Interactive filters
   - Dynamic visualizations
   - Responsive design

5. **Version Control**
   - GitHub repository
   - Version history
   - Source-code management
   - Branch management

6. **Deployment**
   - Vercel static deployment
   - Automatic deployment from GitHub
   - HTTPS
   - Production hosting

7. **Live Analytics**
   - Interactive dashboard
   - Dynamic filtering
   - KPI monitoring
   - Operational analysis
   - Desktop and mobile accessibility

8. **Advanced Data Analysis**
   - Python data processing
   - SQL / query analysis
   - Data-quality validation
   - Pattern identification
   - Anomaly detection
   - AI-assisted insights

---

## 🚀 Active Application

The main page at `/` contains the **BBMED Final Dynamic Insight Dashboard**.

The application contains three major analytical areas:

### 1. Operations & Data Reliability

Production and operational performance analysis including:

- Order-level production
- MES ↔ Excel reconciliation
- Production rate
- Availability
- OEE proxy
- Stoppage analysis
- Order-size effects
- Shift and machine analysis

### 2. Energy & Processing Cost

Energy and processing analysis including:

- Meter consumption
- Energy allocation
- Daily energy trends
- Production-energy relationships
- Disturbance and idle percentages
- Electricity tariff scenarios
- Processing-cost scenarios

### 3. Calculation / Validation / Model

Provides transparency into:

- Calculation logic
- Data relationships
- Model validation
- Order traces
- Meter relationships
- Data provenance

---

## 📁 Project Structure

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
│   ├── semantic-model.png
│   └── data-workflow.png
│
├── docs/
│   └── images/
│       ├── vercel-deployment.jpeg
│       ├── dashboard-preview.jpeg
│       └── project-architecture.jpeg
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

## 🧩 Main Application Files

| File | Purpose |
|---|---|
| `index.html` | Main three-page interactive dashboard |
| `app.js` | Filters, SVG charts, scenarios, order traces and asynchronous data loading |
| `styles.css` | Dashboard styling, accessibility and responsive/mobile layout |
| `data/dashboard.json` | Main dashboard dataset |
| `public/semantic-model.png` | Semantic/data relationship model |
| `public/data-workflow.png` | Data workflow diagram |
| `scripts/build_dashboard_data.py` | Python data-build and validation process |
| `vercel.json` | Vercel deployment configuration |

The application has **no npm dependencies, external chart services, or runtime database connections**.

The browser loads the required JSON dataset and image assets locally.

---

## 💻 Run the Dashboard Locally

Clone or download the repository and open a terminal inside the project folder.

Run:

```bash
python -m http.server 8080 --bind 127.0.0.1
```

Then open:

```text
http://127.0.0.1:8080/
```

> **Important:** Use an HTTP server instead of opening `index.html` directly because the application loads JSON asynchronously. Opening the HTML file directly may result in a loading error.

---

## ⚙️ Data Build

To rebuild the dashboard dataset:

```bash
python scripts/build_dashboard_data.py
```

The default build imports the embedded `D` and `EN` data from the preserved final dashboard snapshot.

The build process validates:

- Normalized order uniqueness
- MES / Excel reconciliation
- Meter relationships
- Energy totals
- Order relationships
- Dashboard JSON schema

The supplied expanded energy dataset contains:

```text
Source rows:       1,417,704
Total energy:      8,426.286 kWh
Allocated orders:  80 KM1 orders
```

### Importing a New Dashboard Export

```bash
python scripts/build_dashboard_data.py --source /path/to/new-dashboard-export.html
```

The supplied dashboard export remains the authority for:

- Calculations
- Canonical meter aliases
- Timestamp allocations
- kWh confirmation

`meta.sourceSha256` identifies the exact imported HTML source.

---

## 🔗 Data Relationships

The dashboard uses normalized relationships between operational and energy datasets.

### Operations

Normalized order keys connect:

- **565-order MES/Excel union**
- **263 MES ↔ Excel comparisons**
- Manual loss records
- MES reason records

### Energy

**80 KM1 energy orders** are linked to the order union.

Their `meter_kwh` keys connect to **five canonical energy meters**.

The model supports:

- Order-level analysis
- Meter-level analysis
- Daily consumption
- Production-energy relationships
- Disturbance analysis
- Idle-time analysis

---

## 🔎 Filter Logic

### Operations Filters

Operations date filters select complete orders using:

```text
order_date
```

Machine, product and shift are treated as order-level attributes.

### Energy Filters

Energy product and size filters select allocated orders.

The energy date filter selects complete orders by order date rather than clipping energy/output calculations at midnight boundaries.

Daily energy charts use:

```text
Calendar Date + Meter Selection
```

State percentages use all five meters for the selected calendar period when meter-level state breakdowns are unavailable.

---

## 💰 Processing Cost Scenarios

Processing-cost calculations use manual processing minutes for selected whole orders.

Users can modify scenario parameters such as:

- Electricity tariff
- Line-hour cost

These values are **scenario inputs** and should not be interpreted as booked financial/accounting costs.

---

## 📈 Analysis Logic

The dashboard supports operational diagnostic analysis including:

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

Pareto totals and cumulative shares are calculated using all selected reasons even when only the largest categories are visualized.

Missing percentages or correlations are not automatically converted into zero observations.

---

## 🧪 Legacy Analysis

The previous workbook ETL process is retained as:

```text
scripts/build_legacy_dashboard_data.py
```

It writes only:

```text
reference/legacy-dashboard.json
```

The legacy process cannot overwrite the active dashboard dataset.

This allows the previous energy pilot and transformation logic to remain available for auditing and regression testing.

---

## ✅ Validation & Testing

Run the Python tests with:

```bash
python -m unittest discover -s tests -v
```

Check the JavaScript syntax with:

```bash
node --check app.js
```

Testing covers:

- Snapshot reproducibility
- Asset references
- Order relationships
- Meter relationships
- Energy totals
- Meter-delta validation
- Allocation checks
- Dashboard filters
- Reset functionality
- Tariff scenarios
- Order traces
- Mobile layout

---

## ▲ Vercel Deployment

The dashboard can be deployed directly as a static Vercel project.

Recommended configuration:

```text
Framework: Other
Build Command: None
Output Directory: .
Entry Point: index.html
```

`vercel.json` explicitly sets the output directory to the project root and disables unnecessary framework/build auto-detection.

The deployment configuration also provides:

- Security headers
- Data revalidation
- Legacy URL redirects
- Static asset handling

`.vercelignore` prevents unnecessary development resources from being included in production deployments, including:

- Source workbooks
- Reference snapshots
- Development scripts
- Tests

---

## 🛠️ Technology Stack

| Area | Technology |
|---|---|
| Data Sources | Excel, CSV, MES / Production Data |
| Data Preparation | Python |
| Data Analysis | Python, SQL / Query Logic |
| Frontend | HTML5 |
| Styling | CSS3 |
| Interactivity | JavaScript |
| Data Exchange | JSON |
| Visualization | JavaScript / SVG |
| Version Control | Git & GitHub |
| Deployment | Vercel |
| Analytics | Operational, Production & Energy Analytics |

---

## 🎯 Project Objective

The objective of the BBMED project is to transform fragmented production and operational datasets into an integrated analytical environment.

The dashboard is designed to support:

- **Data reliability**
- **Production transparency**
- **MES ↔ Excel reconciliation**
- **Production performance monitoring**
- **Root-cause analysis**
- **Energy-consumption analysis**
- **Processing-cost scenarios**
- **Operational decision support**

---

## 📌 Summary

The **BBMED Final Dynamic Insight Dashboard** demonstrates an end-to-end analytics workflow:

```text
Raw Operational Data
        ↓
Data Cleaning & Validation
        ↓
Structured Analytical Data
        ↓
Python / Query Analysis
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

The result is a lightweight, auditable and interactive dashboard for exploring BBMED production, data reliability, energy and processing performance.
```

### Important: name your 3 images like this

Put the three screenshots you uploaded into:

```text
docs/
└── images/
    ├── vercel-deployment.jpeg
    ├── dashboard-preview.jpeg
    └── project-architecture.jpeg
```

Then these README lines will automatically display them on GitHub:

```markdown
![BBMED Dashboard Vercel Deployment](docs/images/vercel-deployment.jpeg)

![BBMED Operations Dashboard](docs/images/dashboard-preview.jpeg)

![BBMED Project Architecture](docs/images/project-architecture.jpeg)
```

