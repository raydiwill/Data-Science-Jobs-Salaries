data_cleaned_2021 Changelog
=====

## Info 

 * Scraped data scientist jobs' details datasets from  [www.kaggle.com](www.kaggle.com). 
 * The dataset originally contains **742** rows and **42** columns.

## Changes

#### Remove unnecessary columns

Columns *Job Description, Headquarters, Founded, Revenue, Competition, Hourly, Employer provided, company_txt, Job Location, Age, google_an, seniority_by_title, Degree* were removed for further analysis as I considered them as unnecessary.

#### Correct typos

Capitalize letters in *job_title_sim* column:
 * data scientist &rarr; Data Scientist.
 * data engineer &rarr; Data Engineer.
 * data modeler &rarr; Data Modeler.
 * analyst, data analitics &rarr; Data Analyst.
 * other scientist &rarr; Other Scientist.
 * data scientist project manager &rarr; Data Scientist Project Manager.
 * machine learning engineer &rarr; Machine Learning Engineer.
 * director &rarr; Director.

#### Trim white space

In column *Company Name*, the string has an unnecessary line break, fixed by trim the line break and create a new column with the same name to contain the newly fixed string. Then break the string into smaller substring using **SPLIT** excel function as they wrongly has values of *rating* column in it. 

#### Change index numbers

The dataset contains 742 rows but the last index of the *index* column diplayed more than 900, after deleting missing value rows I fixed the indexes. 

#### Split column into columns

Column *Location* contains both cities and states of the US, for further analysis in city and state individually, I split the column into 2 named *Location City* and *Location State* in case of any possible analysis in the future.

#### Deal with missing values

The dataset author denoted **"-1"** as either missing or incompleted value. The only possible solution at the time of writing is to remove the records as I could not reach out to the author, thus reducing the total number of rows.

In *job_title_sim* column, the author also denoted na as missing since we cannot categorize the title from *Job Title* column. The best treatment is to remove the records, hence 10 records were removed.

In *Size* column, there are 2 rows with missing values denoted as *"unknown"*. One possible solution is to search for the size of the company on Google, however this would be noted as **miscellaneous** information for further analysis in the future.

## Result

The final result after the cleaning process if a dataset with **721** rows and **31** columns.