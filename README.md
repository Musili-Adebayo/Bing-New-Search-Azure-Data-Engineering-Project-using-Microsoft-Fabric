# Bing-New-Search_An_Azure-Data-Engineering-Project-using-Microsoft-Fabric (Sentiment Analysis).

![Architecture](https://github.com/Musili-Adebayo/Bing-New-Search---End-to-End-Azure-Data-Engineering-Project-using-Microsoft-Fabric./blob/main/Olympic%20Games%20Paris%202024%20News.png)

##  Project Summary
For this project, I analyzed the sentiment analysis from the recently concluded Olympic Games Paris 2024. I used the Bing Search v7 engine to get all the news from Microsoft Bing Search Engine to determine the sentiments from each piece of news. I picked the Bing API because working with APIs will always be part of any data engineering process at one point in your career. For this project, I carried out the following:

1. Create a Bing Search Resource in Azure.
2. Data Ingestion. 
3. Data Transformation with Incremental Loading.
4. Sentiment Analysis with Incremental Loading.
5. Data Visualization and Reporting in Power BI.
6. Set up Alerts with Data Activator with notifications on Teams.

## Data Source: 
Datasource: Olympic news data were loaded from Bing Search Resource News Search APIs v7 (https://api.bing.microsoft.com/v7.0/news/search) available in Azure.

## Data Engineering Technical Skills:
+ Data Ingestion
+ Data Pipeline: Data factory, incremental load, schedule refresh
+ Fabric Data Storage: JSON, Lake House
+ Data Science: Sentiment Analysis, Synase ML Model 
+ Data Warehousing: Analytics Reporting
+ Extract, Transform and Load (ETL) process
+ Power BI Data Visualization technical skills (Documentation, Data Gathering, Power Query, Data Modelling, Report Design, Data Analysis Expression (DAX), Business and Analytics Reporting, Performance Optimization, Deployment and Power BI Service, Scalability)
+ Continuous Improvement
  
## Data Engineering Process
#### 1. Create a Bing Search Resource in Azure:
I created a resource group called AzureXfabric_rg and used the marketplace to search for the Bing Search v7 API to create a Bing Search resource.  I picked the F1 (3 calls per second and 1k Calls per month) pricing tier because it is free.
#### 2. Data Ingestion:
As our data lake, I created a Microsoft Fabric Lakehouse called the bing_olympic_news_db which I connected the Bing Search resource API and also configured the Source and Destination.
- Configuring the Data Source 
To connect to the source data, I use the RestAPI connection available in Fabric to connect to the Bing Search resource API in Azure. 
- Setting the Data Destination.
For the Destination, I set the destination to the bing_olympic_news_db Lakehouse I had created earlier. I also created a file path called olympic-news.json and set the file format to JSON.
#### 3. Data Transformation with Incremental Loading:
I use the spark job within Microsoft Fabric for this and I also implement a Type 1 SCD to load our data into the Lakehouse incrementally.
- ###### Implementing the Type 1 Slowing Changing Dimension (SCD) to avoid loading duplicate data during incremental loading. I opted for type 1 because I am not interested in keeping a history of our existing data.
-  [View ETL codes here](https://github.com/Musili-Adebayo/Bing-New-Search---End-to-End-Azure-Data-Engineering-Project-using-Microsoft-Fabric./blob/main/ETL_process_olympic_news.ipynb)

#### 4. Sentiment Analysis with Incremental Loading:
For the Sentiment Analysis, I use SynapseML formerly (MMLSpark) which is an open-source library that is available within Microsoft Fabric. It is a pre-built intelligent model for our machine learning task and predicts the Olympic news sentiments based on the news description column which has a detailed description of the news article as seen above.
[View Sentiment Analysis codes here](https://github.com/Musili-Adebayo/Bing-New-Search---End-to-End-Azure-Data-Engineering-Project-using-Microsoft-Fabric./blob/main/olympic_news_sentiment_analysis.ipynb)

#### 5. Schedule Refresh:
Since the news data is live, there is a need to schedule its refresh every morning at 7 am in Data Factory. This refresh covers the data Ingestion (pipeline), ETL_process_olympic_news (notebook), and olympic_news_sentiment_analysis.ipynb (notebook)
The refresh schedule is shown here 👇
![Schedule Refresh](https://github.com/Musili-Adebayo/Bing-New-Search-Azure-Data-Engineering-Project-using-Microsoft-Fabric./blob/main/Schedule%20Refresh%20-%20News_Ingestion%20Pipeline.png)

#### 6. Data Visualization in Power BI:
Below is the Data Visualization and report of the Olympic news for the past 7 days as at when I performed this analysis. Over 100 news was published and only 17% of it has positive sentiments.
[Download the Sentiment Analysis Dashboard in PDF here](https://github.com/Musili-Adebayo/Bing-New-Search-Azure-Data-Engineering-Project-using-Microsoft-Fabric./blob/main/Sentiment%20Analysis%20Dashboard.pdf)

![Sentiment Analysis Dashboard](https://github.com/Musili-Adebayo/Bing-New-Search-Azure-Data-Engineering-Project-using-Microsoft-Fabric./blob/main/Sentiment%20Analysis%20Dashboard.png)

#### 7. Set up Alerts with Data Activator with notifications on Microsoft Teams:
I created an alert called Positive Alert Item and I would like to receive a Teams message alert when the Positive Sentiment is greater than 17%.

## KPI Metrics 
For the Visualization, I measure the following KPIs.
1. Total published News (positive, negative, neutral, and mixed
2. Percentage of each sentiment (positive, negative, neutral, and mixed)


## In Summary 
1. This was an exciting opportunity  to demonstrate how Azure Data Services (known as items in Fabric) can be replicated in Microsoft Fabric(an all-in-one analytics solution). These items include DataFactory, Lakehouse, Pipeline, Power BI, Intelligence and  Machine Learning many more. 

#### If you prefer reading, you can read extensively about this project on Medium and Linkedin below
-  [Read on Medium here](https://medium.com/art-of-data-engineering/bing-new-search-end-to-end-azure-data-engineering-project-using-microsoft-fabric-995dc7dd3d37)
-  [Read on LinkedIn here](https://www.linkedin.com/pulse/bing-new-search-end-to-end-azure-data-engineering-project-adebayo-1dorf/)
