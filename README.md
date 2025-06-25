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


## plot link 🔗 
##![Total Sales Over Date]((https://github.com/user-attachments/assets/dc8117d6-bc97-4682-971d-64df9c268841)



#  2) Plot -Top 10 Categories by Number of Orders

## Plot code - 
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

![Top 10 Categories by Number of Orders](https://github.com/user-attachments/assets/d17496d7-a24d-4fdc-b14c-bdab3f7b0519)

