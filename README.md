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
