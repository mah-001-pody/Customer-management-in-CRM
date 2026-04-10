# 🛍️ Customer Management in CRM — Pareto-Based Segmentation

A data analysis project applying the **Pareto Principle (80/20 Rule)** to segment customers of an e-commerce platform by profitability, enabling smarter VIP gift budget allocation and data-driven marketing strategy.

---

## 📌 Problem Statement

The Customer Care and Marketing departments are preparing for a **year-end appreciation campaign** with a limited gift budget. The Marketing Director requested:

> *"Please segment our customer base into three groups — A, B, and C — based on the total profit they generate. I want to allocate 80% of the VIP gift budget to the most valuable customer group and identify who they are (their income levels, occupations, etc.)."*

---

## 🎯 Analysis Questions

1. What percentage of the total customer base does **Group A** represent? Does it follow the Pareto Principle?
2. If the company only has **500 special gift slots**, does the number of Group A customers exceed this limit?
3. Based on customers' **income and occupation** data, what marketing recommendations can attract more new "Group A" customers?

---

## 🗂️ Dataset

| File | Description |
|---|---|
| `Customer.csv` | Customer profile: ID, name, birthdate, marital status, gender, email, annual income, education, occupation, home ownership |
| `EcomSales.csv` | Transaction records: order ID, date, customer ID, segment, region, product, quantity, sales, discount, profit |
| `Product.csv` | Product catalog: code, name, category, subcategory |
| `Region.csv` | Geographic data: city, state, country, coordinates, region, market |

> Full field descriptions available in `_Customer_management_in_CRM__Data_Dictionary.xlsx`.

---

## 🔍 Methodology

### Step 1 — Data Preparation
- Check and handle missing values (dropped 1 null row in `EcomSales`; retained missing `Gender` values as non-critical)
- Verify no duplicate records across all tables
- Detect outliers in `AnnualIncome`, `Sales`, and `Profit` via box plots — retained intentionally since extreme values are key to defining customer value

### Step 2 — Customer Segmentation
- Aggregate total profit per customer from `EcomSales`
- Sort customers by total profit (descending) and compute cumulative profit percentage
- Assign groups using cumulative profit thresholds:
  - **Group A**: top customers contributing the first **80%** of total profit
  - **Group B**: next tier contributing up to **95%** of total profit
  - **Group C**: remaining customers (bottom 5%)

### Step 3 — Profiling Group A
- Analyze `AnnualIncome` distribution via box plot and descriptive statistics
- Analyze `Occupation` distribution via count plot

---

## 📊 Key Findings

### Customer Segmentation Results

| Group | Profit Contribution | % of Customers |
|---|---|---|
| **A** | 80% | ~23.15% |
| **B** | 15% | ~moderate |
| **C** | 5% | ~remainder |

### Pareto Principle Check
Group A represents approximately **23.15%** of the customer base while contributing **80%** of total profit — closely aligning with the 80/20 rule ✅

### Gift Slot Check
The number of Group A customers (**4,031**) significantly **exceeds** the 500 special gift slot limit, requiring a more refined sub-segmentation strategy within Group A.

### Group A Demographics
- **Annual Income**: Group A customers have a notably higher median income than the overall base, with many high-income outliers
- **Top Occupations**: `Professional` and `Management` dominate Group A, followed by `Clerical` and `Skilled Manual` in smaller proportions

---

## 💡 Marketing Recommendations

Based on Group A's income and occupation profile:

- **Develop premium product lines** — High-income professionals and managers are receptive to exclusive, high-quality offerings
- **Emphasize time-saving and convenience** — Busy professionals prioritize efficiency; campaigns should highlight how products simplify their lives
- **Tailor messaging** — Use language and imagery that resonate with a professional audience: quality, performance, and ROI
- **Target premium channels** — LinkedIn, business publications, and professional networks are effective reach channels for this demographic
- **Sub-segment Group A** — Since 4,031 customers exceed the 500-slot limit, consider ranking within Group A by total profit to prioritize the absolute top tier for VIP gifts

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| **Python 3** | Core language |
| **pandas** | Data loading, merging, grouping, and aggregation |
| **matplotlib** | Custom chart rendering |
| **seaborn** | Box plots, count plots, line plots |
| **Jupyter Notebook** | Interactive analysis environment |

---

## 📁 Project Structure

```
customer-management-crm/
│
├── data/
│   ├── Customer.csv
│   ├── EcomSales.csv
│   ├── Product.csv
│   ├── Region.csv
│   └── _Customer_management_in_CRM__Data_Dictionary.xlsx
│
├── Customer_management_in_CRM.ipynb   # Main analysis notebook
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

```bash
pip install pandas matplotlib seaborn jupyter
```

### Run the Notebook

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/customer-management-crm.git
   cd customer-management-crm
   ```

2. Place the CSV files inside a `data/` folder (or update file paths in the notebook).

3. Launch Jupyter:
   ```bash
   jupyter notebook Customer_management_in_CRM.ipynb
   ```

4. Run all cells from top to bottom.

---

## 📄 License

This project is for educational and portfolio purposes.
