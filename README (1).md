# Simple Expense Tracker (Excel)

**Task 34 · Data Analytics Track · Veda Technology Internship**

A monthly personal/business expense tracker built in Excel. It categorizes every expense, tags it as fixed or variable, summarizes spending by month, and validates its own totals.

## Objective

Practice categorization and totals: turn a raw list of transactions into a clear monthly summary, and prove the numbers add up.

## What's Inside

| File | Purpose |
|------|---------|
| `Simple_Expense_Tracker.xlsx` | The tracker (4 sheets, see below) |
| `data/synthetic_expenses.csv` | The raw synthetic dataset (72 transactions, Aug–Oct 2026) |
| `docs/DEPLOYMENT_AND_ROLLBACK.md` | Deployment configuration and rollback evidence |

### Workbook sheets

1. **Expenses**: one row per transaction (Date, Description, Category, Expense Type, Amount, Month). Category is a dropdown. Expense Type and Month are formulas (`VLOOKUP`, `TEXT`).
2. **Monthly Summary**: `SUMIFS` matrix of category × month, grand totals, % of total, a Fixed vs Variable breakdown, and a stacked bar chart.
3. **Categories**: lookup table mapping each category to Fixed or Variable.
4. **Validation**: four automated PASS/FAIL checks (see below).

## Approach

1. Generated **synthetic expense data** (no real personal data) with a fixed random seed for reproducibility: 4 fixed categories (rent, utilities, internet & phone, insurance) and 7 variable ones.
2. Built a `Categories` lookup so each expense is classified as **Fixed** or **Variable** automatically.
3. Used `SUMIFS` to build the monthly summary so it updates when rows are added or edited.
4. Added a **Validation** sheet to validate totals:
   - Expenses total = Summary grand total
   - Category total = Fixed + Variable total
   - Row count matches
   - No uncategorised rows

## Outcome

- Total spend over 3 months: **₹95,857** (Aug ₹32,389 · Sep ₹34,849 · Oct ₹28,619)
- Fixed expenses: **51.2%**, Variable: **48.8%**
- Largest category: **Rent (37.6%)**; largest variable category: **Shopping (14.5%)**
- All validation checks: **PASS**

## How to Use

1. Open `Simple_Expense_Tracker.xlsx`.
2. Add new rows at the bottom of the **Expenses** sheet (pick a Category from the dropdown; Type and Month fill in automatically).
3. For a new month, add its `yyyy-mm` label as a column header on **Monthly Summary**.
4. Check the **Validation** sheet shows all PASS.

## Interview Questions

**Fixed vs variable expense?**
Fixed expenses stay roughly the same every month (rent, insurance, subscriptions). Variable expenses change with behaviour or usage (groceries, shopping, dining out). Fixed costs are your baseline commitment; variable costs are where you can adjust.

**Why categorize expenses?**
Categories turn a long list of transactions into patterns: where money goes, which areas are growing, and where to cut or budget. Without categories you only have a total, with them you have insight.

## Tools

Microsoft Excel (formulas: `SUMIFS`, `VLOOKUP`, `TEXT`, `IFERROR`; data validation; charts).

## Author

Rathod Harshvardhansinh J · Data Analytics Intern, Veda Technology
