---
# Goal of the Model
The goal of this model is to predict the financial damage caused by earthquakes based on various geological and disaster-related factors. By merging earthquake data with disaster records, the model identifies key features such as magnitude, depth, location, and human impact (deaths and affected individuals) to understand their relationship with economic losses. Using Principal Component Analysis (PCA), the model reduces dimensionality while preserving essential patterns, ensuring a more efficient and interpretable dataset. A Random Forest Regressor is then trained to estimate total damage costs, with performance evaluated through metrics like RMSE, R² score, and MAE. This predictive approach aims to support disaster preparedness, risk assessment, and resource allocation by providing insights into the financial impact of earthquakes based on historical data.

---
# Dataset information
Theres two datasets used  one sourced from Kaggle which coombines two datasets as they have the same columns but just have years seperated so the two datasets could easily be combined in to one csv file. The other data set was sourced from the public EM-DAT platform that lets a user use an api call to download disaster damage reports for multiple types of natural disasters.

---
# Data Sources

***Earthquake Dataset Link:*** https://www.kaggle.com/datasets/warcoder/earthquake-dataset

***Disaster Dataset Link:*** https://public.emdat.be/data

---

# Column Definitions
**Dataset Name:**  earthquake_data.csv

* **Columns in the Kaggle Earthquake Dataset:**
  * **title:** title name given to the earthquake
  * **magnitude:** The magnitude of the earthquake
  * **date_time:** date and time
  * **cdi:** The maximum reported intensity for the event range
  * **mmi:** The maximum estimated instrumental intensity for the event
  * **alert:** The alert level - “green”, “yellow”, “orange”, and “red”
  * **tsunami:** "1" for events in oceanic regions and "0" otherwise
  * sig: A number describing how significant the event is. Larger numbers   indicate a more significant event. This value is determined on a number of factors, including: magnitude, maximum MMI, felt reports, and estimated impact
  * **net:** The ID of a data contributor. Identifies the network considered to be the preferred source of information for this event.
  * nst: The total number of seismic stations used to determine earthquake location.
  * **dmin:** Horizontal distance from the epicenter to the nearest station
  * gap: The largest azimuthal gap between azimuthally adjacent stations (in degrees). In general, the smaller this number, the more reliable is the calculated horizontal position of the earthquake. Earthquake locations in which the azimuthal gap exceeds 180 degrees typically have large location and depth uncertainties
  * **magType:** The method or algorithm used to calculate the preferred magnitude for the event
  * **depth:** The depth where the earthquake begins to rupture
  * **latitude / longitude:** coordinate system by means of which the position or location of any place on Earth's surface can be determined and described
  * **location:** location within the country
  * **continent:** continent of the earthquake hit country
  * **country:** affected country
---
* **Columns in the EM-DAT Natural Disaster Dataset:**

