 import geopandas as gpd
import matplotlib.pyplot as plt

# Load the shapefile containing India's geographical data
# You can download a shapefile of India from various online resources like "https://www2.census.gov/geo/tiger/GENZ2021/"
# Make sure to replace 'india_shapefile.shp' with the correct path to the shapefile

shapefile_path = 'india_shapefile.shp'

# Read the shapefile using Geopandas
gdf = gpd.read_file(shapefile_path)

# Plot the map of India
gdf.plot(figsize=(10, 10), color='lightblue', edgecolor='black')

# Customize the plot (optional)
plt.title('Map of India', fontsize=15)
plt.xlabel('Longitude')
plt.ylabel('Latitude')

# Show the plot
plt.show()

