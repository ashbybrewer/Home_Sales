# Home Sales — SparkSQL at Scale

Home-sale records analyzed entirely in **PySpark/SparkSQL** (`Home_Sales_colab.ipynb`), focused on the performance toolbox rather than just the queries.

## Queries
Average price of four-bedroom houses per sale year; average price by build year for 3-bed/3-bath homes (and the 2-floor ≥2,000 sqft variant); average price per `view` rating for homes ≥ $350k.

## The performance story
The same `view`-rating query is timed three ways:
1. Against the raw temp view
2. Against the **cached** table (`spark.catalog.cacheTable`) — faster
3. Against data re-written as **parquet partitioned by `date_built`** — compared again

Caching and partition strategy are verified (`isCached`, uncache, re-check) — the notebook demonstrates *when* each optimization pays.

**Skills:** SparkSQL, temp views, caching lifecycle, parquet partitioning, query benchmarking.

---
*Built during the University of Texas Data Analysis Boot Camp (2023–24), with help from classmates, tutors, and AI tools — disclosed then, kept honest now.*
