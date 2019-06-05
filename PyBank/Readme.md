# PyBank
## Out Put

Financial Analysis

-----------------------------------------

Total Months: 86

Total: $38,382,578.00

Average Change: $-2,315.12

Greatest Increase in Profits: Feb-2012 $1170593.0

Greatest Decrease in Profits: Sep-2013 $-1196225.0


## Python Code
```Python
#Budget_Data
import csv  
import os   



budget_data = os.path.join("budget_data.csv")
with open(budget_data,newline="") as budge_data:
    read_budget = csv.reader(budge_data,delimiter = ",")
    
#Find the total month in the data set
    netTotal = 0
    count = 0 
    greatestInc = 0
    greatestDec = 0
    lastMon = 0
    change = 0
    changeTotal = 0
    next (read_budget,None)
    for row in read_budget:
        count += 1
        netTotal += float(row[1])
        if count > 1: 
            change = float(row[1]) - lastMon
        changeTotal += change
        lastMon = float(row[1])
        #find greatest increase and decrese
        if greatestInc < float(row[1]):
            greatestInc = float(row[1])
            greatestIncDate = row[0]
        
        if greatestDec > float(row[1]):
            greatestDec = float(row[1])
            greatestDecDate = row[0]



averageChange = float(changeTotal/(count-1))
print("Financial Analysis")
print("-----------------------------------------")
print(f"Total Months: {count}")
print(f"Total: ${netTotal:,.2f}")
print(f"Average Change: ${averageChange:,.2f}")
print(f"Greatest Increase in Profits: {greatestIncDate} ${greatestInc:,.2f}")
print(f"Greatest Decrease in Profits: {greatestDecDate} ${greatestDec:,.2f}")



with open("budgetSummary.txt","w") as budgeSum:
    budgeSum.write("Financial Analysis\n")
    budgeSum.write("-----------------------------------------\n")
    budgeSum.write(f"Total Months: {count}\n")
    budgeSum.write(f"Total: ${netTotal:,.2f}\n")
    budgeSum.write(f"Average Change: ${averageChange:,.2f}\n")
    budgeSum.write(f"Greatest Increase in Profits: {greatestIncDate} ${greatestInc}\n")
    budgeSum.write(f"Greatest Decrease in Profits: {greatestDecDate} ${greatestDec}\n")
```
