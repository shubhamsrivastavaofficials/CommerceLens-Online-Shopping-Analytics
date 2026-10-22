# CommerceLens: Online Shopping Intelligence Dashboard

## Project synopsis

### Abstract

CommerceLens is a web-based business intelligence prototype for analysing online shopping transactions. It transforms item-level order records into an interactive view of sales performance, product demand, customer behaviour, and cross-category purchasing patterns. The system combines descriptive sales analysis, Recency–Frequency–Monetary (RFM) customer grouping, and order-level category co-occurrence. It also produces concise observations that help a user investigate possible merchandising and retention opportunities. The application accepts CSV data and computes its analysis locally in the browser.

### Problem statement

Online retailers collect transaction data across products, customers, regions, and sales channels. When these records are viewed only as raw rows, it can be difficult to identify which categories contribute most to revenue, whether customers are returning, and which products are commonly purchased together. A compact analytical interface can make these patterns easier to inspect and discuss.

### Aim

To design and implement an accessible, interactive dashboard that converts online shopping transaction data into clear descriptive analytics for academic demonstration and exploratory decision support.

### Objectives

1. Summarise net revenue, order volume, customer reach, and average order value for a selected date range.
2. Compare category, product, and sales-channel performance.
3. Group customers using transparent RFM rules.
4. Identify category pairs that occur together in the same order.
5. Generate understandable, data-derived observations for further business investigation.
6. Support CSV upload and export so the prototype can be explored with a compatible dataset.

## Modules

### 1. Shopping overview

The overview presents headline measures, a revenue trend, revenue by category, channel contribution, and a summary of customer groups. Date-range and category controls update the analysis.

### 2. Product intelligence

Products are ranked by net revenue, units sold, or number of orders. The table shows product category, quantity, distinct order count, net revenue, and average listed price.

### 3. Customer segments

The prototype calculates three simple measures per customer: recency (days since their latest recorded purchase), frequency (distinct orders), and monetary value (net revenue). It then assigns each customer to one descriptive group:

| Group | Prototype rule |
|---|---|
| Champions | At least 4 orders and a purchase within the last 60 days |
| Loyal | At least 3 orders and does not meet the Champions rule |
| At risk | At least 2 orders and no purchase in the last 120 days |
| New & occasional | All other customers in the selected records |

These fixed rules are intentionally easy to explain. They are not a trained prediction model and may need adjustment for a real retailer's purchase cycle.

### 4. Basket analysis

For each order, the system identifies the distinct product categories present and counts category pairs that appear together. It reports the number and share of selected orders containing each pair. Co-occurrence can suggest a cross-sell experiment, but it does not establish causation.

### 5. Business insights

The insight view describes leading category revenue, leading channel revenue, customer group counts, multi-category purchasing, and average order value. Each observation includes context for how it might be investigated. The prototype does not claim to forecast sales or determine the cause of a pattern.

### 6. Data import and export

The CSV importer checks for required fields and loads valid item rows into the browser. Export downloads the currently filtered item rows. The dataset is not sent to a server by this prototype.

## Methodology

1. **Input:** Read one CSV row per product line in an order.
2. **Preparation:** Parse dates and numeric fields; discard incomplete or invalid item rows.
3. **Filtering:** Select a rolling time range and optional product category.
4. **Aggregation:** Calculate line revenue as `quantity × unit_price × (1 − discount_pct / 100)`, then aggregate by order, customer, product, category, channel, or order pair as required.
5. **Interpretation:** Render the aggregates and apply the transparent RFM and category-pair rules described above.

## Data dictionary

| Field | Required | Description |
|---|---:|---|
| `date` | Yes | Order-line date, readable by the browser |
| `order_id` | Yes | Identifier shared by all lines in one order |
| `customer_id` | Yes | Stable, pseudonymous customer identifier |
| `region` | Yes | Customer or delivery region label |
| `channel` | Yes | Sales channel label, such as Website or Mobile app |
| `category` | Yes | Product category |
| `product` | Yes | Product name or identifier |
| `quantity` | Yes | Units purchased on the line |
| `unit_price` | Yes | Price per unit, in a consistent currency |
| `discount_pct` | No | Percentage discount for the line; defaults to zero |
| `payment_method` | No | Payment method label |

## Technology and architecture

- **Presentation:** HTML5 and responsive CSS.
- **Application logic:** Vanilla JavaScript in the browser.
- **Charts:** Canvas rendering with no charting library.
- **Data storage:** In-memory browser state for the current session; imported records are not persisted.
- **Deployment model:** Static site; the `index.html` file can be hosted by any static web host.

## Scope and limitations

- The bundled dataset is generated for demonstration and must not be presented as observed customer behaviour.
- Monetary display uses USD formatting. Input records should use one consistent currency.
- Revenue is calculated from quantity, listed unit price, and the optional discount percentage; taxes, shipping, refunds, and cost of goods are not represented.
- RFM thresholds are fixed and descriptive.
- Basket analysis counts category co-occurrence only; it does not calculate formal association-rule metrics such as support, confidence, or lift.
- The prototype has no login, server-side storage, role permissions, or multi-user collaboration.
- The dashboard is an exploratory academic prototype and is not a substitute for finance, inventory, or customer-data governance systems.

## Future enhancements

- Add a backend API and database for larger datasets and saved analyses.
- Add data validation reports, configurable date parsing, and currency selection.
- Calculate formal association-rule metrics and product-level bundles.
- Add cohort retention, repeat-purchase intervals, and customer lifetime value estimates.
- Add forecasting with backtesting and clearly reported uncertainty.
- Add accessibility review, automated unit tests, and role-based access controls before production use.

## Suggested evaluation criteria

- Accuracy of calculated totals against a manually verified sample.
- Correctness of distinct order and customer counts.
- Correct assignment of customers to documented RFM rules.
- Correct identification of category pairs within each order.
- Usability of filters, import feedback, and responsive layouts.
- Clarity of the difference between descriptive observations and causal claims.
