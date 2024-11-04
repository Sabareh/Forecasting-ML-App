# Forecasting-ML-App
R machine learning application that performs forecasting on pharmaceutical medicine sales data using information obtained form NHS (UK) General Practitioner (GP) datasets.

# NHS Prescription Forecasting Dashboard

## Overview
This Shiny dashboard application provides time series forecasting capabilities for NHS prescription data. It allows users to analyze and forecast prescription quantities and sales revenue using various forecasting models.

## Features
- Interactive product selection
- Multiple forecasting models:
  - Auto (ETS)
  - Holt-Winters
  - TBATS
  - Auto ARIMA
  - Markov Chain Monte-Carlo (Prophet)
- Metrics analysis:
  - Sales Revenue
  - Quantity
- Visualization components:
  - Top 5 related products comparison
  - Time series decomposition
  - Forecast plots with confidence intervals
- Detailed data tables for both historical and forecast data

## Prerequisites
The following R packages are required:
```r
required_packages <- c(
  "devtools",
  "shinyWidgets",
  "data.table",
  "DT",
  "forecast",
  "ggplot2",
  "shinyjs",
  "plotly",
  "xts",
  "prophet",
  "tidyverse",
  "shinydashboard"
)
```

## Installation

1. Clone the repository:
```bash
git clone https://github.com/Sabareh/Forecasting-ML-App
cd Forecasting-ML-App
```

2. Install required packages:
```r
for(pkg in required_packages){
  if(!require(pkg, character.only = TRUE)){
    install.packages(pkg)
  }
}
```

3. Ensure you have the data file:
- `productdb.rds` should be in the root directory

## Usage

1. Start the application:
```r
shiny::runApp()
```

2. Using the dashboard:
   - Select a product from the dropdown menu
   - Choose a forecasting model
   - Select the metric (Sales Revenue or Quantity)
   - Toggle the ETS decomposition if needed
   - View the results in the various plots and tables

## Data Structure
The application expects a productdb.rds file with the following columns:
- BNFNAME: Product name
- CHEMSUB: Chemical substance
- QUANTITY: Prescription quantity
- ACTCOST: Actual cost
- month: Date in YYYY-MM format

## Features Breakdown

### Product Selection
- Dropdown menu with autocomplete functionality
- Shows all available products in the NHS database

### Forecasting Models
1. **Auto (ETS)**
   - Automatic exponential smoothing
   - Best for general forecasting

2. **Holt-Winters**
   - Triple exponential smoothing
   - Handles trend and seasonality

3. **TBATS**
   - Handles complex seasonality
   - Good for multiple seasonal patterns

4. **Auto ARIMA**
   - Automatic ARIMA model selection
   - Best for stationary time series

5. **MCMC (Prophet)**
   - Facebook's Prophet algorithm
   - Handles missing data and outliers

### Visualizations
1. **Top 5 Plot**
   - Shows related products
   - Interactive plotly visualization

2. **Forecast Plot**
   - Shows predictions with confidence intervals
   - Highlights trends and patterns

3. **Time Series Plot**
   - Historical data visualization
   - Optional ETS decomposition

### Data Tables
1. **Forecast Data**
   - Shows predicted values
   - Includes confidence intervals
   - Currency formatting for revenue

2. **Historical Data**
   - Shows raw data
   - Sortable and searchable

## Styling
- Custom CSS in `www/packt.css`
- Uses Google Fonts:
  - Fanwood Text
  - Varela

## Error Handling
- Validates input data
- Handles missing data gracefully
- Provides user feedback for errors

## Performance Considerations
- Uses reactive programming
- Efficient data.table operations
- Optimized plotting with plotly

## Contributing
Please read CONTRIBUTING.md for details on our code of conduct and the process for submitting pull requests.

## License
This project is licensed under the MIT License - see the LICENSE.md file for details.

## Acknowledgments
- NHS Digital for the prescription data
- R Shiny community
- Contributors to the various R packages used

## Support
For support, please open an issue in the repository or contact [maintainer email].

## Version History
- 1.0.0: Initial release
  - Basic forecasting functionality
  - Five forecasting models
  - Interactive visualizations
