# sales_eda.py
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# ================================
# Load Dataset
# ================================
df = pd.read_csv('data/sales.csv')

# Quick Overview
print("=== First 5 Rows of Dataset ===")
print(df.head())
print("\n=== Summary Statistics ===")
print(df.describe())

# ================================
# Key Takeaways
# ================================
print("\n=== Key Insights ===")

# 1. Dominant Product Focus
dominant_category = df['Category'].value_counts().idxmax()
dominant_brand = df['Brand'].value_counts().idxmax()
print(f"- Dominant product category: {dominant_category}")
print(f"- Dominant brand: {dominant_brand}")

# 2. Promotion Effectiveness
avg_sales_promoted = df[df['Promotion'] == 1]['SalesVolume'].mean()
avg_sales_non_promoted = df[df['Promotion'] == 0]['SalesVolume'].mean()
print(f"- Avg sales (Promoted items): {avg_sales_promoted:.2f}")
print(f"- Avg sales (Non-Promoted items): {avg_sales_non_promoted:.2f}")
if avg_sales_promoted > avg_sales_non_promoted:
    print("  => Promotions appear to increase sales volume.")

# 3. Price and Sales Volume Independence
correlation = df['Price'].corr(df['SalesVolume'])
print(f"- Correlation between Price and SalesVolume: {correlation:.2f}")
if abs(correlation) < 0.3:
    print("  => Price does not strongly affect sales volume.")

# 4. Geographical Diversity
top_countries = df['Country'].value_counts().head(3)
print("- Top product source countries:")
print(top_countries)

# ================================
# Visualizations
# ================================
sns.set(style="whitegrid")

# Sales Volume by Category
plt.figure(figsize=(8,5))
sns.barplot(x='Category', y='SalesVolume', data=df)
plt.title('Sales Volume by Category')
plt.tight_layout()
plt.savefig('images/sales_by_category.png')
plt.show()

# Sales Volume by Brand
plt.figure(figsize=(8,5))
sns.barplot(x='Brand', y='SalesVolume', data=df)
plt.title('Sales Volume by Brand')
plt.xticks(rotation=45)
plt.tight_layout()
plt.savefig('images/sales_by_brand.png')
plt.show()

# Promotion Effectiveness
plt.figure(figsize=(6,4))
sns.boxplot(x='Promotion', y='SalesVolume', data=df)
plt.title('Sales Volume: Promoted vs Non-Promoted')
plt.xticks([0,1], ['Non-Promoted', 'Promoted'])
plt.tight_layout()
plt.savefig('images/promotion_effect.png')
plt.show()

# Price vs Sales Volume
plt.figure(figsize=(6,4))
sns.scatterplot(x='Price', y='SalesVolume', hue='Category', data=df)
plt.title('Price vs Sales Volume by Category')
plt.tight_layout()
plt.savefig('images/price_vs_sales.png')
plt.show()

# ================================
# End of Analysis
# ================================
print("\nAnalysis Complete. Charts saved in the 'images/' folder.")
## Author
**Ramatu Sulemana**  
Data Analyst  
[LinkedIn – www.linkedin.com/in/ramatu-sulemana-a51117376]  
[GitHub – customer-churn-revenue-risk-analysis]

