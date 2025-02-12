# Data Engineer Workshop -001: Python Data Engineer Code Challenge

## Overview

This project is a real exercise modeled after a job interview scenario for a Data Engineer role. The objective is to:
- **Migrate data** from a CSV file into a relational database.
- **Perform data cleaning and transformation** based on specific criteria.
- **Visualize metrics** using Python libraries to generate insightful charts.

The CSV contains 50k rows of candidate data (e.g., first name, last name, email, country, application date, years of experience (YOE), seniority, technology, Code Challenge Score, and Technical Interview Score). A candidate is considered **HIRED** if both the Code Challenge Score and Technical Interview Score are greater than or equal to 7.

## Project Structure

├── candidates.csv # Raw candidate data 

├── notebooks/ 

│ 

└── dataengineer.ipynb # Jupyter Notebook containing the full workflow: 

│ # - Data ingestion & cleaning 

│ # - Database setup & migration 

│ # - Querying & visualizations 

└── README.md # This file

## Technologies Used

- **Programming Language:** Python
- **Data Handling:** pandas
- **Database:** SQLite
- **Database Interaction:** SQLAlchemy
- **Visualization:** matplotlib, seaborn
- **Environment:** Jupyter Notebook

## Installation and Setup

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/SEBASBELMOS/workshop-001.git
   cd workshop-001

2. **Set Up a Virtual Environment (recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate.bat   # On Windows, use: `venv\Scripts\activate.bat`

3. **Update pip and Install Required Packages:**
    ```bash
    python.exe -m pip install --upgrade pip
    pip install pandas sqlalchemy matplotlib jupyter

## Workflow

The Jupyter Notebook (dataengineer.ipynb) contains the following sections:

1. **Data Ingestion & Cleaning:**

- Reading the CSV file using pandas.read_csv() with the delimiter ";".
    ```bash
    import pandas as pd

    df = pd.read_csv('../candidates.csv', delimiter=';')

- Cleaning the data (handling missing values, converting data types).

- Transforming the data (e.g., converting Application Date to a datetime object and extracting the year).
    ```bash
    df['Application Date'] = pd.to_datetime(df['Application Date'], errors='coerce')
    print(df.isnull().sum())
    

    df['Year'] = df['Application Date'].dt.year
    df['Hired'] = (df['Code Challenge Score'] >= 7) & (df['Technical Interview Score'] >= 7)


2. **Database Setup & Data Migration:**

- Creating a SQL database.
- Defining the schema using SQLAlchemy.
- Migrating the cleaned data from the CSV into the database.

3. **Querying the Database:**

- Retrieving metrics using SQL queries:
    - Hires by Technology: (Pie Chart)
    - Hires by Year: (Horizontal Bar Chart)
    - Hires by Seniority: (Bar Chart)
    - Hires by Country Over Years: (Multiline Chart for USA, Brazil, Colombia, and Ecuador)

4. **Data Visualization:**

- Creating charts with matplotlib and seaborn:
    - Pie Chart: Displaying hires by Technology.
    - Horizontal Bar Chart: Showing hires by Year.
    - Bar Chart: Presenting hires by Seniority.
    - Multiline Chart: Illustrating hires by Country over Years.

## Hiring Criteria 
A candidate is considered hired if both the Code Challenge Score and Technical Interview Score are greater than or equal to 7.
