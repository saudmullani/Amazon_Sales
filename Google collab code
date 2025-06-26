
import seaborn as sns
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline
%reload_ext autoreload
%autoreload 2

df = pd.read_csv("Amazon Sale Report.csv")
df

df.head()

df.tail()

df.sample(4)

df.info()

df.describe()

print(df.columns)

# Get the index (position) of the "Sales Channel" column:
try:
    sales_channel_index = df.columns.get_loc("Sales Channel")
    print(f"'Sales Channel' column is at index: {sales_channel_index}")
except KeyError:
    print("'Sales Channel' column not found in the DataFrame.")

# Display the first few rows of the "Sales Channel" column:
if "Sales Channel" in df.columns:
    print(df["Sales Channel"].head())

df = df.drop ([ "Sales Channel ","SKU", "ASIN", "Unnamed: 22", "ship-postal-code",  "fulfilled-by","Style","B2B"], axis=1)

df.isnull().sum()

print(df.duplicated().sum())

df_cleaned = df.dropna(subset=['promotion-ids'])
df.dropna(subset=['promotion-ids'], inplace=True)
df



df["total sales"] = df["Qty"]*df["Amount"]
df

df.info()

df.isnull().sum()
df

df

# Convert object columns to numeric using encoding
df_encoded = df.copy()

# Identify object columns
object_cols = df.select_dtypes(include=['object']).columns

#  Apply encoding to object columns
for col in object_cols:
  df_encoded[col] = df_encoded[col].astype("category").cat.codes

# Calculate the correlation matrix
correlation_matrix = df_encoded.corr()

"""#

"""

plt.figure(figsize=(12, 4.5))  # Changed width from 12 to 20
df['Date'] = pd.to_datetime(df['Date'])  # Convert to datetime if needed
df['Year'] = df['Date'].dt.year
df['Month'] = df['Date'].dt.month
df['Day'] = df['Date'].dt.day

sns.lineplot(x='Date', y='total sales', data=df)
plt.xlabel('Date')
plt.ylabel('total sales')
plt.title(' total sales over date')
plt.xticks(rotation=45, ha='right')
plt.show()

top_10_categories = df['Category'].value_counts().head(10)

plt.figure(figsize=(12, 5))
ax = sns.barplot(x=top_10_categories.index, y=top_10_categories.values)
plt.xlabel('Category')
plt.ylabel('Number of Orders')
plt.title('Top 10 Categories by Number of Orders')
plt.xticks(rotation=45, ha='right')

# Add number labels on top of bars
for p in ax.patches:
    ax.annotate(f'{p.get_height():.0f}', (p.get_x() + p.get_width() / 2., p.get_height()),
                ha='center', va='center', fontsize=10, color='black', xytext=(0, 5),
                textcoords='offset points')

plt.show()


category_counts = df['Category'].value_counts().head(5)  # Get top 5 categories
plt.figure(figsize=(6.3, 8))
explode = [0,0,0,0,0] * len(category_counts)

# Create the pie chart (without explode)
wedges, texts, autotexts = plt.pie(category_counts,
                                  autopct='%1.1f%%',  # Format percentages
                                  startangle=90,
                                  textprops={'fontsize': 13, 'color': 'black'},  # Set text properties
                                  pctdistance=1.1)  # Adjust pctdistance to move labels outside


# Add category labels outside the slices with adjusted spacing
plt.legend(wedges, category_counts.index,
          title="Categories",
          loc="center left",
          bbox_to_anchor=(1, 0, 0.5, 1))  # Adjusted bbox_to_anchor

plt.title('Pie Chart of Top 5 Category Distribution', fontsize=14)  # Updated title
plt.tight_layout()  # Adjust layout to prevent labels from being cut off
plt.show()

import seaborn as sns

top_10_states = df['ship-state'].value_counts().head(10)

plt.figure(figsize=(14, 6))
ax = sns.barplot(x=top_10_states.values, y=top_10_states.index)  # Switch x and y back
plt.xlabel('Number of Orders')  # Switch labels back
plt.ylabel('Ship State')
plt.title('Top 10 Ship States')
plt.xticks(rotation=0, ha='center')  # Adjust x-tick rotation (optional)
plt.yticks(rotation=0, ha='right')  # Adjust y-tick rotation

