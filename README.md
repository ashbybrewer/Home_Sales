# Home Sales Analytics — Fast Price Intelligence at Scale (SparkSQL)

**The problem.** Real-estate and lending teams sit on millions of transaction records, but the moment an analyst asks "what did 4-bedroom homes sell for, by year?" against raw data, the query crawls — and every slow query is wasted compute and a stakeholder waiting. At scale, *how* the data is stored and cached decides whether a pricing dashboard refreshes in seconds or minutes.

**The architecture.** PySpark / SparkSQL on a home-sales dataset. Data is loaded into a temporary view, then progressively optimized through Spark's caching layer (spark.catalog.cacheTable) and re-written as **Parquet partitioned by build year** — the same pipeline shape used in production lakehouse setups.

**How it works.** Core pricing questions are answered in SparkSQL: average price of 4-bed homes by sale year, price by build year for 3-bed/3-bath homes, and price by view rating for homes at or above $350k. The key query is then **benchmarked three ways** — raw temp view vs. cached table vs. partitioned Parquet — with the cache lifecycle verified (isCached, uncache, re-check) to show exactly when each optimization earns its keep.

**Why it matters (ROI).** This is the difference between an analytics layer that costs money and makes people wait and one that is tuned. The project demonstrates the practical judgment a BI role needs: not just writing the query, but knowing the caching and partitioning moves that cut query time and compute spend on large datasets — the skills that keep a reporting layer fast and cheap.

---
*Built during the University of Texas Data Analysis Boot Camp (2023-24) with help from classmates, tutors, and AI tools — disclosed then, kept honest now. Notebook: Home_Sales_colab.ipynb.*
