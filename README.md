# Bing-New-Search_End-to-End-Azure-Data-Engineering-Project-using-Microsoft-Fabric (Sentiment Analysis).

# of Fabric DE Project of NewsData

![Slide1](https://github.com/Musili-Adebayo/Bing-New-Search---End-to-End-Azure-Data-Engineering-Project-using-Microsoft-Fabric./blob/main/Olympic%20Games%20Paris%202024%20News.png)

##  Project Summary
For this project, we will be analyzing the sentiment analysis from the recently concluded Olympic Games Paris 2024. I will be using the Bing Search v7 engine to get all the news from Microsoft Bing Search Engine to determine the sentiments from each news. 
actually picked the Bing API because working with APIs will always be part of any data engineering process at one point in your career. Fo this project, we do the following:
1. Create a Bing Search Resource in Azure.
2. Data Ingestion. 
3. Data Transformation with Incremental Loading..
4. Sentiment Analysis with Incremental Loading.
5. Data Visualization and Reporting in Power BI.
6. Set up Alerts with Data Activator with notification on Teams.

## Data Source: 
Datasource: News data were loaded from Bing Search Resource News Search APIs v7 (https://api.bing.microsoft.com/v7.0/news/search) available in Azure.

## DE Technical Skills:
+ Data Ingestion
+ Data Pipeline: Datafactory, increamental load, schedule refresh
+ Fabric Data Storage: json, Lake House
+ Data Science: Sentiment Analysis, Synase ML Model 
+ Data Warehousing: Analytics Reporting
+ Extract, Transform and Load (ETL) process
+ Power BI Data Visualization technical skills (Documentation, Data Gathering, Power Query, Data Modelling, Report Design, Data Analysis Expression (DAX), Business and Analytics Reporting, Performance Optimization, Deployment and Power BI Service, Scalability)
+ Continuous Improvement
  
## Data Engineering Process
1. I created a resource group called AzureXfabric_rg and used the marketplace to search for the Bing Search v7 API to create a Bing Search resource. I picked the F1 (3 calls per seconds and 1k Calls per month) pricing tier because it is free.
2. Data Ingestion: As our data lake, I created a Microsoft Fabric Lakehouse called the bing_olympic_news_db. I will be connecting to the Bing Search resource API we created earlier in Azure through a Data Pipeline (olympic-news-ingestion-pipeline). We will also configure our Source and Destination.
3. Configuring the Data Source 
To connect to the source data we will be using the Rest connection that is available in Fabric to connect to the Bing Search resource API in Azure. Click on Source > Create new connection > Rest API and set up the connection as seen below.
4. Setting the Data Destination.
For the Destination, we are going to set our destination to the bing_olympic_news_db Lakehouse we created earlier. I also created a file path called olympic-news.json and set the file format to JSON.
3. Data Transformation with Incremental Loading.
It's time to clean the olympi-news.json  file in our lakehouse using a spark job within Microsoft Fabric. We will also implement a Type 1 SCD to load our data into the Lakehouse incrementally.
-  [View ETL codes here](https://github.com/Musili-Adebayo/Bing-New-Search---End-to-End-Azure-Data-Engineering-Project-using-Microsoft-Fabric./blob/main/ETL_process_olympic_news.ipynb)

4. Sentiment Analysis with Incremental Loading.
For the Sentiment Analysis, I will be using SynapseML formerly (MMLSpark) which is an open-source library that is available within Microsoft Fabric. We will use one of the pre-built intelligent models for our machine learning task and predict the Olympic news sentiments based on the news description column which has a detailed description of the news article as seen above.
[View Sentiment Analysis codes here](https://github.com/Musili-Adebayo/Bing-New-Search---End-to-End-Azure-Data-Engineering-Project-using-Microsoft-Fabric./blob/main/olympic_news_sentiment_analysis.ipynb)

Implementing the Type 1 Slowing Changing Dimension (SCD) to avoid loading duplicate data during incremental loading. I opted for type 1 because I am not interested in keeping a history of our existing data.

5. Data Visualization in Power BI.
Below is the Data Visualization and report of the Olympic news for the past 7 days as when I performed this analysis. Over 100 news was published and only 17% of it has positive sentiments.
[View Sentiment Analysis Dashboard here](https://github.com/Musili-Adebayo/Bing-New-Search---End-to-End-Azure-Data-Engineering-Project-using-Microsoft-Fabric./blob/main/olympic_news_sentiment_analysis.ipynb)



6. Set up Alerts with Data Activator with notifications on Microsoft Teams.
In the visual above, click on the card visual and select Set Alerts. The set alert pane will pop up as seen below. I created an alert called Positive Alert Item and I would like to receive a Teams message alert when the Positive Sentiment is greater than 17%.

6. Schedule Refresh: Since the news data is live, there is need to schedule it's refresh every morning at 9am in Data Factory. This refresh covers the data Ingestion (pipeline), ETL process (notebook) and Sentiment Analysis (notebook)
The refresh schedule is shown here 👇

## KPI Building 
While building the visualization, the following KPIs were considered;
1. Count of each review (positive, negative, neutral and mixed
2. Percentage of each review type
3. Total Review
4. Review by Country
5. Review by category...

## Report Design and Visualization
+ The Report Canvas was designed in Canva .
+ A sample of the Home page in here 👇 below.
<img src="https://github.com/Abdur-RasheedAde/Sentiment-Analysis-of-Fabric-Data-Engineering-Project-of-NewsData/blob/main/HomePage.png" width=75% height=75%> 
Link to download PowrBI PDF Report is here 👉 [DownloadPDF](https://github.com/Abdur-RasheedAde/Sentiment-Analysis-of-Fabric-Data-Engineering-Project-of-NewsData/blob/main/News_Report.pdf)


## Conclusions 
1. Microsoft Fabric is a one-stop shop that replicate all Azure Data Services (known as items in Fabric) in one space. These items include DataFactory, Power BI, LakeHouse, Notebooks, Pipeline and so on. 
2. It can iterract with all internal and external data sources like Azure, AWS, GCP, Dataverse and coud services like Databricks, Snowflake and others.
3. It extensively supports SQL, Python, Scala and java Programming Languages
4. It is awesome for Data warehousing and ETL process and visualization.
