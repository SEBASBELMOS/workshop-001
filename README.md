# Data Engineer Workshop -001: Python Data Engineer Code Challenge

## Overview

This project is a real exercise modeled after a job interview scenario for a Data Engineer role. The objective is to:
- **Migrate data** from a CSV file into a relational database.
- **Perform data cleaning and transformation** based on specific criteria.
- **Visualize metrics** using Python libraries to generate insightful charts.

The CSV contains 50k rows of candidate data (e.g., first name, last name, email, country, application date, years of experience, seniority, technology, Code Challenge Score, and Technical Interview Score). A candidate is considered **HIRED** if both the Code Challenge Score and Technical Interview Score are greater than or equal to 7.

## Project Structure

├── Dataset.csv # Raw candidate data 
├── notebooks/ 
│ 
└── DataEngineer.ipynb # Jupyter Notebook containing the full workflow: 
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
   cd your_repository

2. **Set Up a Virtual Environment (recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate   # On Windows, use `venv\Scripts\activate`

3. **Install Required Packages:**
    ```bash
    pip install pandas sqlalchemy matplotlib jupyter

## Workflow

The Jupyter Notebook (DataEngineer.ipynb) contains the following sections:

1. **Data Ingestion & Cleaning:**

- Reading the CSV file using pandas.read_csv() with the appropriate delimiter.
- Cleaning the data (handling missing values, converting data types).
- Transforming the data (e.g., converting Application Date to a datetime object and extracting the year).

2. **Database Setup & Data Migration:**

- Creating a SQLite database.
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

## Notes

- Hiring Criteria: A candidate is considered hired if both the Code Challenge Score and Technical Interview Score are ≥ 7.
- Customization: You may adjust the queries, visualization styles, or even the choice of database based on your preferences.
- Version Control: Make sure to commit all changes to GitHub to keep your progress registered.