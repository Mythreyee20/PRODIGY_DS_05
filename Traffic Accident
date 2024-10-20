import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from mpl_toolkits.basemap import Basemap

url = 'https://raw.githubusercontent.com/your-dataset-link/traffic_accidents.csv'
traffic_data = pd.read_csv(url)

print(traffic_data.head())

print("\nMissing values in each column:")
print(traffic_data.isnull().sum())

traffic_data.dropna(subset=['Road_Condition', 'Weather_Condition', 'Time_of_Day'], inplace=True)

traffic_data['Time_of_Day'] = pd.to_datetime(traffic_data['Time_of_Day'], errors='coerce').dt.hour

plt.figure(figsize=(10, 5))
sns.countplot(data=traffic_data, x='Road_Condition')
plt.title('Accident Count by Road Condition')
plt.xlabel('Road Condition')
plt.ylabel('Number of Accidents')
plt.xticks(rotation=45)
plt.grid()
plt.show()

plt.figure(figsize=(10, 5))
sns.countplot(data=traffic_data, x='Weather_Condition')
plt.title('Accident Count by Weather Condition')
plt.xlabel('Weather Condition')
plt.ylabel('Number of Accidents')
plt.xticks(rotation=45)
plt.grid()
plt.show()

plt.figure(figsize=(10, 5))
sns.countplot(data=traffic_data, x='Time_of_Day')
plt.title('Accident Count by Hour of the Day')
plt.xlabel('Hour of Day')
plt.ylabel('Number of Accidents')
plt.xticks(rotation=45)
plt.grid()
plt.show()

plt.figure(figsize=(12, 8))
plt.title('Accident Hotspots')
map = Basemap(projection='merc', llcrnrlat=traffic_data['Latitude'].min(), urcrnrlat=traffic_data['Latitude'].max(),
              llcrnrlon=traffic_data['Longitude'].min(), urcrnrlon=traffic_data['Longitude'].max(), lat_ts=20, resolution='i')
map.drawcoastlines()
map.drawcountries()
map.drawmapboundary(fill_color='aqua')
map.fillcontinents(color='lightgray', lake_color='aqua')

x, y = map(traffic_data['Longitude'].values, traffic_data['Latitude'].values)
map.scatter(x, y, marker='o', color='red', s=10, alpha=0.5)

plt.show()


plt.figure(figsize=(10, 5))
sns.countplot(data=traffic_data, x='Contributing_Factor')
plt.title('Accident Count by Contributing Factors')
plt.xlabel('Contributing Factor')
plt.ylabel('Number of Accidents')
plt.xticks(rotation=45)
plt.grid()
plt.show()
