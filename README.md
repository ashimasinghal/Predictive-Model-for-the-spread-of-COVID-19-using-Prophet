# Predictive-Model-for-the-spread-of-COVID-19-using-Prophet

## Predictive Modeling
Predictive Modeling is a powerful way of adding artificial intelligence in the most subtle way into your application. over the past many years, there has been a huge advancement in this area. Today we depend on predictive modeling in evry area from finance to warehouse storing.
Time series forecasting is basically the machine learning modeling for Time Series data (years, days, hours…etc.) for predicting future values using Time Series modeling . This helps if your data in serially correlated.
There are many ways to analyse the trend and predict the outcome.
### 1. ARIMA
 It stands for AutoRegressive Integrated Moving Average. It is an integration of AR and MA model. 
 ### 2. Prophet
 Prophet is a procedure for forecasting time series data based on an additive model where non-linear trends are fit with yearly, weekly, and daily seasonality, plus holiday effects. It works best with time series that have strong seasonal effects and several seasons of historical data. Prophet is robust to missing data and shifts in the trend, and typically handles outliers well.

### Installation
```
pip intall plotply
```
```
pip install fbprophet
```

### The Code
 In this code, we'll be working with Prophet. The code itself is pretty straight forward. The dataset used here is from kaggle.
 
 ### read the csv file into the ipython notebook
 using pandas, read th dataset as pandas dataframes.
 
 ```
 df1 = pd.read_csv('train.csv')
 ```
 
### visualize the data to understand the attributes better
I have used plotply in the code but you can go ahead and explore a little bti more bit PowerBI and Tableau, etc.

![newplot (4)](https://user-images.githubusercontent.com/57868216/87540870-f92fcf00-c6bd-11ea-9aed-6f9fc0e573d3.png)
![newplot (7)](https://user-images.githubusercontent.com/57868216/87542538-b7545800-c6c0-11ea-8035-3400de2a74db.png)
![newplot (6)](https://user-images.githubusercontent.com/57868216/87542540-b7ecee80-c6c0-11ea-983e-2b987e4618fd.png)
![newplot (5)](https://user-images.githubusercontent.com/57868216/87542544-b91e1b80-c6c0-11ea-8563-eab69af4ec77.png)

### using Prophet
we needd to columns in the training dataset minimum. 
1. time-series to compute on
2. y values to predict
```
train_dataset_confirmed['ds'] = pd.to_datetime(dataframe.index)
train_dataset_confirmed['y']  = y
```
now we are ready to fit our data for training
```
prophet_basic = Prophet()
prophet_basic.fit(train_dataset_confirmed)
```
now, decide on the periods fro future forecasting
```
future = prophet_basic.make_future_dataframe(periods = 500)
```
And finally, predict and analyze!!
```
pro_change = Prophet(changepoint_range=0.9)
forecast = pro_change.fit(train_dataset_confirmed).predict(future)
fig= pro_change.plot(forecast);
a = add_changepoints_to_plot(fig.gca(), pro_change, forecast)
```
## Future scope
1. using public APIs to feed in the data live streaming
2. Wrapping the model into a flask application and deploying it on the cloud with real-time analysis

