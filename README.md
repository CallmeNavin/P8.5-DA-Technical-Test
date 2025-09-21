# P8.5-DA-Technical-Test

_This project was completed as part of a technical test. Data cannot be shared due to confidentiality, but the full process, insights, and dashboards are documented here._

![Dashboard Visualization](https://github.com/CallmeNavin/P8.5-DA-Technical-Test/blob/main/Dashboard.png)

_Explore more insights in the full Power BI dashboard_

**Part 1: Data Quality Check**

I applied six pillars of data quality to ensure raw data was transformed into trusted data, ready for reporting/dashboarding. (Mnemonic: “Check vào cửa uy(i) tín” → Completeness, Validity, Consistency & Integrity, Uniqueness, Timeliness).

**1.1 Completeness**
- Identify key variables:
  + Marketing (MKT): Revenue, Marketing Cost, Paid Revenue → basis for ROI (Return on Investment).
  + Sales: Type of Lead, Status, Call Date & Close Date (for calculating Sales Cycle Length), and Total Amount (actual realized revenue).
  + Logistics (Vận đơn): Partner Status, Shipping Fee & Payer, Merchandise Value (cross-check with Sales).
  + Among all three, Sales “Total Amount” is considered the most critical metric as it reflects real cash inflows.
- Check missing values:
  + Call Date → 97.89% missing (kept with note on limitation).
  + Other supplementary fields (e.g., Lead confirmation, Serial, Delivery Notes, Cancellation Reason, Tags, Province/City, Call-back date) → >40% missing → excluded.
  + Action: drop columns with >40% missing or entirely NA.

**1.2 Validity**
- Phone number stored as float64, not needed for dashboard.
- Product dimensions stored as object, not required for analysis.

**1.3 Consistency & Integrity**
- Sales revenue > Logistics revenue → explained by discounts, cancellations, or free shipping.
- Comparison between Sales & MKT → used to calculate Marketing contribution ratio.

**1.4 Uniqueness**
- Logistics file rows (7,944) > order IDs (5,817) → multiple rows per order due to multiple products.
- Action: Group by Order ID, aggregate merchandise value.

**1.5 Timeliness**
- Dataset spans Jan–Dec 2020. Some inconsistent date formats were standardized.

**Part 2: Report Construction**

**2.1 Key Metrics**
- Sales: Total revenue, Sales Cycle Length, Loyalty rate.
- Marketing: ROI (Paid Revenue / Marketing Cost), ROI by channel.
- Logistics: Shipping cost ratio, Delivery success/failure status.

**2.2 Power BI Processing**
- Fill down missing values in Logistics (multi-line orders).
- Standardize column formats.
- Define “Partner Fee” as shipping cost.
- Add calculated columns: Sales Cycle Length, Status Group, Channel Group.
- Calculate Loyalty Rate using distinct phone numbers → ~0%.
- Create Marketing ROI measure.
- Build Membership What-if model: parameters %Convert, Months, Price/Month → calculate Membership Revenue and Delta vs Baseline.

**2.3: Insights & Recommendations for Q4/2020**

**_Valuable Insights_**
- Marketing as backbone: 95.82% of revenue attributed to Marketing, ROI = 1.77 (slightly above EdTech benchmark 1.71). Positive but fragile → if ads stop, revenue collapses. (Long-term goal).
- Heavy reliance on physical product: 81.06% revenue from book sales. Stable cash flow but low margin and limited scalability. (Short-term goal).
- Clear seasonality: Revenue peaked in July (159M, summer holidays), stayed high in September (153M, back-to-school), but dropped in November (93M). → Need seasonal marketing optimization and stable recurring revenue streams.
- Logistics cost: Company absorbs ~7% of merchandise value as shipping cost → reduces net profit.
- Loyalty ≈ 0%: Customers purchase once, no repeat → business forced to acquire new customers continuously.
- Channel imbalance: >99% customers from Social Media, while Saleshunt & Upsell ≈ 0.
- Marketing spend imbalance: >90% budget goes to Facebook, ROI FB (36.32%) ≈ Google (34.79%) & TikTok (29%) → high dependency on one channel with no superior ROI.
- ROI volatility: ROI fluctuated 2.15 → 1.29 → 2.02 across Q3, mirrored by revenue swings. Business is overly exposed to ROI shifts.

**_Actionable Plans_**

- Short-term Goals
  + Shift from one-time sales to Half Digital Membership Model (hybrid of product + digital subscription). → More stable revenue, higher CLV, higher gross margin, lower logistics costs, improved referral & loyalty. Parents are more likely to commit to recurring payments (“continuous journey with the child”) than one-time purchases.
  + Seasonal optimization (Back-to-school & Summer packages): capture peak demand, maintain revenue in low months → combined with membership to smooth seasonality.
- Long-term Goals
  + Maintain ROI in range 1.77–2.0 while reducing dependency on Facebook.
  + Negotiate lower costs with Facebook.
  + Reallocate part of budget to Google & TikTok, which offer similar ROI at lower spend.
  + Expand non-Marketing revenue streams: launch Half Digital Membership, implement referral programs, retention/upsell for existing students, cross-sell additional products, invest in content-driven growth (TikTok/YouTube).
- Data Quality Improvements (for Q4 onward)
  + Enforce mandatory entry for Call Date when Sales first contact customers.
  + Recheck overlap between “Shipping Fee” and “Partner Fee” → merge into a single column to avoid confusion.

**2.4 Appendix – Half Digital Membership Model**
- What-if dashboard simulates scenarios when a portion of current customers convert to membership.
  + Adjustable parameters: % conversion, monthly fee, subscription length.
  + Only ~45% conversion into 12-month membership at 300k VND/month would surpass baseline revenue from 100% one-time sales.

**Part 3: About Me**

Hi, I'm Navin (Bao Vy) – an aspiring Data Analyst passionate about turning raw data into actionable business insights. I’m eager to contribute to data-driven decision making and help organizations translate analytics into business impact. For more details, please reach out at:

🌐 LinkedIn: https://www.linkedin.com/in/navin826/

📂 Portfolio: https://github.com/CallmeNavin/
