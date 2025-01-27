# Hotel Booking Dataset Analysis

This project involves analyzing hotel booking data to explore booking patterns, cancellations, and customer preferences. The dataset includes 36275 unique booking records from a hotel management system, covering booking details from 2017 to 2018. The analysis utilizes R for data cleaning, transformation, and preliminary analysis, and Power BI for visualization and creating interactive dashboards.

## Dataset Overview

- **Number of records**: 36275
- **Number of fields**: 19
- **Source**: [Kaggle - Hotel Reservations Dataset]([https://www.kaggle.com/datasets](https://www.kaggle.com/datasets/ahsan81/hotel-reservations-classification-dataset/data))
- **Time period**: 2017 - 2018

### Key Features

- **Customer Preferences**: Information such as preferred room types, meal plans, and booking status.
- **Booking Patterns**: Includes trends based on the day of the week, month, and holiday periods.
- **Cancellation Behavior**: Examines previous cancellations and cancellation rates.
- **Revenue Generation**: Insights into pricing fluctuations and segmentation by room types.

## Tools and Technologies Used

- **R**: Used for data cleaning, transformation, and preliminary analysis.
- **Power BI**: Used for data visualization and creating interactive dashboards.
- **DAX**: Employed for calculating various metrics, such as bookings, cancellations, weekends, and average prices.

## Data Processing and Analysis

### Data Cleaning and Transformation

The dataset required several cleaning and processing steps:

1. **Standardization of columns**: Removed extra spaces in the "Form" field.
2. **Handling Missing Values**: Identified and filled missing values for consistency.
3. **Leap Year Adjustment**: February 29th was adjusted to February 28th to maintain consistency across the data.
4. **Filtering Incomplete Data**: Removed irrelevant or incomplete records.
5. **Date Table Creation**: Created a `dimDate` table for time-based analysis, which includes various date attributes like weekday, weekend, month, and year.

### Code Example

Here is an example of the code used to handle missing values, correct leap year dates, and create a new date column:

```r
# Check for missing values
sum(!complete.cases(hotel))
colSums(is.na(hotel))

# Create date column by combining year, month, and day
hotel$date <- tryCatch(
  as.Date(paste(hotel$arrival_year, hotel$arrival_month, hotel$arrival_date, sep = '-'), format = '%Y-%m-%d'),
  error = function(e) NA
)

# Correct February 29th for leap years
hotel$arrival_date[hotel$arrival_month == 2 & hotel$arrival_date == 29] <- 28
```
## Visualization and Insights

Power BI was used to create various visualizations, including:

- **Bar Charts**: Total bookings by month.
- **Line Charts**: Trends during weekends and holidays.
- **Boxplots**: Price fluctuations based on room types and meal plans.

## Key Insights

- **Booking Trends**: Bookings are most concentrated in the first half of the month, with significant peaks towards the end.
- **Weekend Bookings**: Weekend bookings show a strong variation year by year, with certain months having higher booking volumes.
- **Cancellation Rate**: The cancellation rate is 32.76%, with longer stays and specific meal plans contributing to higher cancellations.

## Key Findings and Value Creation

- **Revenue Optimization**: By focusing on high-demand periods (peak booking days), hotels can optimize pricing and offer promotions.
- **Customer Segmentation**: Segmenting bookings based on room types and meal plans provides deeper insights into customer preferences.
- **Cancellation Management**: A more targeted approach to handling cancellations, especially for longer stays and specific meal plans, could help reduce losses.

