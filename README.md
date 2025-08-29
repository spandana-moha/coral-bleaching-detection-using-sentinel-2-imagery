# Coral Bleaching Detection using Satellite (Sentinel-2) Imagery

This project is an end-to-end pipeline that leverages Google Earth Engine (GEE) to detect and map potential coral bleaching events using Sentinel-2 satellite imagery. The objective is to provide a scalable and cost-effective method for monitoring coral reefs and identifying areas at risk of bleaching.

---

## Environment Setup
The pipeline uses the earthengine-api, geemap, shapely, and scikit-learn libraries. It authenticates with the Google Earth Engine API to connect to the backend.

---

## Study Area
The project focuses on a specific area near Lizard Island in the Great Barrier Reef, Australia. The timeframe for the imagery is set from February to June 2020, coinciding with the region's warm season.

---

## Data Preprocessing
- **Data Filtering** - Images are filtered by a low cloud cover percentage (less than 20%).
- **Cloud Masking** - A custom cloud mask is applied using the QA60 bitmask band to remove clouds and cirrus pixels.
- **Median Composite** - A median composite is created from the cleaned image collection to reduce noise.
- **Band Selection** - The analysis uses the Blue (B2), Green (B3), Red (B4), and Near-Infrared (B8) bands.

--- 

## Feature Engineering
New spectral features are engineered to distinguish between healthy coral, bleached coral, and other substrates. These features include:
- Visible Brightness
- Blue/Green Ratio
- Red/Green Ratio
- NDWI-like Index

---

## Unsupervised Learning
- **K-Means Clustering** - The engineered features are used as input for an unsupervised K-Means clustering model. The model classifies pixels into distinct clusters.
- **Cluster Analysis** - The clusters are analyzed and visualized to identify those corresponding to "bleached-like," "healthy," and "other" categories.

--

## Results and Visualization
The final clusters are visualized on a map of the study area to provide a clear, pixel-based map of potential coral bleaching.

--- 

## Technologies and Tools
- **Google Earth Engine (GEE)**: Cloud-based platform for planetary-scale geospatial analysis.
- **Sentinel-2**: Satellite imagery for Earth observation.
- **Python Libraries**: earthengine-api, geemap, shapely, scikit-learn, numpy, matplotlib.

---

## Results
The K-Means clustering model successfully classified pixels in the study area, with the following rough pixel counts for each cluster: [689284, 72137, 730221]. These clusters were then visualized on a map to show the spatial distribution of potential bleaching events.

---

## Future Work
- **Supervised Learning**: Implement a supervised machine learning model (e.g., Random Forest or Support Vector Machine) to improve classification accuracy using a pre-labeled dataset of healthy and bleached coral.
- **Time-Series Analysis**: Extend the project to perform a time-series analysis to monitor the progression of coral bleaching events over multiple years.
- **Web Application**: Deploy the model as a web application to allow users to select a study area and date range for on-the-fly analysis.
