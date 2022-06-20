# python-challenge


PYPOLL

import pandas as pd

#Calculate the total number of months included in this dataset
Months = df["Date"].count()

#Calculate the changes in "Profit/Losses" over the entire period, and then the average of those changes

Previous_Value = df.loc[0, "Profit/Losses"]
Net_Change = []

for x, y in df.iterrows():
    
    Difference = (y["Profit/Losses"])-Previous_Value
    Net_Change.append(Difference)
    Previous_Value = (y["Profit/Losses"])
       
df["Change"] = Net_Change
df

#Calculate the greatest increase in profits
GreatestIncrease = df["Change"].max()
Gi_Date = df[df["Change"] == GreatestIncrease]["Date"].values[0]

# #Calculate the greatest decrease in profits
GreatestDecrease = df["Change"].min()
Gd_Date = df[df["Change"] == GreatestDecrease]["Date"].values[0]

#Calculate average change
#average_change = round(df["Profit/Losses"][1:].mean(), 2)

total_changes = df["Profit/Losses"].sum()
average_change = total_changes / (Months - 1)
average_change = round(average_change, 2)

#Print the financial analysis

print ("Financial Analysis")

print("Total Months:", Months)
print ("Total:", total_sum)
print("Average Change:", average_change)
print(f"Greatest Increase in Profits: {Gi_Date}  ({GreatestIncrease})")
print(f"Greatest Decrease in Profits: {Gd_Date} ({GreatestDecrease})")