# Add quantity labels on top of bars (adjust position for horizontal bars)
for p in ax.patches:
    ax.annotate(f'{p.get_width():.0f}', (p.get_width(), p.get_y() + p.get_height() / 2.),
                ha='left', va='center', fontsize=10, color='black', xytext=(5, 0),
                textcoords='offset points')

plt.show()
qty_by_size = df.groupby('Size')['Qty'].sum().reset_index()

plt.figure(figsize=(10, 6))
ax = sns.barplot(x='Size', y='Qty', data=qty_by_size)  # Use barplot for vertical bars

plt.xlabel('Size')
plt.ylabel('Total Quantity')
plt.title('Quantity by Size')
plt.xticks(rotation=45, ha='right')

# Add labels on top of bars
for p in ax.patches:
    ax.annotate(f'{p.get_height():.0f}', (p.get_x() + p.get_width() / 2., p.get_height()),
                ha='center', va='center', fontsize=10, color='black', xytext=(0, 5),
                textcoords='offset points')

plt.show()

qty_by_size = df.groupby('Size')['Qty'].sum().reset_index()

plt.figure(figsize=(11, 6))
ax = sns.barplot(x='Size', y='Qty', data=qty_by_size)  # Use barplot for vertical bars

plt.xlabel('Size')
plt.ylabel('Total Quantity')
plt.title('Quantity by Size')
plt.xticks(rotation=45, ha='right')

# Add labels on top of bars
for p in ax.patches:
    ax.annotate(f'{p.get_height():.0f}', (p.get_x() + p.get_width() / 2., p.get_height()),
                ha='center', va='center', fontsize=10, color='black', xytext=(0, 5),
                textcoords='offset points')

plt.show() 


plt.figure(figsize=(8, 6))
ax = sns.countplot(x='Courier Status', data=df)
plt.xlabel('Courier Status')
plt.ylabel('Number of Orders')
plt.title('Distribution of Courier Status')
plt.xticks(rotation=45, ha='right')

# Add labels on top of bars
for p in ax.patches:
    ax.annotate(f'{p.get_height():.0f}', (p.get_x() + p.get_width() / 2., p.get_height()),
                ha='center', va='center', fontsize=10, color='black', xytext=(0, 5),
                textcoords='offset points')

plt.show()


"""# conclusion of all chart  ;


1)This line chart visually represents the trend of total sales over time. Here's what you can conclude from it:

Trend: The blue line represents the daily total sales. The chart shows how the sales fluctuate over the given time period. You can observe increases, decreases, and potentially any patterns or seasonality in the sales data.
Fluctuations: The ups and downs in the line indicate the variability of sales. Areas with steeper slopes suggest more rapid changes in sales.
Overall Pattern: You might be able to identify any overall trends in the sales. For instance, are sales generally increasing, decreasing, or remaining relatively stable over the time period?

2)The bar chart displays the quantity of products sold for each category.
Set1 and Kurti are the highest selling product categories.
Western Dress, Blouse, and Saree have lower sales compared to Set1 and Kurti.
Y-axis labels likely represent rank rather than exact quantity.
This visualization helps to understand sales performance across categories.

3)The pie chart shows the distribution of the top 5 product categories.
Set1 has the largest share, followed by Kurti.
Western Dress, Blouse, and Saree have smaller proportions.
Percentages on each slice represent the category's contribution to total sales.
This visualization helps to compare the relative popularity of product categories.

4)The bar chart displays the top 10 states with the most orders.
Maharashtra has the highest number of orders, followed by Karnataka and Uttar Pradesh.
Delhi, Telangana, and Tamil Nadu also have a substantial number of orders.
The remaining states in the top 10 have relatively fewer orders.
This visualization helps to identify the key geographic areas for sales.


5)M size has the highest sales quantity.
L and XL sizes also have significant sales.
S, XXL, and 3XL have lower sales quantities.
The chart visualizes size-wise sales distribution.
It helps understand customer preferences for sizes.

6)The line plot visualizes the relationship between the quantity of items sold and the total amount earned.
There is a general positive correlation: as quantity increases, the amount also tends to increase.
However, the relationship isn't perfectly linear, indicating other factors may influence the amount.
Some data points show higher amounts for the same quantity, possibly due to price variations or discounts.
This chart helps understand how sales quantity affects overall revenue.
"""
