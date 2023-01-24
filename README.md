# Challenge3_PayBank

import os
import csv
from pathlib import Path 


csvpath = Path('/Users/majosegarciamontes/Desktop/budget_data.csv')


TotalMonths = []
TotalProft = []
MonthlyProfit = []
 

with open(csvpath) as csvfile:
    csvreader = csv.reader(csvfile,delimiter=",") 
    header = next(csvreader)   

    
    for row in csvreader: 

        
        TotalMonths.append(row[0])
        TotalProft.append(int(row[1]))

    
    for i in range(len(TotalProft)-1):
        
        
        MonthlyProfit.append(TotalProft[i+1]-TotalProft[i])
        

MaxDecrease = min(MonthlyProfit)
MaxIncrease = max(MonthlyProfit)



max_decrease_month = MonthlyProfit.index(min(MonthlyProfit)) + 1 
max_increase_month = MonthlyProfit.index(max(MonthlyProfit)) + 1



print("Financial Analysis")
print("--------------------------------------------------")
print(f"Total Months: {len(TotalMonths)}")
print("")
print(f"Total: $ {sum(TotalProft)}")
print("")
print(f"Average Change: {round(sum(MonthlyProfit)/len(MonthlyProfit),2)}")
print("")
print(f"Greatest Increase in Profits: {TotalMonths[max_increase_month]} ($ {(str(MaxIncrease))})")
print("")
print(f"Greatest Decrease in Profits: {TotalMonths[max_decrease_month]} ($ {(str(MaxDecrease))})")


analysis_file = Path('/Users/majosegarciamontes/Desktop/Challenge3/paybank/PayBank_Majo.txt')

with open(analysis_file,"w") as file:
    

    file.write("Financial Analysis")
    file.write("\n")
    file.write("--------------------------------------------------")
    file.write("\n")
    file.write(f"Total Months: {len(TotalMonths)}")
    file.write("\n")
    file.write(f"Total: ${sum(TotalProft)}")
    file.write("\n")
    file.write(f"Average Change: {round(sum(MonthlyProfit)/len(MonthlyProfit),2)}")
    file.write("\n")
    file.write(f"Greatest Increase in Profits: {TotalMonths[max_increase_month]} (${(str(MaxIncrease))})")
    file.write("\n")
    file.write(f"Greatest Decrease in Profits: {TotalMonths[max_decrease_month]} (${(str(MaxDecrease))})")
