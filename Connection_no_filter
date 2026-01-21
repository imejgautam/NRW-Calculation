import pandas as pd

# Step 1: Load both Excel files
ledger_df = pd.read_excel("D:/KUKL Internship/NRW of 7.1/Shrawan/Ledger Data.xlsx")
meter_df = pd.read_excel("D:/KUKL Internship/NRW of 7.1/Shrawan/Meter Reading List.xlsx")

# Step 2: Standardize 'Con No' columns for matching
ledger_df['Con No'] = ledger_df['Con No'].astype(str).str.strip()
meter_df['Con No'] = meter_df.iloc[:, 1].astype(str).str.strip()  # Assuming column 1 is 'Con No'

# Step 3: Create composite key (which is just 'Con No' here)
ledger_df['Key'] = ledger_df['Con No']
meter_df['Key'] = meter_df['Con No']

# Step 4: Find matching entries based only on 'Con No'
common_keys = set(ledger_df['Key']) & set(meter_df['Key'])

# Step 5: Filter both dataframes
filtered_ledger = ledger_df[ledger_df['Key'].isin(common_keys)].drop(columns=['Key'])
filtered_meter = meter_df[meter_df['Key'].isin(common_keys)].drop(columns=['Key'])

# Step 6: Save results
filtered_ledger.to_excel("D:/KUKL Internship/NRW of 7.1/Shrawan/filtered_ledger_Con.xlsx", index=False)
filtered_meter.to_excel("D:/KUKL Internship/NRW of 7.1/Shrawan/filtered_meter_reading_Con.xlsx", index=False)

print("Both files have been filtered using only 'Con No' for matching.")