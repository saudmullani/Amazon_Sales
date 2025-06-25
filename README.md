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


## plot link 🔗 
![Total Sales Over Date]((https://github.com/user-attachments/assets/dc8117d6-bc97-4682-971d-64df9c268841)
