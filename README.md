# Ecommerce Order Data Analysis Dashboard

This project generates synthetic ecommerce transaction data and provides a Streamlit-based interactive dashboard to visualize the data. The dashboard allows users to explore daily profit/loss, identify popular products, and filter the data by various fields. Additionally, there's a basic fraud detection feature to identify potential fraudulent orders.

## Table of Contents

1. [Project Overview](#project-overview)
2. [Requirements](#requirements)
3. [Data Generation](#data-generation)
4. [Streamlit Dashboard](#streamlit-dashboard)
5. [Running the Application](#running-the-application)
6. [Fraud Detection](#fraud-detection)
7. [License](#license)

## Project Overview

This project consists of two main parts:

1. *Synthetic Data Generation*: A Python script that generates at least 100,000 rows of synthetic ecommerce order data. This data includes fields like order_id, customer_name, total_price, total_discount, product_name, coupon_code, etc.
   
2. *Streamlit Dashboard*: A web-based interactive dashboard to explore and visualize the generated data. It includes features like:
   - Uploading a CSV to inspect the data.
   - Visualizing daily profit and loss.
   - Identifying the most popular products.
   - Filtering orders by product name.
   - A simple fraud detection dashboard to flag suspicious transactions.

## Requirements

- Python 3.x
- Required Python packages:
  - Faker
  - pandas
  - matplotlib
  - seaborn
  - streamlit

You can install the required packages using the following command:

bash
pip install -r requirements.txt


### requirements.txt

txt
Faker==18.6.0
pandas==1.5.3
matplotlib==3.8.0
seaborn==0.12.2
streamlit==1.15.0


## Data Generation

The generate_data.py script generates synthetic ecommerce data and saves it into a CSV file. The following fields are included in the generated data:

- order_id: Unique identifier for the order.
- customer_name: Random name generated using the Faker library.
- order_date: Random order date within the current year.
- total_price: Random total price between $10 and $500.
- total_discount: Discount applied to the order (0% to 25% of the total price).
- total_after_discount: The total price after applying the discount.
- product_category: Randomly chosen from a set of categories (e.g., Electronics, Clothing, Home, etc.).
- product_name: Random product name chosen from the selected category.
- coupon_code: A coupon code applied to the order (randomly assigned with 30% probability).
- cost_price: The cost of the product, randomly assigned and lower than the total price.

### Example Usage of generate_data.py:

To generate 100,000 rows of synthetic data and save it to synthetic_orders.csv:

bash
python generate_data.py


## Streamlit Dashboard

The streamlit_dashboard.py file is the core of the interactive dashboard, which provides the following features:

### Key Features:
1. *File Upload*: Users can upload a CSV file to inspect and visualize its data.
2. *Daily Profit / Loss*: A bar chart showing daily profit or loss, calculated from the difference between total_after_discount and cost_price.
3. *Most Popular Products*: A bar chart showing the top 10 most popular products by order frequency.
4. *Order Filtering*: A dropdown allows users to filter orders by product_name and view the corresponding data.
5. *Fraud Detection*: A basic fraud detection heuristic identifies potential fraudulent orders based on the discount and cost price of the product.

## Running the Application

To run the Streamlit app:

1. First, ensure that you have generated the data (synthetic_orders.csv) using the generate_data.py script or have your own CSV file ready.
2. Install the required dependencies using the requirements.txt.
3. Launch the Streamlit app with the following command:

bash
streamlit run streamlit_dashboard.py


This will open a local server where you can interact with the dashboard.

## Fraud Detection

The fraud detection feature uses a basic heuristic to flag potential fraudulent orders:

- *Potential Fraud Criteria*:
  - Orders where the total_discount is more than 50% of the total_price and the cost_price is greater than the total_after_discount. These could be signs of suspicious activity, such as fraudulent coupon usage or manipulated pricing.

This heuristic is simple and can be extended with more sophisticated fraud detection algorithms, such as:
- Checking for multiple orders from the same user in a short time.
- Detecting unusually high numbers of high-value orders.
- Comparing geographic location for order mismatches.

## License
This project is open source and available under the MIT License
