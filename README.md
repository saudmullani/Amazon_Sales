plt.figure(figsize=(12, 4.5))  # Changed width from 12 to 20
df['Date'] = pd.to_datetime(df['Date'])  # Convert to datetime if needed
df['Year'] = df['Date'].dt.year
df['Month'] = df['Date'].dt.month
df['Day'] = df['Date'].dt.day

(https://github.com/user-attachments/assets/dc8117d6-bc97-4682-971d-64df9c268841)
