# Indus-River-Sindh-6-Canals-Analysis-
In this project we can analyse the Sindh 6 Canals Data 
import pandas as pd

# Canal Data for Major Canals from Sindh River
canal_data = {
    "Canal Name": [
        "Sutlej Valley Canal",
        "Bari Doab Canal",
        "Nara Canal",
        "Dadu Canal",
        "Khairpur Canal",
        "Sakkar Canal"
    ],
    "Location (District, Province, Coordinates)": [
        "District 1, Sindh, (24.8607° N, 67.0011° E)",
        "District 2, Sindh, (25.276987° N, 55.296249° E)",
        "District 3, Sindh, (23.6345° N, 81.2550° E)",
        "District 4, Sindh, (24.4539° N, 68.7980° E)",
        "District 5, Sindh, (24.1234° N, 67.5678° E)",
        "District 6, Sindh, (23.9876° N, 69.2345° E)"
    ],
    "Size (Width, Depth, Length)": [
        "15m, 4m, 50km",
        "12m, 3.5m, 45km",
        "18m, 5m, 60km",
        "10m, 3m, 40km",
        "14m, 4.5m, 55km", 999
        "16m, 4m, 65km"
    ],
    "Water Flow (Discharge in cubic feet per second)": [
        5000,
        4500,
        6000,
        4000,
        4800,
        5500
    ],
    "Construction Start Date": [
        "01-Jan-2000",
        "15-Mar-2001",
        "22-May-2002",
        "10-Jul-2003",
        "18-Aug-2004",
        "05-Nov-2005"
    ],
    "Construction End Date": [
        "31-Dec-2005",
        "30-Nov-2006",
        "15-Oct-2007",
        "28-Feb-2008",
        "12-Jan-2009",
        "22-Dec-2010"
    ],
    "Construction Duration (Time Taken for Construction)": [
        "5 years",
        "5 years 8 months",
        "5 years 5 months",
        "4 years 7 months",
        "4 years 5 months",
        "5 years 1 month"
    ],
    "Operational Status (Active/Inactive)": [
        "Active",
        "Inactive",
        "Active",
        "Active",
        "Inactive",
        "Active"
    ],
    "Maintenance History (Dates and Details of Any Major Repairs)": [
        "30-Sep-2010: Pipeline replacement",
        "02-Jan-2015: Channel reinforcement",
        "15-Mar-2017: Concrete lining repair",
        "20-Apr-2019: Valve maintenance",
        "05-Jun-2020: Levee repair",
        "10-Feb-2022: Sediment removal"
    ]
}

# Create DataFrame
canal_df = pd.DataFrame(canal_data)

# Display the DataFrame
print("Canal DataFrame: \n", canal_df)

# Data Analysis
# 1. Analyzing the operational status
status_count = canal_df['Operational Status (Active/Inactive)'].value_counts()
print("\nOperational Status Counts: \n", status_count)

# 2. Analyzing Construction Duration
# Convert construction duration to months for better analysis
def convert_duration_to_months(duration):
    if 'year' in duration:
        years = int(duration.split(' ')[0])
        months = years * 12
        if 'month' in duration:
            months += int(duration.split(' ')[2])
        return months
    return 0

canal_df['Construction Duration (Months)'] = canal_df['Construction Duration (Time Taken for Construction)'].apply(convert_duration_to_months)

# 3. Analyzing the Water Flow
avg_water_flow = canal_df['Water Flow (Discharge in cubic feet per second)'].mean()
print("\nAverage Water Flow: ", avg_water_flow)

# 4. Analyzing the construction duration
avg_construction_duration = canal_df['Construction Duration (Months)'].mean()
print("\nAverage Construction Duration (in months): ", avg_construction_duration)
