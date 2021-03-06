Data Scientist Salaries in the USA
=====

This is a personal portfolio project Exploratory Data Analysis (EDA) repository on salary of jobs in Data Science field in the USA.

## Data Collection

The dataset is taken from kaggle website.

## EDA

### Data understanding

First step is to read the csv file stored locally with pandas read_csv command.

```python
data_org = pd.read_csv('..\Data-Science-Jobs-Salaries\datasets\data_original.csv')

```

Then, previewing the first 5 rows to be familiar with the data using head command

```python
data_org.head()
```

![image](https://user-images.githubusercontent.com/97393390/177134063-beb71366-33f5-40e5-940f-64ade1c6c06d.png)


The dataset originally contains 742 rows and 42 columns.

```python
data_org.shape
(742, 42)
```

We can gather more information on the dataset by the following command

```python
data_org.info()

<class 'pandas.core.frame.DataFrame'>
RangeIndex: 742 entries, 0 to 741
Data columns (total 42 columns):
 #   Column              Non-Null Count  Dtype  
---  ------              --------------  -----  
 0   index               742 non-null    int64  
 1   Job Title           742 non-null    object 
 2   Salary Estimate     742 non-null    object 
 3   Job Description     742 non-null    object 
 4   Rating              742 non-null    float64
 5   Company Name        742 non-null    object 
 6   Location            742 non-null    object 
 7   Headquarters        742 non-null    object 
 8   Size                742 non-null    object 
 9   Founded             742 non-null    int64  
 10  Type of ownership   742 non-null    object 
 11  Industry            742 non-null    object 
 12  Sector              742 non-null    object 
 13  Revenue             742 non-null    object 
 14  Competitors         742 non-null    object 
 15  Hourly              742 non-null    int64  
 16  Employer provided   742 non-null    int64  
 17  Lower Salary        742 non-null    int64  
 18  Upper Salary        742 non-null    int64  
 19  Avg Salary(K)       742 non-null    float64
 20  company_txt         742 non-null    object 
 21  Job Location        742 non-null    object 
 22  Age                 742 non-null    int64  
 23  Python              742 non-null    int64  
 24  spark               742 non-null    int64  
 25  aws                 742 non-null    int64  
 26  excel               742 non-null    int64  
 27  sql                 742 non-null    int64  
 28  sas                 742 non-null    int64  
 29  keras               742 non-null    int64  
 30  pytorch             742 non-null    int64  
 31  scikit              742 non-null    int64  
 32  tensor              742 non-null    int64  
 33  hadoop              742 non-null    int64  
 34  tableau             742 non-null    int64  
 35  bi                  742 non-null    int64  
 36  flink               742 non-null    int64  
 37  mongo               742 non-null    int64  
 38  google_an           742 non-null    int64  
 39  job_title_sim       742 non-null    object 
 40  seniority_by_title  742 non-null    object 
 41  Degree              742 non-null    object 
dtypes: float64(2), int64(23), object(17)
memory usage: 243.6+ KB
```

### Data cleaning

The following step are done to make the dataset as clean as possible

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


The final result after the cleaning process if a dataset with **721** rows and **31** columns.

### Visualization


