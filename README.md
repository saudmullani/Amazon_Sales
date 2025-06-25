 📈 PLOTS
#  1) Plot - Total Sales Over Date 


## Plot code - 
plt.figure(figsize=(12, 4.5))

df['Date'] = pd.to_datetime(df['Date'])  


df['Year'] = df['Date'].dt.year


df['Month'] = df['Date'].dt.month


df['Day'] = df['Date'].dt.day    






sns.lineplot(x='Date', y='total sales', data=df)


plt.xlabel('Date')


plt.ylabel('total sales')


plt.title(' total sales over date')


plt.xticks(rotation=45, ha='right')


plt.show()


![Total sales over date](https://github.com/user-attachments/assets/6c77ed9a-0b14-4f98-9e83-dee19fac01c6)


## plot link 🔗 ((https://github.com/user-attachments/assets/dc8117d6-bc97-4682-971d-64df9c268841)



#   2) Plot - Top 10 Categories by Number of Orders

## Plot code - 


top_10_categories = df['Category'].value_counts().head(10)

plt.figure(figsize=(12, 5))


ax = sns.barplot(x=top_10_categories.index, y=top_10_categories.values)


plt.xlabel('Category')


plt.ylabel('Number of Orders')


plt.title('Top 10 Categories by Number of Orders')


plt.xticks(rotation=45, ha='right')



for p in ax.patches:
    ax.annotate(f'{p.get_height():.0f}', (p.get_x() + p.get_width() / 2., p.get_height()),
                ha='center', va='center', fontsize=10, color='black', xytext=(0, 5),
                textcoords='offset points')
                

plt.show()

![Top 10 Categories by Number of Orders](https://github.com/user-attachments/assets/d17496d7-a24d-4fdc-b14c-bdab3f7b0519)

## plot link 🔗 (https://github.com/user-attachments/assets/d17496d7-a24d-4fdc-b14c-bdab3f7b0519)



# 3) Plot - Pie Chart of Top 5 Category Distribution

## Plot code - 

category_counts = df['Category'].value_counts().head(5)    -   #Get top 5 categories


plt.figure(figsize=(6.3, 8))


explode = [0,0,0,0,0] * len(category_counts)



##-   Create the pie chart without explode


wedges, texts, autotexts = plt.pie(category_counts,
                                  autopct='%1.1f%%', 
                                  startangle=90,
                                  textprops={'fontsize': 13, 'color': 'black'},
                                  pctdistance=1.1) 

                                  



plt.legend(wedges, category_counts.index,
          title="Categories",
          loc="center left",
          bbox_to_anchor=(1, 0, 0.5, 1))        -   #Adjusted bbox_to_anchor
          

plt.title('Pie Chart of Top 5 Category Distribution', fontsize=14)      -   #Updated title


plt.tight_layout()  -  #Adjust layout to prevent labels from being cut off


plt.show()

![Pie Chart of Top 5 Category Distribution](https://github.com/user-attachments/assets/08f64692-b33c-4106-97ec-d6dd5f18bd50)

## plot link 🔗(https://github.com/user-attachments/assets/08f64692-b33c-4106-97ec-d6dd5f18bd50)



# 4) Plot - Top 10 Ship States

## Plot code - 

import matplotlib.pyplot as plt


import seaborn as sns


top_10_states = df['ship-state'].value_counts().head(10)



plt.figure(figsize=(14, 6))


ax = sns.barplot(x=top_10_states.values, y=top_10_states.index) - #Switch x and y back


plt.xlabel('Number of Orders') - #Switch labels back
plt.ylabel('Ship State')


plt.title('Top 10 Ship States')

plt.xticks(rotation=0, ha='center')       -  #Adjust x-tick rotation (optional)



plt.yticks(rotation=0, ha='right')          -   #Adjust y-tick rotation


##- Add quantity labels on top of bars 

for p in ax.patches:
    ax.annotate(f'{p.get_width():.0f}', (p.get_width(), p.get_y() + p.get_height() / 2.),
                ha='left', va='center', fontsize=10, color='black', xytext=(5, 0),
                textcoords='offset points')

plt.show()


![Top 10 Ship States](https://github.com/user-attachments/assets/b9144b82-00f1-4bee-b0d1-15abe1b38ecf)


## plot link 🔗(https://github.com/user-attachments/assets/bd7a394d-aca8-454b-8e05-f8ae7cb8a5af)



# 5) plot - Quantity by Size

## Plot code - 


qty_by_size = df.groupby('Size')['Qty'].sum().reset_index()

plt.figure(figsize=(11, 6))


ax = sns.barplot(x='Size', y='Qty', data=qty_by_size)  - #Use barplot for vertical bars

plt.xlabel('Size')


plt.ylabel('Total Quantity')


plt.title('Quantity by Size')

plt.xticks(rotation=45, ha='right')


##- Add labels on top of bars



for p in ax.patches:
    ax.annotate(f'{p.get_height():.0f}', (p.get_x() + p.get_width() / 2., p.get_height()),
                ha='center', va='center', fontsize=10, color='black', xytext=(0, 5),
                textcoords='offset points')

plt.show()


![Quantity by Size )](https://github.com/user-attachments/assets/152a7206-09cd-484b-ae89-ab2214824d19)


## plot link 🔗 (https://github.com/user-attachments/assets/152a7206-09cd-484b-ae89-ab2214824d19)

# 6) plot - Distribution of Courier Status

## Plot code - 


plt.figure(figsize=(8, 6))


ax = sns.countplot(x='Courier Status', data=df)


plt.xlabel('Courier Status')


plt.ylabel('Number of Orders')


plt.title('Distribution of Courier Status')


plt.xticks(rotation=45, ha='right')

##-Add labels on top of bars
for p in ax.patches:
    ax.annotate(f'{p.get_height():.0f}', (p.get_x() + p.get_width() / 2., p.get_height()),
                ha='center', va='center', fontsize=10, color='black', xytext=(0, 5),
                textcoords='offset points')

plt.show()

![Distribution of Courier Status](https://github.com/user-attachments/assets/91f41be0-6aeb-40eb-af95-f3e86e1160f0)


## plot link 🔗 (https://github.com/user-attachments/assets/91f41be0-6aeb-40eb-af95-f3e86e1160f0)
