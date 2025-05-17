# Airbnb Property Clustering - Project Overview

## Problem
- Airbnb users often struggle to choose properties that match their preferences due to the large number of available options.
- Misalignment between property searches and user preferences can reduce satisfaction and trust in the service.
- A system is needed to group properties based on similar characteristics to simplify the search for properties that match user needs.

## Research Questions
- How can Airbnb properties be grouped based on characteristics such as price, location, amenities, and property type?
- Can clustering algorithms be used to identify relevant market segments within the Airbnb property data?

## Objectives
- To identify property segments based on relevant characteristics.
- To optimize pricing and marketing strategies by grouping properties into more relevant clusters.

---

## Data Analysis (Exploratory Data Analysis)
1. **Property Price Distribution**: Property prices tend to have a right-skewed distribution, indicating that the majority of properties are affordable.

![Property Price Distribution](https://github.com/mufti19/AirBnB-Recomendation-System-Final-Project-/blob/main/Data%20Exploration/Property%20Price%20Distribution.png)<br>
2. **Property Types**: The *Entire home/apt* room type is more common compared to other types like *Private room* and *Shared room*.

![Number of Properties by Room Type](https://github.com/mufti19/AirBnB-Recomendation-System-Final-Project-/blob/main/Data%20Exploration/Number%20of%20Properties%20by%20Room%20Type.png)<br>
3. **Price vs Property Rating**: Many high-priced properties have good ratings, but there are also low-priced properties that receive high ratings.

![Price vs Property Rating](https://github.com/mufti19/AirBnB-Recomendation-System-Final-Project-/blob/main/Data%20Exploration/Price%20vs%20Property%20Rating.png)<br>

---

## Data Processing
- **Handling Missing Values**: 
  - Variables with more than 10% missing values are removed.
  - Missing values in other variables are filled with *mean* (for numeric data) or *mode* (for categorical data).
- **Handling Outliers**: 
  - The IQR method is used to detect and handle outliers in columns such as *beds*, *bathrooms*, and *bedrooms*.
- **Feature Engineering**: 
  - Categorical variables are encoded to prepare data for machine learning models, such as *host_is_superhost*, *is_location_exact*, and *Instant_bookable*.

---

## ML Modeling
- **Algorithms Applied**:
  - K-Means Clustering
  - Agglomerative Clustering
  - Self-Organizing Map (SOM)
  - DBSCAN
- **Selection of Optimal Cluster Count**:
  - K-Means and Agglomerative used 5 clusters based on the Elbow method.
  - SOM generated 3 clusters based on the Dunn Index.
  - DBSCAN used standard parameters with *eps* = 0.3 and *min_samples* = 5.

---

## Model Evaluation
- **Model Evaluation with Clustering Metrics**:
  - **Davies-Bouldin Index**: Measures the proximity between clusters, the lower this value, the better.
  - **Silhouette Score**: Measures the quality of cluster separation.
  - **Calinski-Harabasz Index**: Measures how compact and separated the clusters are.

- **Evaluation Results**:

| Model           | Davies-Bouldin Index | Silhouette Score | Calinski-Harabasz Index |
|-----------------|----------------------|------------------|-------------------------|
| KMeans          | 0.804                | 0.492            | 4.756.113               |
| Agglomerative   | 0.807                | 0.478            | 4.348.488               |
| DBSCAN          | 0.658                | 0.187            | 152.192                 |
| SOM             | 0.927                | 0.409            | 3.648.951               |

  - **K-Means**: The evaluation metrics show the best performance with high scores in the Davies-Bouldin Index and Silhouette Score.
  - **DBSCAN**: Performs poorly in Silhouette Score but can detect some outliers effectively.
  - **SOM**: Although adequate, there is some overlap between clusters.

Based on the evaluation results, **K-Means** is the most effective model for clustering this data, producing clearly defined and compact clusters. The low Davies-Bouldin Index and high Silhouette Score indicate that K-Means provides optimal results in separating and grouping properties according to their characteristics.

---

## Cluster Profiling

#### Cluster Segmentation:
- **Cluster 1 (Budget Single)**:
  - **Description**: Affordable accommodation for 1-2 people with a price of $113/night. This cluster offers full privacy with the entire unit available, such as *Entire Home/Apt*.
  - **Target Market**: Solo travelers or couples who prioritize affordability and privacy.
  
- **Cluster 2 (Spacious Family Home)**:
  - **Description**: A spacious property for large families (6 people) with a price of $200/night. It has 3 bedrooms suitable for groups or families needing more space.
  - **Target Market**: Families or groups looking for more spacious and comfortable accommodation at an affordable price.
  
- **Cluster 3 (Luxury Group Stay)**:
  - **Description**: Similar to Cluster 2 but with a higher price ($202/night) and more amenities for larger groups, including additional comfort.
  - **Target Market**: Large groups or families seeking a more luxurious experience with additional facilities.
  
- **Cluster 4 (Economy Shared Room)**:
  - **Description**: Budget accommodation with a price of $70/night for a *Shared Room*. Ideal for those who prioritize cost savings but still need some privacy.
  - **Target Market**: Budget-conscious travelers who don't need much private space and prefer shared facilities.
  
- **Cluster 5 (Mid-Range Private Room)**:
  - **Description**: Option priced at $134/night for 4 people in a *Private Room*. It offers a good balance of price and comfort.
  - **Target Market**: Individuals or couples seeking privacy and comfort at a mid-range price.

---

## Business Recommendations Per Cluster (Marketing, Sales, & Promotion):

- **Cluster 1 (Budget Single)**:
  - **Target Market**: Solo travelers, young couples, backpackers.
  - **Strategic Marketing**:
    - Focus marketing on platforms like TikTok and Instagram with the theme: “#Affordable. #Comfortable, #BudgetFriendly”.
    - Collaborate with micro-influencers who talk about budget travel and solo trips.
  - **Promotions**:
    - “Stay 3 nights, get 1 free” for solo guests.
    - 10-15% discount for first-time users.
    - Add high-speed WiFi for digital nomads.

- **Cluster 2 (Spacious Family Home)**:
  - **Target Market**: Large families, local tourists with children, family reunions.
  - **Strategic Marketing**:
    - Highlight family comfort & togetherness with campaigns: “#FamilyComfortInEveryCorner”.
    - Show walkthrough videos of homes (YouTube, Facebook Ads).
  - **Promotions**:
    - Free breakfast or airport pickup for families of 4 or more.
    - Bundle deals for stays of 5 nights or more.
    - “Family Vacation Package” during school holidays or Lebaran.

- **Cluster 3 (Luxury Group Stay)**:
  - **Target Market**: Executive groups, premium tourists, large families, corporate outings with high budgets.
  - **Strategic Marketing**:
    - Use platforms like Airbnb Luxe.
    - Premium influencer strategy with high-end travel or lifestyle YouTubers.
    - Luxury visual campaign: “Luxury Experience Together”.
  - **Promotions**:
    - Exclusive offers like checkout or butler service for stays of 3+ nights.
    - Private tour packages or rooftop BBQ as a bonus.
    - Upselling: offer spa experiences, transportation, or private chefs.

- **Cluster 4 (Economy Shared Room)**:
  - **Target Market**: Backpackers, solo travelers, students, freelancers.
  - **Strategic Marketing**:
    - Position as “New Friends, New Experiences”.
  - **Promotions**:
    - “Stay more, pay less” weekly discount.
    - Free welcome drink or breakfast.
    - “Referral Guest” bonus – discounts for bringing friends.

- **Cluster 5 (Mid-Range Private Room)**:
  - **Target Market**: Small groups, vacationing couples, remote workers.
  - **Strategic Marketing**:
    - Campaign: “Privacy, Expensive? Don’t Worry”.
    - Promote on LinkedIn to attract remote workers (Work from Bali).
    - Focus on platforms like Airbnb with mid-range filter.
  - **Promotions**:
    - 15% discount for bookings of 7 nights or more.
    - Include coworking day pass or free laundry.
    - Highlight guest reviews about comfort & privacy.

---

# Team Behind This Project
* As the final project to finish the learning path for Data Science in [Rakamin_Academy](https://rakamin.com/), this model was built by a growth team called **Hi5**.

**The Team Member**<br> 
- **Salsabila N.Y** - Mentor  
- **Mufti Habibie A** - Data Scientist  
- **Johannes** - Data Analyst  
- **Syahdilla Fitri U** - Project Manager  
- **Ismawardani** - Data Engineer
