# Data Sourcing Challenge

## Project Overview
The program is tasked to allow the NOAA Space Weather Prediction Center to predict the occurrence of a Geomagnetic Storms (GSTs) that are caused by Coronal Mass Ejections (CMEs). To achieve this, users must extract data from NASA's API, specify the data related to CME and GST, and then merge and clean the data for the most optimal predictive models.

## Installation Instructions
1. **Clone the Repository:**
   ```bash
   git clone https://github.com/ezwang8/data-sourcing-challenge.git
   ```
   
2. **Ensure Python is installed:**
   Verify Python installation:
   ```bash
   python --version
   ```
   If not installed, download it from [python.org](https://www.python.org/downloads/).

3. **Install Jupyter Notebook:**
   If Jupyter is not installed, run:
   ```bash
   pip install jupyter
   ```

4. **Install necessary Packages:**

   Install pandas for data manipulation and analysis:
   ```bash
   pip install pandas
   ```

   Install requests for making API calls to NASA's API:
   ```bash
   pip install requests
   ```

   Install python-dotenv for loading environment variables (the API key) from a .env file:
   ```bash
   pip install python-dotenv
   ```

6. **Navigate to the Project Directory:**
   ```bash
   cd athletic_sales_analysis
   ```

7. **Launch Jupyter Notebook:**
   Open the notebook interface:
   ```bash
   jupyter notebook
   ```

8. **Open the Notebook:**
   In Jupyter, locate the `retrieve_data.ipynb` file and run the cells for analysis.

## File Roles
- **retrieve_data.ipynb:** The main script that performs the analysis. It retrieves, processes, and analyzes CME and GST data from NASA's API.
- **.env:** The file that contains the NASA API key, which is required for accessing the API securely.

## Steps
1. **Request CME Data:**
   - Use NASA's DONKI API to request Coronal Mass Ejection (CME) data. 
   - Keep the essential columns (`activityID`, `startTime`, and `linkedEvents`). Remove the rows without any `linkedEvents` since those sections aren't related to GSTs.

2. **Request GST Data:**
   - Use NASA API to request Geomagnetic Storm (GST) data.
   - Keep the essential columns (`activityID`, `startTime`, and `linkedEvents`). Clean the data by exploding the `linkedEvents` field, so every entry is related to a GST event.

3. **Merge and Clean the Data:**
   - Merge the two datasets (CME and GST) on the columns (`gstID`, `CME_ActivityID`, `GST_ActivityID`, and `cmeID`).
   - Check the make sure the merged dataset's rows match between both DataFrames. Drop any unnecessary columns or null values.

4. **Calculate Time Difference:**
   - Create a new column called `timeDiff` to compare the start times of the CME and the GST.

5. **Descriptive Statistics:**
   - Use the `describe()` function to create key statistics for the `timeDiff` column. The statistics help us check how long it takes for a CME to turn into a GST event.

6. **Export Cleaned Data:**
   - Export the cleaned and merged dataset to a CSV file, without the DataFrame's index, for future analysis.

## Summary
- The statistics created from the timeDiff column has found that the average time difference between the detection of a CME and the onset of a GST is around 2-3 days.
- With this information, NASA and the Space Weather Prediction Center will now have a clearer idea on predicting upcoming storms that would impact their satellite and power grid systems.
