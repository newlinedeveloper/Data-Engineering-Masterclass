# Data-Engineering-Masterclass
Data Engineering Masterclass 

- Dimonsional Data modeling
- Fact Data modeling
- Appling Analytical patterns
- KPIs and Experimentation
- Data Visualization and Impact
- Unit Testing Pyspark pipelines
- Data pipeline Maintenance
- Apache Spark Fundamentals
- Data Quality patterns
- Real-time pipelines with Flink and Kafka

### Data Modeling - Complex Data types and accumulation

- what is dimension? - Dimensions are attributes of entity
-   slow changing
-   Fixed

- Knowing your data consumer
- OLTP vs OLAP data modeling
- Cumulative table design
- The compactness vs usability tradeoff
- Temporal cardinality explosion
- Run-length encoding compression gotchas


#### Knowing your consumer
- Data analysts / Data scientists
  - Should be very easy to query. Not many complex data types
- Other data engineers
  - should be compact and probably harder to query. Nested types are okay
- ML Models
     - Depends on the model and how its trained
- Customers
   - Should be very easy to interpret the chart


#### OLTP vs Master data vs OLAP
- OLTP - Online transaction processing
    - Optimizes for low-latency, low-volume queries
- OLAP - Online analytical processing
-   - Optimizes for large volume, Group by queries, Minimizes joins
- Master Data
-   -  Optimizes for completeness of entity definitions, deduped
 
#### Mismatching needs = less business value
- Some of the biggest problems in data engineering occur when data is modeled for the wrong consumer

#### OLTP and OLAP is Continuum
Production database ----> Master Data ----> OLAP Cubes ----> Metrics


(Transational data)----> (Combined & flattened data)-------> (To perform analytics query Dice and slice of the data)


#### Cumulative Table design
- Core components
-   - 2 dataframes (yesterday and today)
    - FULL OUTER JOIN the two data frames together
    - COLAESCE values to keep everything around
    - Hang onto all the history
 
- Usages
  - Growth analytics at facebook (dim_all_users)
  - State transition tracking (We will cover this more in analytics track, applying analytical patterns later)


 

