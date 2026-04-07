# ****Log Data Processing System using PySpark and Azure Data Lake****

---

## **Project Overview**

This project implements an end-to-end data engineering pipeline to process semi-structured log data. The system ingests raw data from an API, transforms it into a structured format, and generates meaningful insights such as user activity and error rates. The final output is visualized through dashboards.

---

## **Project Objective**

To design and build a scalable data pipeline that:

- Ingests semi-structured log data  
- Processes and cleans data using PySpark  
- Converts raw data into structured format  
- Generates business-level insights  
- Enables reporting and visualization  

---

## **Problem Statement**

Modern systems generate large volumes of log data in formats such as JSON and text. These logs are not directly suitable for analysis due to their semi-structured nature.

This project solves:

- Converting raw logs into structured datasets  
- Improving query performance  
- Extracting meaningful insights from log data  

---

---

## **Architecture**
API → Azure Data Factory → Azure Data Lake (Bronze)
→ Azure Databricks (Silver, Gold)
→ Microsoft Fabric → Power BI Dashboard

---

## **Technology Stack**

- Python  
- PySpark  
- Azure Data Lake Storage (ADLS Gen2)  
- Azure Databricks  
- Azure Data Factory  
- Unity Catalog  
- Microsoft Fabric (Lakehouse)  
- SQL  
- Power BI  

---

## **Azure Resource Setup**

The following resources were created:

- Resource Group  
- Storage Account (ADLS Gen2)  
- Access Connector (Managed Identity)  
- Azure Databricks Workspace  
- Azure Data Factory  

---

## **Data Ingestion (Bronze Layer)**

- Data is fetched from a REST API using Azure Data Factory  
- API returns JSON data  
- Data is stored in the Bronze layer without transformation  

**Example Path:**
/bronze/comments/raw_data.json


This layer stores raw, unprocessed data.

---

## **Data Processing (Silver Layer)**

The Silver layer focuses on cleaning and structuring data.

### **Key Operations**

- Parsing JSON data using PySpark  
- Selecting required columns  
- Removing null values  
- Removing duplicates  
- Normalizing data (1 row = 1 record)  
- Adding derived columns:
  - log_level (ERROR / INFO)
  - timestamp  

### **Output Structure**


postId | commentId | comment | user | log_level | timestamp


---

## **Data Aggregation (Gold Layer)**

The Gold layer contains business-level aggregations used for reporting.

### **Aggregations Created**

- Comment count per post  
- Average comments  
- User activity  
- Top users  
- Engagement metrics  
- Error rate calculation  
- Data quality checks (nulls, duplicates)  

**Example Tables:**
comment_count
top_users
engagement
user_activity
error_rate


These tables are stored in Delta format in Azure Data Lake.

---

## **Microsoft Fabric Integration**

- Created a Lakehouse in Microsoft Fabric  
- Connected Azure Data Lake using shortcuts  
- Accessed Gold layer Delta tables directly  
- No data movement required  

This enables efficient querying and centralized analytics.

---

## **Power BI Dashboard**

The structured data was used to build dashboards in Power BI.

### **Visualizations Included**

- KPI Card for error rate  
- Bar chart for top users  
- Column chart for post engagement  
- User segmentation visuals  

### **Insights Generated**

- User activity trends  
- System error analysis  
- Engagement patterns  

---

## **Key Features**

- End-to-end data pipeline  
- Scalable processing using PySpark  
- Medallion architecture implementation  
- Efficient storage using Delta format  
- Integration with Microsoft Fabric  
- Interactive dashboards  

---

## **Challenges Faced**

- Handling semi-structured JSON data  
- Ensuring data quality (nulls and duplicates)  
- Managing schema consistency  
- Handling permission issues in Fabric  

---

## **Future Enhancements**

- Real-time data processing using streaming  
- Automated pipeline scheduling  
- Alerting system for error spikes  
- Advanced analytics using machine learning  

---

## **Conclusion**

This project demonstrates a complete data engineering workflow from data ingestion to visualization. By leveraging Azure services, PySpark, and Microsoft Fabric, raw log data is transformed into actionable insights. The solution is scalable, efficient, and suitable for real-world data processing scenarios.
