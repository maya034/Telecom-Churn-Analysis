# Telecom-Churn-Analysis
Exploring and analyzing the data to discover key factors responsible for customer churn and come up with ways/recommendations to ensure customer retention.
Predict behavior to retain customers. You can analyze all relevant customer data and develop focused customer retention programs. Each row represents a customer, each column contains customer’s attributes described on the column Metadata. The raw data contains 7043 rows (customers) and 21 columns (features). The “Churn” column is our 


Thank you for providing the abstract of the paper. Based on the abstract, I can provide a more detailed breakdown of the key concepts and methodologies discussed in the paper:

https://openacttexts.github.io/LDACourse1/index.html#why-loss-data-analytics




import pandas as pd

# Sample DataFrame (replace this with your actual DataFrame)
data = {
    'Primary_Risk': [75, 80, 70, 85],
    'Secondary_Risk': [60, 55, 65, 50],
    'DIS_Vegetation_BU': [3, 10, 100, 300]
}

df = pd.DataFrame(data)

def calculate_final_score(row):
    # Define the weights for DIS_Vegetation_BU distance ranges
    if row['DIS_Vegetation_BU'] <= 5:
        weight_vegetation = 1.0  # 100% Total_Score
    elif 5 < row['DIS_Vegetation_BU'] <= 50:
        weight_vegetation = 0.85  # 85% Total_Score
    elif 50 < row['DIS_Vegetation_BU'] <= 200:
        weight_vegetation = 0.6  # 60% Total_Score
    elif 200 < row['DIS_Vegetation_BU'] <= 500:
        weight_vegetation = 0.2  # 20% Total_Score
    else:
        weight_vegetation = 0.0  # 0% Total_Score

    # Calculate the final score based on the weighted Total_Score
    final_score = weight_vegetation * row['Total_Score']

    return final_score

# Calculate the final score for each row in the DataFrame
df['Final_Score'] = df.apply(calculate_final_score, axis=1)

# Print the DataFrame with the calculated final scores
print(df)

