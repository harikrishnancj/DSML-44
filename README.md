
# DSML 44

Assignment 1
  
     Removing duplication,Blank row,Heading;
Assignement 2

       Addcolumn,select column,sum,if,new measure new column,dateddiff,standarddiv,sumx;
Assignment 3

      charts, maps,slicer ,measure,filter report level,drills ,hierarchies,relationship;
# COVID-19 Global Impact Analysis Report

## Data Source
- **Source**: [Kaggle COVID-19 Dataset](https://www.kaggle.com/datasets/imdevskp/corona-virus-report)
- **Date Range**: January 2020 to July 2020 (or the last available update)

---

## 1. Importing and Preprocessing the Dataset

- **Data Import**: The dataset was imported into Power BI for analysis.
- **Data Cleaning**:
  - **Duplicates Removal**: Identified and removed any duplicate rows from the dataset.
  - **Blank Rows**: Removed blank rows to ensure accurate data analysis.
  - **Null Values**: Replaced any null values with zeros to avoid errors in calculations.

- **Issues with WHO Region Data**:
  The dataset had incomplete WHO Region information, so I performed the following steps to correct it:

  1. **Adding a WHO Region Column**:
     - A new column `WHO reg` was created to fill missing WHO Region values with the corresponding continent name:
       ```DAX
       WHO reg = IF(worldometer_data[WHO Region] = "", worldometer_data[Continent], worldometer_data[WHO Region])
       ```

  2. **Correcting the WHO Region Data**:
     - For cases where the region was "Australia/Oceania", I updated it to "Western Pacific":
       ```DAX
       whor = IF(worldometer_data[WHO reg] = "Australia/Oceania", "Western Pacific", worldometer_data[WHO reg])
       ```

  3. **Consolidating Regions**:
     - Combined North and South America into "Americas":
       ```DAX
       Whoregion = IF(worldometer_data[whor] = "North America" || worldometer_data[whor] = "South America", "Americas", worldometer_data[whor])
       ```

  - **Final Data Purification**: Removed any remaining null or invalid values to ensure the dataset was clean and ready for analysis.

---

## 2. Measures and New Calculations

- Created various measures using DAX to calculate the sum of active cases, recoveries, and deaths.
- Added calculations to track trends in the data using **SUMX** and other DAX functions for accurate data analysis.

---

## 3. Dashboard Overview

### Page 1: Overview Page
- **Main Title**: *COVID-19 Global Impact Analysis Report*
- **Subtitle**: *An Analysis of Cases, Recoveries, and Regional Trends Using Data from WHO and Worldometer*

- **Text Box**: Added a text box with the following details:
  - **Source**: Kaggle COVID-19 dataset
  - **Date Range**: January 2020 to [last update date]
  - **Important Fields**: Total Cases, Deaths, Recoveries, Active Cases, WHO Region, Continent
  - **Project Objectives**:
    - Understand COVID-19's spread across regions.
    - Analyze trends in active cases, recoveries, and deaths by continent and WHO region.
    - Identify insights into the pandemic's progression patterns.

- **Image**: Inserted relevant images to visualize global COVID-19 trends.

- **Navigation Button**: Added a button to navigate to the next page of the dashboard.

---

### Page 2: Interactive Slicer and Key Metrics
- **Visual Elements**:
  - Added 4 **gauge charts**, 3 **cards**, and a **map** to show key metrics such as:
    - Sum of Active Cases
    - Sum of Deaths
    - Sum of Recoveries
    - Confirmed COVID-19 Cases
  - **Slicer**: Implemented slicers for dynamic filtering by region, continent, and WHO region.

  - **4 Gauge Charts**: 
    - Display key metrics in a visual format:
      - **Active Cases**
      - **Deaths**
      - **Recoveries**
      - **Confirmed COVID-19 Cases**
    
  - **3 Cards**: 
    - Each card displays a summary statistic:
      - **Total Confirmed Cases** (Global count)
      - **Total Active Cases** (Global count)
      - **Total Deaths** (Global count)
    
  - **Map**: 
    - The map visualizes the geographical distribution of COVID-19 cases globally. It uses color coding to indicate the **number of confirmed COVID-19 cases** in different countries or regions.
    - Users can hover over countries to view detailed metrics (e.g., Active cases, Total cases, Deaths).

  - **Slicer**:
    - A **slicer** is used for filtering the data by region, continent, and WHO region. It allows users to narrow down the data to specific geographical areas and update the visuals accordingly.

---

### Page 3: Hierarchical Data and Drill-Down Analysis
- **Hierarchical Structure**: Set up drill-down functionality between regions, continents, and WHO regions to analyze active cases in greater detail.
  - Users can click on a specific region or continent to drill down into more granular data (e.g., by WHO region).

- **Line Chart**: 
  - Displayed trends of active COVID-19 cases by WHO region over time.
  - Added **date** as a page-level filter to allow users to explore data over different months.
  - Used **bookmarks** to show trends for specific months (e.g., January, February, March, etc.).

---

### Page 4: Additional Insights and Relationships
- **Advanced Charts**: 
  - Added various charts to explore relationships between different data points.
  - Explored how active cases correlate with recoveries, deaths, and confirmed cases across regions and WHO regions.

---

## 4. Conclusion

This Power BI report offers comprehensive insights into the global spread of COVID-19 using data from WHO and Worldometer. Key findings include:

- Understanding the spread of COVID-19 across regions and continents.
- Analyzing the trends in active cases, recoveries, and deaths globally.
- Gaining data-driven insights into the progression of the pandemic.

The interactive elements, such as slicers and drill-down functionality, allow for a dynamic exploration of the data, providing a more detailed understanding of how COVID-19 has affected different parts of the world over time.

---

## 5. Future Improvements
- Future updates could include more granular data, such as daily cases and recovery rates, to allow for a more detailed trend analysis.
- Incorporate additional external data sources for a more comprehensive analysis.

---

This README serves as a guide to understanding the Power BI COVID-19 report, detailing the steps taken to clean and preprocess the data, as well as providing an overview of the analysis and visualizations included in the report.

   
