# NorthStar Delivery Data Analytics

A data analytics project on the NorthStar urban delivery dataset: orders, deliveries,
drivers, hubs, customers, vehicles, complaints, incidents and app events. It covers
relational querying, statistical analysis, data cleaning and a NoSQL design in MongoDB.

## Repository structure
- `notebooks/`: one notebook per part of the project
- `data/`: the NorthStar dataset (CSV files)
- `docs/`: data dictionary and dataset notes

## Parts
1. **SQL in R** (`notebooks/1_sql_in_r.ipynb`): Cleans the customer zones and runs seven SQL queries on hubs, complaints, drivers, vehicles, app events, incidents and compensation costs.
2. **R analytics** (`notebooks/2_r_analytics.ipynb`): Loads the data in R, plots the distributions and tests correlations, such as training score against driver rating and age against loyalty score.
3. **Python data processing** (`notebooks/3_python_processing.ipynb`): Loads all nine files, checks missing values, builds seven charts, and runs a correlation matrix and a linear regression on fuel cost.
4. **MongoDB** (`notebooks/4_mongodb.ipynb`): Builds a document database, runs create, read, update and delete operations, runs aggregation pipelines, and tests indexes.

## Key findings
- **Delivery outcomes:** Across all deliveries, 13.9% failed and 21.3% were delayed. Business deliveries had the highest failure rate at 19.8%, and parcel deliveries had the lowest at 10.9%.
- **Hubs:** Hubs H08 (20.3%) and H05 (20.0%) had the highest failure rates. H03 (9.2%) and H02 (9.4%) had the lowest. Across all hubs, 64.8% of deliveries were on time.
- **Incidents:** 158 of 280 incidents (56%) were unresolved. The mean resolution time was 12.0 hours, and the median was 11.5 hours.
- **Complaints:** Complaints raised through the chatbot were resolved fastest, in an average of 7.5 days. Complaints raised through the app took longest, at 8.3 days.
- **Zones:** The central zone had the most complaints (60) and the highest compensation cost (£1,255.63). The same zone had the highest delivery failure rate, at 19%.
- **App performance:** Average API latency was between about 470 and 500 ms across event types. Payment retries and chat escalations had 19 failed events each.
- **Drivers and fuel cost:** Training score and driver rating are only weakly related (correlation -0.04 to -0.07). The regression model explained almost none of the variation in fuel cost (R² = -0.0004), so the variables tested do not predict fuel cost.

## Limitations
- The hub query in notebook 1 compared the status with the wrong case (`onTime`), which made on-time counts zero. It has been corrected to `OnTime`. Re-run that cell to refresh its output.
- The MongoDB index comparison ran on an empty result set (0 documents examined), so it shows how indexes are created, not a measured speed-up.

## Tools
R · SQL · Python (pandas, scikit-learn) · MongoDB

## How to run
1. Clone the repository.
2. Open the notebooks in order, starting with `1_sql_in_r.ipynb`.
3. Install the packages listed at the top of each notebook.