**Dataset Name:** public_emdat_custom_request_2025-03-21_e861b1e0-df2d-4878-8dfd-5e504fe9cd63.xlsx
  * **DisNo.:** Unique disaster identification number.  
  * **Historic:** Indicates whether the event is historical.  
  * **Classification Key:** Internal classification reference for the disaster.  
  * **Disaster Group:** Broad category of disaster (e.g., **Natural, Technological**).  
  * **Disaster Subgroup:** More specific classification within the disaster group (e.g., **Geophysical, Hydrological**).  
  * **Disaster Type:** The main type of disaster (e.g., **Earthquake, Flood, Cyclone**).  
  * **Disaster Subtype:** A more detailed category within the disaster type (e.g., **Tsunami, Landslide**).  
  * **External IDs:** Additional external reference identifiers.  
  * **Event Name:** The name of the specific disaster event (if available).  
  * **ISO:** The ISO country code where the disaster occurred.  
  * **Country:** The full name of the country affected.  
  * **Subregion:** The subregion within the affected country (e.g., **South Asia, Eastern Africa**).  
  * **Region:** The broader geographical region (e.g., **Asia, Africa, Europe**).  
  * **Location:** The specific location or city where the disaster occurred.  
  * **Origin:** The originating cause of the disaster (if applicable).  
  * **Associated Types:** Other disaster types linked to the main event (e.g., **Earthquake triggering a Tsunami**).  
  * **OFDA/BHA Response:** Indicates if the **USAID Office of Foreign Disaster Assistance (OFDA)/Bureau for Humanitarian Assistance (BHA)** responded.  
  * **Appeal:** Indicates whether an international appeal was launched for aid.  
  * **Declaration:** Whether an official disaster declaration was made.  
  * **AID Contribution ('000 US$):** The amount of aid provided (in thousands of US dollars).  

  * **Magnitude:** The magnitude of the disaster (e.g., **earthquake magnitude, cyclone wind speed**).  
  * **Magnitude Scale:** The unit used to measure magnitude (e.g., **Richter Scale, Saffir-Simpson Scale**).  
  * **Latitude:** The latitude coordinate of the disaster location.  
  * **Longitude:** The longitude coordinate of the disaster location.  
  * **River Basin:** The river basin affected (if applicable).  
  * **Start Year:** The year the disaster started.  
  * **Start Month:** The month the disaster started.  
  * **Start Day:** The day the disaster started.  
  * **End Year:** The year the disaster ended.  
  * **End Month:** The month the disaster ended.  
  * **End Day:** The day the disaster ended.  
  * **Total Deaths:** The total number of people who died due to the disaster.  
  * **No. Injured:** The number of people injured.  
  * **No. Affected:** The total number of people affected (includes displaced individuals).  
  * **No. Homeless:** The number of people left homeless due to the disaster.  
  * **Total Affected:** The sum of all affected individuals, including injured, displaced, and impacted communities.  
  * **Reconstruction Costs ('000 US$):** The estimated reconstruction costs (in thousands of US dollars).  

  * **Reconstruction Costs, Adjusted ('000 US$):** The adjusted reconstruction costs based on inflation and other factors.  

  * **Insured Damage ('000 US$):** The total insured losses (in thousands of US dollars).  

  * **Insured Damage, Adjusted ('000 US$):** Adjusted insured damage value considering inflation.  

  * **Total Damage ('000 US$):** The total estimated economic damage (in thousands of US dollars).  

  * **Total Damage, Adjusted ('000 US$):** The adjusted total damage cost considering inflation.  

  * **CPI:** The Consumer Price Index (used for damage cost adjustments).  

  * **Admin Units:** The affected administrative divisions (e.g., **state, province**).  

  * **Entry Date:** The date the disaster data was first recorded in the database.  
  * **Last Update:** The most recent update to the disaster record.  

---
# Plan
The datasets contain a large number of columns, so the first step is to clean the data and merge only the relevant information needed to train the model for predicting earthquake damages.

**Data Cleaning:** Removing null values from critical columns and ensuring numerical data is correctly formatted.

**Filtering Earthquake Data:** Extracting only earthquake-related entries from the natural disaster dataset.

**Merging Datasets:** Combining the earthquake dataset with the disaster report data based on shared attributes such as magnitude, longitude, latitude, and country.

**Feature Engineering:** Creating additional features (such as the interaction between magnitude and depth) to improve model performance.

**Training the Model:** Applying Principal Component Analysis (PCA) for dimensionality reduction and training a Random Forest model using an 80/20 train-test split.

**Evaluation:** Assessing the model’s performance using RMSE, R² score, and MAE, as well as analyzing residuals to understand prediction errors.

This approach ensures that the model is trained on high-quality, relevant data, optimizing its ability to predict earthquake damages accurately.


This approach was decided on after many attempts and research into different ways of producing a model which can be found here : https://colab.research.google.com/drive/1kU_q6uv8_kZrmT7yFKb4r1ZNDsPaLvEN?usp=sharing

---

## Author
**Conor Dawson**  
BSc (Hons) in Software Development 
