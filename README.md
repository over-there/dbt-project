# Marketing common data modelling challenge
	

### Task: to rebuilt a model used at Improvado. Imagine that MCDM-model behind dashboard, is lost somehow.
Given:
 
	- raw data from the ad systems (seeds folder): 
 
    		* src_ads_bing_all_data
    		* src_ads_creative_facebook_all_data
    		* src_ads_tiktok_ads_all_data
    		* src_promoted_tweets_twitter_all_data,
      
	- the MCDM table structure for this report (seeds folder): mcdm_paid_ads_basic_performance_structure. 
 
 And there is a [dashboard](https://lookerstudio.google.com/reporting/fa668749-b82f-41a8-a12e-f7d9c0733b57/page/tEnnC)

### Important: Due to difficulties with the suggested tools, I used GitHub, Python, and Tableau.

## The general approach

To build the required model, I merged the data from four files into the final MCDM. Some files had missing data or renamed fields.

    1. Load the files in Jupyter Notebook.
    
    2. Check the data quality: missing values, errors.
    
    3. Compare the column names in the final model with the available data and complete the datasets. At this stage, it became evident that a significant number of columns needed to be added and renamed.
    For example, for Tiktok, we replaced the adgroup_id column with adset_id, and rt_installs with installs. For Bing, we renamed the conv column to total_conversions.
    For Facebook, we additionally calculated *engagements = likes + shares + comments + views + clicks*, and set total_conversions equal to the purchase column as the target conversion.
    
    4. We also added missing columns to each dataset for each channel: if the data type is INT, we used 0, and if it's STRING, we used "unknown".
    
    5. After unifying all four datasets following the format of the final model, we combined the data into the resulting table. This table can be found in the mcdm_model folder **mcdm_final** file.
    
    6. Create a dashboard using the final model.

## Submission
-   A link to the recreated [dashboard](https://public.tableau.com/app/profile/marina1319/viz/Adsperformance/adsperformance?publish=yes) in Tableau Public.
-   A new mcdm_model folder with the MCDM in the repo.

## Metrics:
	- *Cost per engage* is just a spended sum divided by sum of engagements
	- *Conversion cost* is calculated by dividing sum of spended by total conversions count
	- *Impressions by channel* is a sum of impressions for each channel
	- *CPC* gets like sum of spended divided by clicks count

### Tools
-   Jupyter Notebook (Python)
-   Tableau


### How to Use the Repository
Clone this repository to continue your dbt Cloud or other tool.

The repository includes raw data from various ad platforms, as well as the MCDM structure for the ads_basic_performance report and the final report in the mcdm_model folder.

