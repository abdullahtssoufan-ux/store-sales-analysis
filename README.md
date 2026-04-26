# 🛒 Store Sales Analysis — Python & Power BI

An end-to-end data analysis project that explores store sales performance across regions, customer segments, product categories, and sales channels. The project covers the full pipeline: raw data ingestion → cleaning → feature engineering → exploratory analysis → Power BI dashboard.

---

## 📁 Project Structure

```
store-sales-analysis/
│
├── day4_capstone.csv                  # Raw dataset (input)
├── Capstone_05042026.ipynb            # Python notebook: cleaning, EDA & visuals
├── Python_Project_storesales_.csv     # Cleaned & enriched dataset (output)
├── Sales_Dashboard.pbix               # Interactive Power BI dashboard
└── README.md
```

---

## 🔄 Project Pipeline

```
Raw CSV  →  Python (Cleaning + EDA)  →  Cleaned CSV  →  Power BI Dashboard
```

---

## 📊 Dataset Overview

The raw dataset (`day4_capstone.csv`) contains store sales orders with the following fields:

| Column | Description |
|---|---|
| `OrderID` | Unique order identifier |
| `OrderDate` | Date the order was placed |
| `CustomerID` | Unique customer identifier |
| `Segment` | Customer segment (Consumer, Corporate, Home Office) |
| `Region` | Sales region (North, South, East, West) |
| `Channel` | Sales channel (Store, Online, Partner) |
| `Category` | Product category (Electronics, Furniture, Office Supplies) |
| `Product` | Product name |
| `Quantity` | Units ordered |
| `UnitPrice` | Price per unit |
| `Discount` | Discount applied |
| `ShippingCost` | Shipping cost for the order |
| `Returned` | Whether the order was returned |
| `PaymentMethod` | Payment method (Cash, Card, Wallet, Transfer) |
| `NetSales` | Net sales revenue |
| `Profit` | Profit earned |

---

## 🐍 Python Notebook — `Capstone_05042026.ipynb`

### 1. Data Cleaning

- **Text columns** — stripped whitespace, standardized casing, replaced empty strings with `NaN` for: `Segment`, `Category`, `Region`, `Channel`, `Product`, `Returned`, `PaymentMethod`
- **Numeric columns:**
  - `Quantity` — coerced to numeric
  - `UnitPrice` — removed `$` signs, coerced to numeric
  - `Discount` — removed `%` signs, normalized values >1 to decimal (e.g. 20 → 0.20)
- **Missing values:**
  - `Discount` → filled with `0`
  - `ShippingCost` → filled with column mean
  - Rows missing `Region`, `Product`, `Quantity`, or `UnitPrice` → dropped
- **Dates** — parsed `OrderDate` to datetime, extracted `Month` and `Year` columns

### 2. Feature Engineering

```python
df_clean["Grosssale"]            = Quantity × UnitPrice
df_clean["Netsalerecalcualtion"] = Grosssale × (1 − Discount)
df_clean["profit_margin"]        = Profit / Netsalerecalcualtion
```

### 3. Summary Analysis

| Question | Approach |
|---|---|
| Which category has highest net sales? | `groupby("Category")` → sum of net sales |
| Which region is strongest? | `groupby("Region")` → total sales + avg discount |
| Which segment has the highest profit margin? | `groupby("Segment")` → avg profit margin |
| What is the monthly trend? | `groupby("Month")` → avg net sales over time |

### 4. Visualizations

- Bar chart — Net Sales by Category
- Line chart — Monthly sales trend
- Line chart — Yearly sales trend
- Bar chart — Profit Margin by Customer Segment

### Libraries Used

```python
pandas
numpy
matplotlib
seaborn
```

### How to Run

```bash
# Clone the repository
git clone https://github.com/your-username/store-sales-analysis.git
cd store-sales-analysis

# Install dependencies
pip install pandas numpy matplotlib seaborn

# Launch the notebook
jupyter notebook Capstone_05042026.ipynb
```

---

## 📈 Power BI Dashboard — `Sales_Dashboard.pbix`

<img width="1117" height="629" alt="dashboard" src="https://github.com/user-attachments/assets/db9b42b5-8c75-4fe9-ab57-f770c8099289" />


Built on top of the cleaned dataset, the dashboard provides interactive views of:

- **Sales Overview** — Total revenue, profit, and order volume KPIs
- **Regional Performance** — Sales and profit by region
- **Customer Segments** — Consumer vs. Corporate vs. Home Office comparison
- **Category Analysis** — Revenue by Electronics, Furniture, Office Supplies
- **Channel Breakdown** — Store vs. Online vs. Partner performance
- **Payment Methods** — Transaction distribution by payment type
- **Time Trends** — Monthly and yearly sales trends

### How to Open

1. Download [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free)
2. Open `Sales_Dashboard.pbix`
3. Interact with the filters and visuals

---

## 🛠 Tools & Technologies

| Tool | Purpose |
|---|---|
| Python (pandas, numpy) | Data cleaning & feature engineering |
| Python (matplotlib, seaborn) | Exploratory visualizations |
| Jupyter Notebook | Analysis environment |
| Power BI Desktop | Interactive dashboard |
| CSV | Data storage format |
| GitHub | Version control & project sharing |

---

## 📬 Contact
Abdullah Soufan
abdullah.t.s.soufan@gmail.com
Feel free to open an issue or reach out with any questions or suggestions!
