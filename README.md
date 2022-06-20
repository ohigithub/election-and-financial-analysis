# python-challenge

PYBANK

import pandas as pd

#open/view CSV file

csv_path = "/Users/daniellesears/Downloads/election_data.csv"

df = pd.read_csv(csv_path)
df.head()

#calculate the total # of votes cast
total_votes = df["Ballot ID"].count()

#create a complete list of candidates who received votes
specific_candidates_list = df["Candidate"].unique()

#calculate the percentage of votes each candidate won and list the total number of votes each candidate won

vote_1 = 0
vote_2 = 0
vote_3 = 0



for candidate in df["Candidate"]:
    if candidate == "Charles Casper Stockham":
        vote_1 += 1
    
    elif candidate == "Diana DeGette":
        vote_2 += 1
        
    elif candidate == "Raymon Anthony Doane":
        vote_3 += 1
        
#print("(vote_1)")("{:,1f}%".format)
print(vote_1/total_votes)
print(vote_2/total_votes)
print(vote_3/total_votes)
#calculate the winner

most_votes = max(vote_1, vote_2, vote_3)

if most_votes == vote_2:
    most_votes == "Diana DeGette"


print("Election Results")

#How do I get the line seperating the title of this analysis from the analysis itself?
print("Total Votes:", total_votes)
print("Winner:", most_votes)






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
