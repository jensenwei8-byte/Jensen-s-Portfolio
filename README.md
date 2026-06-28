# Bayland Health Creator Investment Analysis

## Submission Overview

This submission answers the question: **Which TikTok Shop affiliate creators should Bayland Health invest more in next quarter, and why?**

The analysis evaluates creators using both sales scale and efficiency. Instead of ranking creators by GMV alone, I created an **Investment Priority Score** that combines Sales Impact, Efficiency, Order Quality, Cost Efficiency, and Reliability.

## Files Included

| File                                  | Purpose                                                                                                                   |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `Bayland_Creator_Analysis.pbix`       | Interactive Power BI dashboard for creator performance, ranking, investment decisions, and creator drill-through analysis |
| `Bayland_Creator_Recommendation.doc`  | Stakeholder presentation covering data exploration, metric definition, and headline recommendations                       |
| `Bayland_Creator_Recommendation.doc`  | Data cleaning, exploration, joins, validation checks, and supporting analysis                                             |
| `wide_creator_analysis.csv`           | Final analysis table used for modeling and dashboarding                                                                   |
| `cleaning_log.md`                     | Summary of data quality issues, cleaning decisions, and assumptions                                                       |
| `README.md`                           | Instructions for reviewing the submission                                                                                 |

## How to Review the Submission

### Part 1 — Data Cleaning and Preparation

See:

* `Bayland_Creator_Recommendation.doc`
* `cleaning_log.md`
* `wide_creator_analysis.csv`

These files document how the raw creators, videos, orders, and products tables were cleaned and joined. The final output is a creator-level / order-level analysis table used for the dashboard.

### Part 2 — Dashboard

See:

* `Bayland_Creator_Analysis.pbix`

Open the `.pbix` file in Power BI Desktop. The main dashboard includes:

* Creator Investment Map
* Creator leaderboard
* Investment Priority Score
* Investment Decision
* Drill-through creator profile page
* Creator Selling Power Profile / radar view
* Radar chart tooltip

### Part 3 — Data Exploration

See:

* `Bayland_Creator_Recommendation.doc`

The data exploration section reviews creator performance distribution, order status patterns, content performance, and key drivers of sales. The main findings are: 
* creator performance is uneven, so Bayland should not rely on raw GMV alone when deciding where to invest
* not every orders can be traced back to creator
* Video content is 91% of all the content type, it is the major GMV generator.

### Part 4 — Metric Definition and Justification

See:

* `Bayland_Creator_Recommendation.doc`
* `Bayland_Creator_Analysis.pbix`

I define an **Investment Priority Score** using five normalized 0–100 percentile-based scores:

1. **Sales Impact Score** — based on Net GMV from completed orders
2. **Efficiency Score** — based on Net GMV per Video
3. **Reliability Score** — based on Completed Orders
4. **Order Quality Score** — based on Refund/Cancel Rate, using reverse percentile logic
5. **Cost Efficiency Score** — based on Revenue per Commission Dollar

The final score is calculated as:

**Investment Priority Score = 35% Sales Impact Score + 30% Efficiency Score + 15% Order Quality Score + 10% Cost Efficiency Score + 10% Reliability Score**

Creators are then ranked by Investment Priority Score, and their Investment Decision is assigned using score bands.

### Part 5 — Interactive Review / Drill-Through

See:

* `Bayland_Creator_Analysis.pbix`

The Power BI dashboard allows the reviewer to select or drill through to a specific creator and review their raw KPIs, score breakdown, order quality, content efficiency, and final recommendation.
### Category Filter

![Category Filter](Dashboard%20Screenshot/Category%20filter)

### Drill-through Function

![Drill-through Function](Dashboard%20Screenshot/Drill%20through%20Function.png)

### Hovering on Creator Profile

![Hovering on Creator Profile](Dashboard%20Screenshot/Hovering%20on%20Creator%20Profile.png)

### Part 6 — Headline Recommendation

See:

* Slide 1 of `Bayland_Creator_Recommendation.pptx`
* Creator leaderboard in `Bayland_Creator_Analysis.pbix`

The presentation leads with the recommendation for the Partnerships lead. It names the specific creators I would invest more in, test and grow, maintain, or step back from based on their Investment Priority Score and supporting KPIs.

## Key Assumptions

* Only **completed orders** are counted toward Net GMV because they represent realized sales.
* Cancelled and refunded orders are included in the Refund/Cancel Rate to evaluate order quality risk.
* Creator performance is evaluated at the creator level using the cleaned creator identifier.
* Where an order was missing `creator_id` but had a valid `video_id`, the creator was backfilled using the videos table.
* Orders are treated as the primary transaction-level fact table.
* Products are joined using `sku_id`, since product IDs may not be unique across SKUs.
* Net GMV per Video is used as the main efficiency metric because it measures how much completed-order revenue a creator generates per piece of content.
* The Investment Priority Score uses percentile normalization so metrics with different units can be compared on the same 0–100 scale.
* The score is designed for next-quarter investment prioritization, not as a complete measure of long-term brand value.

## What I Would Do Next With More Time

With more time, I would improve the analysis by adding:

* Product margin data to measure profit, not only GMV
* Repeat purchase or customer retention data to estimate long-term creator value
* Customer acquisition cost and free product seeding cost
* More detailed attribution logic for orders influenced by multiple creators or channels
* Time-window analysis to separate recent momentum from historical performance
* Statistical confidence intervals to reduce small-sample bias
* Creator audience demographics and content category fit
* A/B testing design for creators classified as “Test and Grow”

## AI Disclosure

I used AI assistance to help structure the analysis, refine metric definitions, and improve the wording of the stakeholder presentation and README. Final metric choices, assumptions, dashboard design, and recommendations were reviewed and adjusted by me based on the provided dataset and business objective.
