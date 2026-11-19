# Retail Orders Dataset — Inspection Report

**Inspection date:** 18 November 2026  
**Dataset:** Retail orders (Nepal; NPR)  
**Status:** Inspection only (no values have been changed)

## 1. Source, real or synthetic, and grain

- **Source supplied:** A CSV dataset
- **Real or synthetic:** Synthetic (Constructed for practice purpose)
- **Apparent grain:** One row appears to represent one order containing one product alongside price, discount, payment means and order status.
- **Important key assumption:** `order_id` appears intended to identify an order, but the supplied data contains repeated identifiers. 

## 2. Rows and columns

- **Data rows supplied:** 244 (excluding the header).
- **Columns:** 12.
- **Column names:** `order_id`, `order_date`, `customer_id`, `customer_name`, `city`, `category`, `product`, `quantity`, `unit_price_npr`, `discount_pct`, `payment_method`, `order_status`.

The apparent sequence covers order IDs around `ORD1001`–`ORD1240`, but the sequence itself is not complete or unique in the supplied records.

## 3. Column table: name, type you believe it is, type Excel assigned, note

| Column | Expected analytical type | Excel assigned | Inspection note |
|---|---|---|---|
| `order_id` | Text / identifier | General | Identifier; leading letters matter. Check uniqueness. |
| `order_date` | Date | Date | Mixed formats and invalid-looking calendar dates are present. |
| `customer_id` | Text / identifier | General | Some values are blank. Do not treat as a quantity. |
| `customer_name` | Text | General | Names include inconsistent capitalization. |
| `city` | Categorical text | General | Blanks, spelling variants, abbreviations, and capitalization differences. |
| `category` | Categorical text | General | Inconsistent spelling/capitalization and possible product-category mismatches. |
| `product` | Categorical text | General | Product labels; inspect whether they agree with category. |
| `quantity` | Whole number | General | Blanks, a negative value, a text value, and an extreme quantity. |
| `unit_price_npr` | Numeric currency (NPR) | General | Text-formatted prices, zero, and an extreme value. |
| `discount_pct` | Numeric percentage | General | Values outside the usual 0–100% range. |
| `payment_method` | Categorical text | General | Some values are blank. |
| `order_status` | Categorical text | General | Capitalization, whitespace, and spelling variants. |

## 4. Missing values (per column, counts)

| Column | Blank values |
|---|---:|
| `order_id` | 0 |
| `order_date` | 0 |
| `customer_id` | 3 |
| `customer_name` | 0 |
| `city` | 9 |
| `category` | 0 |
| `product` | 0 |
| `quantity` | 4 |
| `unit_price_npr` | 0 |
| `discount_pct` | 0 |
| `payment_method` | 5 |
| `order_status` | 0 |
| **Total blank cells** | **21** |

## 5. Duplicates (what kind, how many, how you found them)

Two different duplicate checks are necessary:

1. **Exact repeated records:** Four records at the end of the supplied data repeat earlier records exactly:
   - `ORD1008`
   - `ORD1065`
   - `ORD1116`
   - `ORD1181`

   These are four additional repeated rows. An exact-row duplicate check across all 12 columns should identify them.

2. **Repeated `order_id` with different record contents:** `ORD1101` occurs twice, but the two records have different dates, customers, cities, products, and other values. This is not an exact-row duplicate. It is a key/identifier conflict that needs source-owner investigation.

**Finding:** The supplied data has four exact repeated rows and one additional repeated order identifier with different contents. There are five duplicate-ID occurrences beyond the first occurrence when considering the repeated IDs described above.

**How to document your Excel check:** Record whether Remove Duplicates was run on all 12 columns or only on `order_id`. Those operations answer different questions. Run it only on a copy, and do not delete anything from the original dataset during this inspection.

## 6. Outliers and impossible values (list rows and why)

The following are records to investigate, not automatic instructions to delete. “Unusual” does not always mean “wrong.”

| Order ID | Column | Observed value | Why it needs investigation |
|---|---|---:|---|
| `ORD1013` | `quantity` | -2 | Negative quantity is unusual for a normal sales-order record; could represent a return/adjustment, but the row status is Delivered. |
| `ORD1019` | `unit_price_npr` | `Rs. 1,250` | Added Rs at front gives consistency error. |
| `ORD1034` | `unit_price_npr` | 9,999,999 | Extreme compared with the other listed prices. |
| `ORD1045` | `unit_price_npr` | `1,800` | Comma-formatted value stored as text in the CSV. |
| `ORD1056` | `order_date` | `2026-02-30` | 30 February is not a valid calendar date. |
| `ORD1078` | `unit_price_npr` | 0 | A zero price may be a free item, promotion, or an error; business context is required. |
| `ORD1089` | `quantity` | `two` | Text in a numeric quantity field. |
| `ORD1100` | `order_date` | `31/13/2026` | Invalid date: month 13 does not exist. |
| `ORD1142` | `discount_pct` | 150 | Discount exceeds 100%; likely invalid unless the field has a nonstandard meaning. |
| `ORD1151` | `order_date` | `2027-03-14` | Future-dated relative to the inspection date; confirm whether this is a planned/future order or an error. |
| `ORD1190` | `quantity` | 500 | Extreme quantity relative to the other records; could be a bulk order, but should be verified. |
| `ORD1201` | `discount_pct` | -10 | Negative discount is unusual. |

