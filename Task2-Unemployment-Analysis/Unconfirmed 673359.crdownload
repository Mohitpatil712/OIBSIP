import pandas as pd
import matplotlib.pyplot as plt

#  Load Dataset
df = pd.read_csv("Unemployment in India.csv")

print(df.head())
print(df.info())

# Clean Column Names
df.columns = df.columns.str.strip()
df.columns = df.columns.str.lower()
df.columns = df.columns.str.replace(" ", "_")
df.columns = df.columns.str.replace("(", "")
df.columns = df.columns.str.replace(")", "")

print(df.columns)

# Data Cleaning
df['date'] = pd.to_datetime(df['date'], dayfirst=True)
df = df.dropna()

# Unemployment Trend Over Time
trend = df.groupby('date')['estimated_unemployment_rate_%'].mean()

plt.plot(trend.index, trend.values)
plt.title("Unemployment Rate Trend in India")
plt.xlabel("Date")
plt.ylabel("Unemployment Rate (%)")
plt.show()

# COVID impact
plt.plot(trend.index, trend.values)
plt.axvline(pd.to_datetime("2020-03-01"), linestyle='--')
plt.title("COVID-19 Impact on Unemployment")
plt.xlabel("Date")
plt.ylabel("Unemployment Rate (%)")
plt.show()

# State-wise Analysis
state_avg = df.groupby('region')['estimated_unemployment_rate_%'].mean()

state_avg.plot(kind='bar')
plt.title("State-wise Unemployment Rate")
plt.xlabel("State")
plt.ylabel("Unemployment Rate (%)")
plt.xticks(rotation=90)
plt.show()

# Urban vs Rural Analysis
area_avg = df.groupby('area')['estimated_unemployment_rate_%'].mean()

area_avg.plot(kind='bar')
plt.title("Urban vs Rural Unemployment")
plt.xlabel("Area")
plt.ylabel("Unemployment Rate (%)")
plt.show()

# Correlation Analysis
numeric_data = df[
    ['estimated_unemployment_rate_%',
     'estimated_employed',
     'estimated_labour_participation_rate_%']
]

print(numeric_data.corr())