
### 📈 1) Plot - Total Sales Over Date 

![Total Sales Over Date]((https://github.com/user-attachments/assets/dc8117d6-bc97-4682-971d-64df9c268841)

# Plot banao - Total Sales Over D
plt.figure(figsize=(12, 4.5))  # Width aur height adjust kiya gaya hai
plt.plot(df['Date'], df['Total_Sales'], color='green', linewidth=2)
plt.title('Total Sales Over Time', fontsize=14)
plt.xlabel('Date')
plt.ylabel('Total Sales')
plt.grid(True)
plt.tight_layout()
plt.show()
