# Customers-Performance-Analysis-and-Visualization-of-an-Automobile-Company-Sales-Data
A Data Science Project that Analysed  the sales performance of an Automobile company Based in the United States. The company’s sales transaction data generated over the past years was used for this  analysis

#### PROBLEM STATEMENT:

Who are their Top 10 Most-Profitable Customers  in the United State ?

## DATA PRE-PROCESSING 
#### DATA LOADING 

```Python
##  importing all the necessary python packages


# solution 
import numpy as np 
import pandas as pd 
import matplotlib.pyplot as plt

print("The packages have been successfully imported")
```

```Python
# reading the sales data into a pandas dataframe

bikes_df = pd.read_csv("C:/Users/Mazeliz Depot1/Desktop/NGOZI/_Mr Emma class/Data Set/bikes.csv")
bikes_df.head()    
```
![Loading and Reading](https://github.com/user-attachments/assets/9b13daf4-4332-40d4-ba30-e0c78943c37b)


####  Data Modification
```Python
# (1). Adding the following 3 columns to your pansdas Dataframe:  bikes_df

# TotalCostPrice : To be obtained by (OrderQuantity x CostPrice_usd)

bikes_df["TotalCostPrice"] = bikes_df["OrderQuantity"] * bikes_df["CostPrice_usd"] 

# SalesRevenue : To be obtained by (OrderQuantity x SellingPrice_usd)

bikes_df["SalesRevenue"] = bikes_df["OrderQuantity"] * bikes_df["SellingPrice_usd"] 

# Profit : To be obtained by (SalesRevenue - TotalCostPrice)

bikes_df["Profit"] = bikes_df["SalesRevenue"] - bikes_df["TotalCostPrice"]

bikes_df.head()
```
![Data Modification](https://github.com/user-attachments/assets/234d7552-c875-4b97-bb9b-18ca691bc460)


## DATA ANALYSIS
#### DATA FILTERING
```Python
Is_Country_Name = bikes_df["CustomerCountry"] == "United States"
bikes_df[Is_Country_Name].head(15)
```
![Data Filtering](https://github.com/user-attachments/assets/2ceb5a7c-cf55-4613-b476-5fe779f1c0c7)

#### Data Aggregates / Data Summary
```Python
# Data Aggregates / Data Summary
bikes_df[Is_Country_Name].pivot_table(values = "Profit", index = "CustomerName", aggfunc = np.sum)
Profitable_Customers = bikes_df[Is_Country_Name].pivot_table(values = "Profit", index = "CustomerName", aggfunc = np.sum)
Profitable_Customers
```
![Data Aggregate](https://github.com/user-attachments/assets/dd5dcc9c-2ecd-41ed-a49c-693308e2ebfe)

## Data sorting
```Python
# step 4: Data sorting 
# solution
Profitable_Customers.sort_values("Profit", ascending = False)
Top_10_profitable_customer = Profitable_Customers.sort_values("Profit", ascending = False)
Top_10_profitable_customer.head(15)
```
![Data Sorting](https://github.com/user-attachments/assets/0196012e-d7ef-4bee-80c7-3db99545329f)

## Result 
```Python
top_10_customers = Profitable_Customers.sort_values("Profit", ascending = False).head(10)
top_10_customers
```
![Result](https://github.com/user-attachments/assets/11f2a4f3-6f08-46b7-b3df-d95c6e61de7a)

## DATA VISUALIZATION
```Python
## VISUALIZATING THE RESULT 

top_10_customers.plot(kind = "bar")


# Adding a Title and Label
plt.title("The Top 10 Customers in The United State")

plt.ylabel("Total Profit")
plt.xlabel("Customers Name" )


#Showing the Result
plt.show()
```
![Visualization](https://github.com/user-attachments/assets/2a15e044-75e8-4269-b668-5eb762d7faf4)