Other values may be unusual for the business even if they are technically valid. The owner should define plausible product-price and order-quantity ranges.

## 7. Inconsistent categories (list the variants)

### City

- `Kathmandu`, `kathmandu`, `KTM`
- `Pokhara`, `pokhara`
- `Lalitpur`, `Lalitur`

The first two groups contain capitalization/abbreviation variants. `Lalitur` appears to be a spelling error for `Lalitpur`.

### Category

- `Groceries`, `groceries`, `GROCERY`, `Grocery`
- `Electronics`, `ELECTRONICS`, `electronics`
- `Stationery`, `Stationary`
- `Home & Kitchen`, `Home and Kitchen`

There are also category/product combinations that appear inconsistent and should be checked against the product catalogue:

- `ORD1041`: Electronics / Notebook Pack
- `ORD1084`: Grocery / Phone Charger
- `ORD1125`: ELECTRONICS / Steel Plates Set
- `ORD1156`: electronics / Lentils 2kg
- `ORD1162`: Home and Kitchen / Geometry Box
- `ORD1173`: Grocery / Earbuds
- `ORD1175`: Stationary / Water Bottle
- `ORD1223`: electronics / Lentils 2kg
- `ORD1234`: ELECTRONICS / Geometry Box

These may be category-entry errors, but a product catalogue or owner confirmation is needed.

### Order status

- `Delivered`, `delivered`, `DELIVERED ` (trailing space)
- `Cancelled`, `Canceled`

### Customer name

- `sita sharma` appears with different capitalization from `Sita Sharma`.

## 8. Date problems

| Order ID | Supplied date | Issue |
|---|---|---|
| `ORD1056` | `2026-02-30` | Invalid calendar date. |
| `ORD1100` | `31/13/2026` | Invalid month; cannot be interpreted as a valid date. |
| `ORD1121` | `15-03-2026` | Different date format from the dominant `YYYY-MM-DD` format. |
| `ORD1151` | `2027-03-14` | Future date relative to 18 November 2026. |
| `ORD1171` | `2026-1-5` | Inconsistent zero-padding; may still be interpretable as 5 January 2026. |

The dataset mixes date representations. Excel may parse some differently depending on regional settings. Confirm the intended date convention with the owner before converting anything.

## 9. Five questions this data can answer

1. How many orders were recorded by month? (`order_date`, `order_id`)
2. Which products and categories appear most frequently in orders? (`product`, `category`, `quantity`)
3. Which cities have the highest recorded order counts? (`city`, `order_id`)
4. Which payment methods are used most often? (`payment_method`, `order_id`)
5. What is the distribution of order statuses (Delivered, Pending, Returned, Cancelled)? (`order_status`, `order_id`)

These are descriptive questions. They do not automatically establish sales revenue, profit, or customer satisfaction.

## 10. Three questions it cannot

1. **What is the shop's profit or profit margin?** The dataset has no product cost, operating expenses, tax, shipping cost, or reliable net-sales definition.
2. **Why do customers return or cancel orders, and are they satisfied?** There are no return/cancellation reasons, feedback, complaint, or satisfaction fields.
3. **What is the shop's inventory position or which products need replenishment?** There are no stock-on-hand, supplier, purchase, reorder-level, or inventory movement fields.

Other questions may also require additional data. For example, customer lifetime value requires a reliable customer key and a sufficiently complete transaction history.

## 11. What I would ask the shop owner

1. What exactly does one row represent: an order, an order line, or a product within an order?
2. Should `order_id` be unique? Why does `ORD1101` appear with two different sets of order details?
3. Are the four exact repeated records accidental exports, or do they represent legitimate repeated events?
4. What date format and timezone should be used? Are future-dated orders allowed?
5. What do blank customer IDs, cities, quantities, and payment methods mean? Are they unknown, not applicable, or missing during entry?
6. Can quantity be negative? If so, how are returns, refunds, and adjustments represented?
7. Can a product have a zero price? What are valid price and quantity ranges?
8. Is `discount_pct` always a percentage from 0 to 100? Can negative values represent surcharges?
9. Is there an authoritative product-to-category mapping? Which category labels are valid?
10. What are the approved city names and payment-method labels?
11. Are `Canceled` and `Cancelled` the same status? Are there other allowed statuses?
12. Does `unit_price_npr` mean list price, selling price before discount, or actual price paid?
13. How should revenue be calculated for Delivered, Returned, Pending, and Cancelled orders? Are refunds recorded elsewhere?
14. Are taxes, shipping fees, and other charges included in the listed price?

## Inspection conclusion

The supplied dataset contains 244 data rows and 12 columns. It has blank fields, four exact repeated records, a repeated order identifier with conflicting record details, inconsistent category/location/status labels, invalid or inconsistent dates, text values in numeric fields, and values that need business validation.