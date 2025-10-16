# 🏡 Buenos Aires Housing Analysis

This project explores real estate pricing trends in Buenos Aires, Argentina, with a focus on apartments listed under $400,000 USD. Through data wrangling, exploratory analysis, and visualization, we uncover patterns in pricing, surface area, and neighborhood distribution. The project culminates in an interactive MVP that allows users to explore apartment listings dynamically.

---

## 📌 Project Objectives

- Clean and consolidate multiple real estate datasets
- Focus analysis on affordable apartments in Capital Federal
- Identify pricing trends and spatial patterns
- Build an interactive MVP for real-time exploration

---

## 🧠 Step-by-Step Process

### 1. **Data Collection**
Five CSV files containing apartment listings were sourced and stored in the `data/` directory. Each file includes details such as price, location, surface area, and property type.

### 2. **Data Wrangling**
Using a custom `wrangle()` function, we:
- Filtered listings to include only apartments in *Capital Federal* priced below $400,000 USD
- Removed outliers in surface area using the 10th and 90th percentiles
- Extracted latitude and longitude from the `lat-lon` column
- Parsed neighborhood names from hierarchical location strings
- Dropped irrelevant columns to streamline the dataset

The cleaned dataset was saved in `data/processed/buenos-aires-real-estate-splitted-dataset.csv`.

## 📊 Exploratory Data Analysis (EDA)

To uncover pricing dynamics in Buenos Aires' apartment market, I conducted a series of visual and statistical analyses using Python. This section outlines the key steps and insights, with full code and plots available in the notebook.

---

### 1. **Price Distribution**

I began by visualizing the distribution of apartment prices under $400,000 USD. This helped identify the most common price ranges and detect skewness in the data.

📌 **Insight**:  
Most listings fall between **$50,000 and $150,000**, with a peak around **$100,000**. The distribution is right-skewed, indicating fewer high-priced listings.

---

### 2. **Price vs. Area**

Next, I explored the relationship between apartment size and price. This visual helped assess whether larger apartments command higher prices.

📌 **Insight**:  
There’s a clear upward trend—larger apartments tend to be more expensive. However, there's significant variability, suggesting other factors (like location) also influence price.

---

### 3. **Geospatial Price Mapping**

Using an interactive map, I plotted apartment locations and colored them by price. This revealed spatial pricing patterns across the city.

📌 **Insight**:  
High-priced apartments cluster in premium neighborhoods like **Puerto Madero**, **Palermo**, and **Belgrano**, while lower-priced listings are more dispersed in southern and peripheral areas.

---

### 4. **Neighborhood-Level Price Comparison**

To quantify pricing differences across neighborhoods, I calculated the average price per neighborhood and visualized it using a bar chart.

📌 **Insight**:  
- **Puerto Madero** leads with the highest average price, exceeding **$250,000**  
- **Palermo** and **Belgrano** follow closely  
- **Villa Lugano** and **Villa Riachuelo** rank lowest, averaging below **$50,000**


## 🤖 Model Building

To estimate apartment prices based on key features, I built a regression model using scikit-learn. The goal was to predict the price of a property using its surface area, geographic coordinates, and neighborhood.

---

### 🔧 Features Used
- `surface_covered_in_m2`: Total covered area of the apartment
- `lat` and `lon`: Latitude and longitude coordinates
- `neighborhood`: Categorical location label

---

### 🧪 Baseline Model

I began with a simple baseline model that predicted the mean apartment price for all listings. This gave a baseline Mean Absolute Error (MAE) of **~44,860 USD**, which served as a benchmark for improvement.

---

### 🛠️ Ridge Regression Pipeline

To improve performance, I built a pipeline that included:
- One-hot encoding for categorical features
- Imputation for missing values
- Ridge regression for prediction

After training the model on the full dataset, the MAE dropped significantly to **~24,207 USD**, indicating a strong improvement over the baseline.

---

### 📦 Test Predictions

I applied the trained model to a separate test dataset and generated price predictions for unseen listings. The predictions aligned well with expected market values and demonstrated the model’s generalization capability.

---

This modeling step adds predictive power to the project and sets the stage for future enhancements, such as hyperparameter tuning, cross-validation, or deploying the model in a real-time pricing tool.


---

## 📈 Prediction Function

To make the model usable for real-time predictions, I developed a custom function called `make_prediction`. This function accepts user-defined inputs for:

- Surface area (`area`)
- Latitude (`lat`)
- Longitude (`lon`)
- Neighborhood (`neighborhood`)

It processes these inputs into a format compatible with the trained Ridge Regression model and returns a price estimate rounded to two decimal places. This function is the backbone of the interactive experience and demonstrates how machine learning can be applied to real-world decision-making.

📌 **Example Output**:  
> Predicted apartment price: **$250,775.11** for a 110 m² apartment in Villa Crespo  
> Predicted apartment price: **$111,914.76** for a 53 m² apartment in central Buenos Aires

---

## 🧪 Interactive MVP

To showcase the model in action, I built an interactive MVP using `ipywidgets` directly inside the Jupyter Notebook. This interface allows users to:

- Adjust sliders for surface area, latitude, and longitude
- Select a neighborhood from a dropdown menu
- Instantly view the predicted apartment price based on their inputs

📌 **Features**:
- Real-time predictions using the trained model
- Intuitive sliders and dropdowns for user input
- Seamless integration with the notebook environment

This MVP transforms the notebook into a dynamic pricing tool, making it accessible for buyers, sellers, and analysts exploring the Buenos Aires housing market.

## 🧰 Technologies Used

This project was built entirely in Python using the following tools and libraries:

- **Jupyter Notebook**: Interactive environment for data exploration and modeling
- **Pandas**: Data manipulation and cleaning
- **Matplotlib & Plotly**: Data visualization (static and interactive)
- **Scikit-learn**: Machine learning model building and evaluation
- **Ipywidgets**: Interactive UI elements for real-time predictions
- **Glob2**: File handling across multiple datasets

These tools enabled efficient data wrangling, insightful visualizations, and a responsive MVP—all within a notebook-based workflow.



