# data-cleaning-python
import pandas as pd

df = pd.read_csv("data.csv")

# remove duplicates
df = df.drop_duplicates()

# fill missing values
df = df.fillna(method='ffill')

# save cleaned data
df.to_csv("cleaned_data.csv", index=False)
