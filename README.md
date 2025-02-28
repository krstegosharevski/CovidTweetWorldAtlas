# World Analysis of Covid-19 Tweets

This document outlines the methodology used to analyze and visualize the geographical distribution of Covid-19 tweets. The goal is to gain insights into the global and regional prevalence of long COVID by leveraging geospatial techniques. The analysis follows a structured workflow, including data import, cleaning, location extraction, geocoding, geospatial processing, and visualization.

## Step 1: Data Import and Cleaning
The dataset, initially stored in a CSV file, was loaded into a pandas DataFrame. To maintain data integrity, rows containing missing tweet information were removed, ensuring a clean and reliable dataset for further analysis.

## Step 2: Tweet Processing
To standardize and refine the tweet content, a text-cleaning function was applied to the 'Tweets' column. This function:

Converted all text to lowercase.
Removed URLs and usernames (denoted by the '@' symbol).
Eliminated non-alphanumeric characters.
Filtered out common English stopwords (e.g., "the", "is", "in") to retain only meaningful information.
These preprocessing steps helped ensure that only relevant textual data remained for analysis.

## Step 3: Location Extraction
To identify geographical references within tweets, Named Entity Recognition (NER) from the SpaCy library was utilized. The model specifically searched for geopolitical entities (GPE), such as city and country names. The extracted locations were stored in a new column labeled 'Locations' for further processing.

## Step 4: Geocoding
Once location names were extracted, they were converted into geographic coordinates (latitude and longitude) using the Nominatim geocoder from the geopy library. The obtained coordinates were stored as shapely Point objects in a new column named 'Geometry'.

## Step 5: Geospatial Analysis
With geographic coordinates available, the dataset was transformed into a GeoDataFrame, a specialized format from the geopandas library designed for spatial data processing. This allowed for various geospatial analyses, including proximity calculations and clustering.

## Step 6: Data Visualization
To visualize the geographical distribution of tweets, the data was plotted on a global map using geopandas. Each tweet’s location appeared as an individual point, offering a clear representation of how discussions about long COVID were distributed across different regions.

## Step 7: Cluster Analysis
To identify high-density areas of tweet activity, the DBSCAN (Density-Based Spatial Clustering of Applications with Noise) algorithm was applied. This clustering technique grouped closely located tweets while marking isolated tweets as outliers. The resulting clusters were color-coded and plotted on the map, highlighting hotspots of online discussion about long COVID.

By following this structured approach, we successfully conducted a comprehensive geospatial analysis of Covid tweets. The results provide a visual understanding of the prevalence and distribution of discussions related to long COVID-19, offering valuable insights into regional trends and public discourse on the topic.