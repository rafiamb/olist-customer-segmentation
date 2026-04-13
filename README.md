# Customer Segmentation Analysis

## Project Background
Olist is a Brazilian e-commerce platform, founded in 2015, that connects small and medium-sized merchants to customers across Brazil through a centralized online marketplace.

Olist has accumulated significant transaction data across thousands of sellers and customers that has been underutilized for customer retention strategy. This project analyzes customer purchasing behavior to segment Olist's customer base and uncover retention opportunities that can improve customer lifetime value and reduce churn.

Insights and recommendations are provided on the following key areas:
* **Customer Segmentation:** Classification of 93,357 customers into distinct behavioral segments using Recency-Monetary (RM) analysis to identify Champions, Loyal Customers, Needs Attention, At Risk, and Lost customers.
* **Retention Analysis:** Evaluation of customer purchasing patterns revealing that 97% of customers place only one order, highlighting a critical retention gap across the business.
* **Segment Value Analysis:** Assessment of median spend and recency across segments to prioritize marketing investment and identify highest-value customer groups.
* **Marketing Recommendations:** Targeted retention strategies for each customer segment designed to maximize revenue impact while minimizing unnecessary marketing spend.

An interactive Tableau dashboard can be viewed [here](https://public.tableau.com/views/CustomerSegmentation-Olist/Dashboard?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link).

The Python notebook used for data cleaning, EDA, SQL queries, and RM scoring can be found [here](rfm_analysis.ipynb).

---

## Data Structure and Initial Checks
Olist's database contains 9 tables covering the full e-commerce operation. This analysis focuses on 4 tables directly relevant to customer purchasing behavior: `orders`, `order_items`, `customers`, and `payments` across 96,477 transactions from 93,357 unique customers.

![ERD Diagram](olist_erd.jpg)

Prior to beginning the analysis, a variety of checks were conducted for quality control and familiarization with the datasets. The SQL queries used to inspect and clean the data can be found in the notebook linked above.

---

## Executive Summary

### The Core Problem
Olist has a retention problem. Analysis of 93,357 customers across 96,477 transactions reveals that 97% of customers place only one order and never return. This means the business is heavily dependent on continuously acquiring new customers to sustain revenue, rather than building value from its existing base. Improving retention, even marginally, would generate significantly more revenue at a fraction of the cost of new customer acquisition.

### Methodology
RFM is a customer segmentation technique that scores customers based on three behavioral dimensions: Recency (how recently they purchased), Frequency (how often they purchase), and Monetary (how much they spend). In this analysis, Frequency was excluded because 97% of customers placed only one order, making it a poor differentiator across segments. Each customer was scored on a 1-10 decile scale across Recency and Monetary and assigned to one of five segments based on their combined score. Median spend was used instead of average to account for high-value outliers in the dataset.

Below is the overview page from the Tableau dashboard. The entire interactive dashboard can be viewed [here](https://public.tableau.com/views/CustomerSegmentation-Olist/Dashboard?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link).

![Dashboard](Dashboard.png)

---

## Key Findings

| Segment | Customers | % of Base | Median Spend |
|---|---|---|---|
| Champions | 9,631 | 10% | $265 |
| Loyal Customers | 24,580 | 26% | $155 |
| Needs Attention | 32,571 | 35% | $103 |
| At Risk | 20,972 | 22% | $67 |
| Lost | 5,603 | 6% | $40 |

- Champions spend **6.6x more** than Lost customers on median
- The **Needs Attention** segment is the largest at 35% of the customer base with high potential if re-engaged
- **At Risk and Lost** customers combined represent 28% of the base but generate the least revenue
- The data reveals a clear drop-off in both recency and spend as customers move from Champions to Lost

---

## Recommendations

Each segment requires a distinct strategy to maximize retention ROI.

#### Champions — Protect & Reward
- Launch a VIP early access or loyalty program to reward and retain them
- Leverage this group for product feedback and reviews as they are most likely to respond
- **Do not discount** as they buy at full price and discounting erodes margin unnecessarily

#### Loyal Customers — Nurture & Upsell
- Target with personalized recommendations based on past purchase categories
- Offer a small incentive such as free shipping or a small discount to drive a repeat purchase
- Priority segment for upsell campaigns

#### Needs Attention — Re-Engage Now
- Launch a time-limited re-engagement email campaign
- Sub-segment by recency and prioritize customers who purchased within the last 6 months
- A/B test messaging to identify what drives conversion

#### At Risk — Win Back Before It's Too Late
- Deploy a win-back campaign with a meaningful discount of 15-20%
- Highlight new products or categories they have not yet tried
- Set a marketing spend cap for customers with low monetary scores

#### Lost — Minimize Spend
- Send one final win-back email, then suppress from future campaigns
- Redirect saved budget toward Champions and Loyal Customers

---

### Bottom Line
Improving retention by even 5% across the Needs Attention segment would generate significant incremental revenue without additional acquisition cost, representing the highest ROI opportunity available to the marketing team.
