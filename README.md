# 🍕 Pizza Sales Analysis — SQL Project

A SQL-based data analysis project exploring pizza sales data. The project involves building a relational database from CSV datasets and answering business questions using SQL queries across two difficulty levels.

---

## 📁 Project Structure

```
├── pizza_analysis.sql    # All SQL queries (schema + analysis)
├── pizza_types.csv       # Pizza type definitions and ingredients
├── pizzas.csv            # Pizza variants with sizes and prices
├── orders.csv            # Order dates and times
└── order_details.csv     # Line-item order details with quantities
```

---

## 🗄️ Database Schema

The project uses four relational tables:

| Table | Rows | Description |
|---|---|---|
| `pizza_types` | 32 | Pizza names, categories, and ingredients |
| `pizzas` | 96 | Pizza variants (size + price per type) |
| `orders` | 21,350 | Order timestamps |
| `order_details` | 48,620 | Per-order pizza quantities |

**Entity Relationships:**
- `order_details.order_id` → `orders.order_id`
- `order_details.pizza_id` → `pizzas.pizza_id`
- `pizzas.pizza_type_id` → `pizza_types.pizza_type_id`

---

## 🔍 Analysis Questions

### Basic
- Total number of orders placed
- Total revenue generated from pizza sales
- Highest-priced pizza
- Most common pizza size ordered
- Top 5 most ordered pizza types by quantity

### Intermediate
- Total quantity ordered per pizza category
- Order distribution by hour of the day
- Category-wise count of pizza types available
- Average number of pizzas ordered per day
- Top 3 pizza types by revenue

---

## 🚀 Getting Started

### Prerequisites
- PostgreSQL (or any SQL-compatible database)

### Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/pizza-sales-analysis.git
   cd pizza-sales-analysis
   ```

2. Import the CSV files into your database (using `COPY`, pgAdmin, or a similar tool).

3. Run the SQL file:
   ```bash
   psql -U your_user -d your_database -f pizza_analysis.sql
   ```

---

## 🛠️ Tools Used

- **PostgreSQL** — database and query execution
- **CSV datasets** — raw sales data source

---

## 📊 Sample Insights

- Revenue is calculated by joining `order_details` with `pizzas` on `pizza_id` and summing `price × quantity`.
- Hourly order distribution uses `DATE_PART('hour', time_col::time)` to identify peak ordering times.
- Daily average pizza volume is derived using a subquery that aggregates quantities per date.
