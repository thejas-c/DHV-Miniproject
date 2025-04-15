# Infectious Disease Data Visualization

This project provides a Python script to visualize sporadic infectious disease data from an Excel file using the `pandas` and `plotly` libraries. It generates a variety of interactive plots to explore trends, geographic distribution, and disease prevalence.


## Setup

1.  **Prepare Your Data:**

    *   The script expects the data to be in an Excel file.  The default filename is `SPORADIC INFECTIOUS DISEASES.xlsx`.
    *   The first sheet of the Excel file is read by default.  If your data is on a different sheet, modify the `sheet_name` variable in the script.
    *   **Important:** The Excel file **must** contain the following columns with exact names (case-sensitive):

        *   `infectious disease`
        *   `Record period`
        *   `Location`
        *   `Cumulative cases (deaths) reported during the record period`
        *   `Cumulative cases (deaths) reported since 01/01/2023`

2.  **Configure the Script:**

    *   Open the `main.py` script (or whatever you named the python file).
    *   **Modify `excel_file`:** Change the `excel_file` variable to the correct path to your Excel file. For example:

        ```python
        excel_file = '/path/to/your/data.xlsx'
        ```

    *   **Modify `sheet_name` (if needed):**  If your data is not on the first sheet of the Excel file, update the `sheet_name` variable:

        ```python
        sheet_name = 'YourSheetName'
        ```

    *   **Review `location_mapping`:** The script uses a dictionary called `location_mapping` to map location names to their latitude and longitude coordinates for the geographic map.  **Carefully check this dictionary!**

        *   Ensure that all the `Location` values in your Excel file are present as keys in the `location_mapping`.
        *   Verify that the latitude and longitude coordinates are accurate.  Incorrect coordinates will lead to misrepresentation on the map. If a location is missing, add it to the dictionary. Example:

            ```python
            location_mapping = {
                'Panama': {'lat': 8.5380, 'lon': -80.7821},
                'New Location': {'lat': 34.0522, 'lon': -118.2437}, # Example
                ...
            }
            ```

## Usage

1.  **Run the Script:**

    Open your terminal or command prompt, navigate to the directory where you saved the script, and run it using Python:

    ```bash
    python main.py  # Replace main.py with the actual name of your Python file
    ```

2.  **View the Visualizations:**

    The script will generate several interactive plots using `plotly`. These plots include:

    *   **Time Series Analysis:** Scatter plot of cumulative cases over time for each disease.
    *   **Cases by Location:** Bar chart of cumulative cases by location.
    *   **Geographic Distribution:** Interactive map showing the distribution of infectious diseases.
    *   **Disease Comparison:** Subplots comparing cumulative cases for each disease over time (line plots).
    *   **Detailed Data Table:** Interactive table for inspecting the raw data.
    *   **Cumulative Cases Since 01/01/2023 by Location:** Bar chart.
    *   **Cumulative Cases vs. Cases Since 01/01/2023:** Grouped bar chart.
    *   **Disease Distribution:** Pie chart showing the proportion of total cumulative cases for each disease.

## Data Preprocessing and Cleaning

The script performs the following data preprocessing steps:

*   **Date Extraction:** Extracts dates from the `Record period` column, handling single dates and date ranges.
*   **Data Type Conversion:** Converts cumulative case columns to numeric types.
*   **Missing Value Handling:** Removes rows with missing values in key columns.

## Error Handling

The script includes error handling to catch common issues:

*   **File Not Found:** Checks if the specified Excel file exists.
*   **Missing Columns:** Checks if the required columns are present in the Excel file.
*   **Date Parsing Errors:** Catches errors during date parsing and displays the problematic value.
*   **Missing Latitude/Longitude:** Warns if latitude or longitude data is missing for some locations.

## Output

The script displays the generated plots directly.

## Customization

*   **Plot Customization:** The `plotly` library provides extensive options for customizing the appearance and behavior of the plots. Refer to the `plotly` documentation for details: [https://plotly.com/python/](https://plotly.com/python/)
*   **Data Filtering:** You can modify the script to filter the data based on specific criteria, such as date ranges, locations, or diseases. Add filtering steps after reading the data using `pandas`.
*   **Additional Visualizations:** You can add more types of visualizations to the script to explore different aspects of the data.

## Troubleshooting

*   **"FileNotFoundError":** Double-check that the `excel_file` variable is set to the correct path to your Excel file.
*   **"KeyError":** Ensure that all the location names in your Excel file are present as keys in the `location_mapping` dictionary and that the spelling is correct.
*   **"ValueError" related to dates:** Inspect the `Record period` column in your Excel file for any invalid or unexpected date formats.  The script attempts to handle date ranges, but it might fail if the format is inconsistent. The error message will indicate the specific date string that is causing the problem.
*   **Blank plots or incorrect data:**  Verify that the data in your Excel file is clean and consistent.  Pay attention to missing values, incorrect data types, and spelling errors.
*   **Map not displaying correctly:** Double check the latitude and longitude values in the `location_mapping` dictionary.  Swapped or inaccurate coordinates will cause problems.
