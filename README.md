# data-cleaning-python
import pandas as pd

def load_data(filepath):
    df = pd.read_csv(filepath)
    return df

def clean_data(df):
    # Standardize column names
    df.columns = df.columns.str.lower().str.replace(" ", "_")

    # Remove duplicates
    df = df.drop_duplicates()

    # Handle missing values
    df = df.dropna()

    # Convert date column
    if 'date' in df.columns:
        df['date'] = pd.to_datetime(df['date'])
        df['hour'] = df['date'].dt.hour
        df['day_of_week'] = df['date'].dt.day_name()

    return df

def save_clean_data(df, output_path):
    df.to_csv(output_path, index=False)
    print(f"[INFO] Cleaned data saved to {output_path}")
    
