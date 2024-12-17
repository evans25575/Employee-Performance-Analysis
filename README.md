# Employee-Performance-Analysis
# Employee Performance Analysis  

## Project Overview  
This project analyzes employee performance using metrics such as experience, appraisal scores, and departmental data.

## Tools Used  
- **Programming Language**: R  
- **Libraries**: ggplot2, dplyr  

## Key Features  
1. **Data Cleaning**: Ensured no missing values.  
2. **Performance Analysis**: Evaluated performance based on experience and appraisal scores.  
3. **Visualization**:  
   - Experience vs Performance Scatter Plot  
   - Appraisal Score Distribution  

## Results  
- **Key Insights**:  
   - Experienced employees generally performed better.  
   - The IT department had the highest appraisal scores.  

## Files Included  
- `employee_performance_analysis.R` - Full R code.  
- `experience_vs_performance.png` - Scatter plot.  
- `appraisal_score_distribution.png` - Histogram.  
- `department_summary.csv` - Summary table with departmental insights.  

## How to Use  
1. Clone this repository:  
   ```bash
   git clone https://github.com/evans25575/Employee_Performance_Analysis.git
   
CODES

# Load necessary libraries
library(ggplot2)
library(dplyr)

# Simulated Dataset
employee_data <- data.frame(
  Employee_ID = 1:10,
  Department = c("Sales", "HR", "IT", "Sales", "IT", "HR", "Finance", "IT", "Finance", "Sales"),
  Experience = c(2, 5, 7, 3, 10, 6, 8, 4, 9, 1),
  Appraisal_Score = c(78, 85, 90, 72, 95, 88, 92, 80, 85, 70),
  Marketing_Budget = c(2000, 1500, 3000, 1800, 3500, 1600, 2800, 2100, 3000, 1300),
  Quarterly_Performance = c(85, 88, 92, 80, 95, 86, 90, 83, 87, 75)
)

# View the dataset
print("Employee Performance Dataset")
print(employee_data)

# Data Cleaning: Check for missing values
missing_values <- colSums(is.na(employee_data))
print("Missing Values per Column:")
print(missing_values)

# Summary Statistics
summary_stats <- employee_data %>%
  summarise(
    Avg_Experience = mean(Experience),
    Avg_Appraisal = mean(Appraisal_Score),
    Avg_Performance = mean(Quarterly_Performance)
  )
print("Summary Statistics:")
print(summary_stats)

# Visualization 1: Experience vs Performance
ggplot(employee_data, aes(x = Experience, y = Quarterly_Performance, color = Department)) +
  geom_point(size = 4) +
  labs(title = "Experience vs Performance by Department",
       x = "Experience (Years)",
       y = "Quarterly Performance") +
  theme_minimal()

# Save the plot
ggsave("experience_vs_performance.png")

# Visualization 2: Appraisal Score Distribution
ggplot(employee_data, aes(x = Appraisal_Score, fill = Department)) +
  geom_histogram(binwidth = 5, alpha = 0.7, position = "dodge") +
  labs(title = "Distribution of Appraisal Scores by Department",
       x = "Appraisal Score",
       y = "Count") +
  theme_minimal()

# Save the plot
ggsave("appraisal_score_distribution.png")

# Summary Table by Department
department_summary <- employee_data %>%
  group_by(Department) %>%
  summarise(
    Avg_Experience = mean(Experience),
    Avg_Appraisal_Score = mean(Appraisal_Score),
    Avg_Performance = mean(Quarterly_Performance)
  )
print("Summary Table by Department:")
print(department_summary)

# Export Department Summary to CSV
write.csv(department_summary, "department_summary.csv", row.names = FALSE)
