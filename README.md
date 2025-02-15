# Workshop -001: Data Engineer 💻

This project was created by **Sebastian Belalcazar** [@SEBASBELMOS](https://github.com/SEBASBELMOS)

---

## Overview 

This project is a real exercise modeled after a job interview scenario for a Data Engineer role. The objective is to:
- **Migrate data** from a CSV file into a relational database.
- **Perform data cleaning and transformation** based on specific criteria.
- **Visualize metrics** using Python libraries to generate insightful charts.

## Dataset Information

The CSV contains 50k rows of candidate data (e.g., first name, last name, email, country, application date, years of experience (YOE), seniority, technology, Code Challenge Score, and Technical Interview Score). A candidate is considered **HIRED** if both the Code Challenge Score and Technical Interview Score are greater than or equal to 7.

- First Name ➜ Object
- Last Name ➜ Object
- Email ➜ Object
- Country ➜ Object
- Application Date ➜ Object
- YOE (years of experience) ➜ Integer
- Seniority ➜ Object
- Technology ➜ Object
- Code Challenge Score ➜ Integer
- Technical Interview Score ➜ Integer

## Project Structure

| Folder/File            | Description |
|------------------------|------------|
| **assets**             | Contains static resources such as images, and other media files for the project documentation |
| **data/**             | Contains datasets used in the workshop |
| ├── candidates.csv    | CSV file with raw candidate data |
| **functions/**        | Python package for database connection |
| ├── db_connection/    | Includes the `db_connection.py` module |
| │ ├── db_connection.py | Establishes a connection to the Postgres database using SQLAlchemy |
| **env/**              | This folder is ignored in `.gitignore`, must be created manually |
| ├── .env             | Stores environment variables for the database connection |
| **notebooks/**        | Contains Jupyter Notebooks with the workflow |
| ├── dataengineer.ipynb | Includes data ingestion, cleaning, and visualisation |
| **pdf/**              | Stores documentation and workshop PDFs |
| ├── activity.pdf     | PDF with instructions for the activity |
| **pyproject.toml**    | Poetry configuration file for managing dependencies |
| **README.md**         | This file |

## Technologies Used

- **Programming Language:** Python 3.13.1 -> [Download here](https://www.python.org/downloads/)
- **Data Handling:** pandas -> [Documentation here](https://pandas.pydata.org/)
- **Database:** PostgreSQL -> [Download here](https://www.postgresql.org/download/)
- **Database Interaction:** SQLAlchemy -> [Documentation here](https://docs.sqlalchemy.org/)
- **Visualization:** Power BI Desktop -> [Download here](https://www.microsoft.com/es-es/power-platform/products/power-bi/desktop)
- **Environment:** Jupyter Notebook -> [VSCode tool used](https://code.visualstudio.com/docs/datascience/jupyter-notebooks)

All the libraries are included in the Poetry project config file (_pyproject.toml_).

## Installation and Setup

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/SEBASBELMOS/workshop-001.git
   cd workshop-001
   ```

2. **Set Up a Virtual Environment (recommended):**
    ```bash
    python -m venv venv
    source venv/bin/Activate.ps1   # On Windows, use: `venv\Scripts\Activate.ps1`
    ```

3. **Update pip and Install Required Packages:**
    ```bash
    python.exe -m pip install --upgrade pip
    pip install pandas sqlalchemy matplotlib jupyter psycopg2-binary dotenv
    ```

4. **Enviromental variables**
    >Realise this in VS Code.

    To establish a connection with the database, we use a module called _connection.py_. This Python script retrieves a file containing our environment variables. Here’s how to create it:
    1. Inside the cloned repository, create a new directory named *env/*.
    2. Within that directory, create a file called *.env*.
    3. In the *.env file*, define the following six environment variables (without double quotes around values):
        ```python
        PG_HOST = #host address, e.g. localhost or 127.0.0.1
        PG_PORT = #PostgreSQL port, e.g. 5432

        PG_USER = #your PostgreSQL user
        PG_PASSWORD = #your user password
        
        PG_DRIVER = postgresql+psycopg2
        PG_DATABASE = #your database name, e.g. postgres
        ```

5. **Installing the dependencies with _Poetry_**
    - Windows: 
        - In Powershell, execute this command: 
            ```powershell
            (Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | py -
            ```
            <img src="https://github.com/SEBASBELMOS/workshop-001/blob/main/assets/poetry_installation.png" alt="Logo" width="600"/>
        - Press Win + R, type _sysdm.cpl_, and press **Enter**. 
        - Go to the _Advanced_ tab, select _environment variable_.
        - Under System variables, select Path → Click Edit.
        - Click _Edit_ and set the path provided during the installation in **PATH** so that the `poetry` command works. ("C:\Users\username\AppData\Roaming\Python\Scripts")
        - Restart Powershell and execute _poetry --version_.

        
    - Linux
        - In a terminal, execute this command:
            ```bash
            curl -sSL https://install.python-poetry.org | python3 -
            ```
            <img src="https://github.com/SEBASBELMOS/workshop-001/blob/main/assets/poetry_linux.png" alt="Logo" width="600"/>
        - 



---
## Workflow

The Jupyter Notebook (dataengineer.ipynb) contains the following sections:

1. **Data Ingestion & Cleaning:**

- Reading the CSV file using pandas.read_csv() with the delimiter ";".
    ```bash
    import pandas as pd

    df = pd.read_csv('../data/candidates.csv', delimiter=';')
    ```
- Cleaning the data (handling missing values, converting data types).

- Transforming the data (e.g., converting Application Date to a datetime object and extracting the year).
    ```bash
    df['Application Date'] = pd.to_datetime(df['Application Date'], errors='coerce')
    print(df.isnull().sum())
    

    df['Year'] = df['Application Date'].dt.year
    df['Hired'] = (df['Code Challenge Score'] >= 7) & (df['Technical Interview Score'] >= 7)
    ```


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
