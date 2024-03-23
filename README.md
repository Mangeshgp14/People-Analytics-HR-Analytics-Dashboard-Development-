<h1 align="center">People Analytics : HR Analytics Dashboard Development</h1>


<img width="1000" src="https://github.com/Mangeshgp14/People-Analytics-HR-Analytics-Dashboard-Development-/blob/main/HR%20Analytics.jpg" >

<h3>Project Report : <a href="https://docs.google.com/document/d/1rnj3-LmxuiUeKIMZCYmahlwEMm9ZHICnR6tiuZkZqok/edit?usp=sharing">Link</a></h3>

<h3>Business Problem ❓:</h3>
<p>
The Human Resources department of ABC, a multinational company has approached our analytics firm. They are seeking our help in building a modern, interactive dashboard to present to their management executives.
They have identified some key aspects which need to be depicted in these dashboards.
They want a dynamic dashboard that seamlessly connects to their prevailing database and provides actionable insights to the stakeholders.
<ol>
   <li> The client wants to present some KPIs such as employee count, employee diversity, YoY growth, etc to the top executive management.
   </li>
   <li>They also want to analyze the hiring process of the organization where the important aspects to be presented would be the hiring source, quality of employees hired from these sources, attrition rate, employee satisfaction score, etc.
   </li>
 </ol>
 Apart from these requirements, if our firm can provide some additional insights or suggestions that may prove vital in the app development, they can surely do so.
</p>

<h3>Solution 💡:</h3>

<h4>1. Understanding client's requirement 🤝🏻 </h4>

1.1. The client has requested the development of dashboards to visually depict the current employee diversity within their organization, as well as to showcase the existing hiring process.<br>
1.2. Key Performance Indicators (KPIs) for the first objective include the gender ratio, total employee count, and year-on-year growth.<br>
1.3. KPIs for the second objective encompass the attrition rate, employee engagement and satisfaction scores, and the quality of past recruitments.<br>
1.4. The client prefers simple, user-friendly dashboards that are easy to use and understand.


<h4>2. Understanding client's database system 🛢️ </h4>

2.1. The client's current employee management system stored the data in the form of Excel files. They are going to provide these files as the input to our data pipeline. <br>
2.2. It will be a single Excel file that will contain all the data points necessary to satisfy the client's dashboard requirement.

<h4>3. Building Data Pipeline </h4>

3.1. To automate the entire workflow and ensure the data is kept secure, the best approach would be to load the data from the Excel file into an SQL database and connect it to PowerBI to create a seamless, robust, and secure data pipeline that can be constant monitored and updates as per requirement.
3.2. We will be using Python to load data into a MySQL relational database. 
3.3. The Python library named 'sqlalchemy' will be used to connect to MySQL and create a database and ingest data into it.

**1.1. Python Script to load the dataset(CSV files) into MySQL database**

````PYTHON
# Installing necessary libraries
#!pip install mysql-connector-python
#!pip install pandas
#!pip install sqlalchemy

#Also create a python file name 'config' that contains all the confidential credentials.
````

````PYTHON
# Importing Libraries
import pandas as pd
from sqlalchemy import create_engine
import config
````

````PYTHON
# MySQL database configuration
db_config = {
    'user': config.username,
    'password': config.password,
    'host': config.host,
    'raise_on_warnings': True
}

# Create a SQLAlchemy engine to connect to the MySQL server
mysql_engine = create_engine(f"mysql+mysqlconnector://{db_config['user']}:{db_config['password']}@{db_config['host']}")
````
````PYTHON
# Create a new database
new_database_name = 'HR_ANALYTICS_DATABASE'
with mysql_engine.connect() as connection:
    connection.execute(f"CREATE DATABASE IF NOT EXISTS {new_database_name}")

# Connect to the newly created database
db_config['database'] = new_database_name
engine = create_engine(f"mysql+mysqlconnector://{db_config['user']}:{db_config['password']}@{db_config['host']}/{db_config['database']}")

````


````PYTHON
# Loading CSV files as tables into the database
csv_files = ['HR_data']

for i in csv_files :
    
    # CSV file path
    csv_file_path = f'{i}.csv'

    # Table name in MySQL
    table_name = f'{i}'

    # Read CSV into a Pandas DataFrame
    df = pd.read_csv(csv_file_path)

    # Insert DataFrame records into MySQL using SQLAlchemy


<h4>4. Developing Dashboard </h4>
<h4>5. Deriving Insights </h4>




<h3>Tech Stack</h3>

 <ol>
  <li>
   Excel: Data Loading
  </li>
    <li>
   Python (Pandas): Data Preprocessing, Data loading into Database
  </li>
    <li>
   MySQL: Data Storage
  </li>
    <li>
   Power BI: Dashboard Development
  </li>
 </ol>
 

<h3>Key Insights</h3>
