# PyPoll
## Out Put
Election Results

-------------------------------

Total Votes : 3521001

-------------------------------

Khan : 63.00% :2218231

Correy : 20.00% :704200

Li : 14.00% :492940

O'Tooley : 3.00% :105630

-------------------------------

Winner :Khan

-------------------------------

## Python code

```python
import csv 
import os 
import collections 


csvPath = os.path.join("election_data.csv")
with open(csvPath,newline = "") as election_data:
    readData = csv.reader(election_data)
    count = 0
    next(election_data, None)
    Candidates=[]
    lsCand = []
    
    for row in readData:      
        count += 1       
        #Gathers a list of candidates
        lsCand.append(row[2])
        cand = row[2]
        #creates a unique list of candidates
        if cand not in Candidates:
            Candidates.append(cand)
#counts the occurances of each candidate (which tallies the votes)
countVotes = collections.Counter(lsCand)




#prints candidates votes and percents to both terminal and txt file
with open("SummPoll.txt","w") as summPoll:
    #to Terminal
    print("Election Results")
    print("-------------------------------")
    print(f"Total Votes : {count}")
    print("-------------------------------")
    #to TXT
    summPoll.write("Election Results\n")
    summPoll.write("-------------------------------\n")
    summPoll.write(f"Total Votes : {count}\n")
    summPoll.write("-------------------------------\n")

    for cand,numVotes in countVotes.items():
        perc = (float(numVotes/count*100))
        print(f"{cand} : {perc:,.02f}% : {numVotes}")
        summPoll.write(f"{cand} : {perc:,.02f}% :{numVotes}\n")
    print("-------------------------------")
    summPoll.write("-------------------------------\n")

    #find the winner of the election and outputs it
    num = 0
    for cand, numVotes in countVotes.items():
        if float(numVotes) > float(num):
            winner = cand
            num = numVotes
    print(f"Winner : {winner}")
    summPoll.write(f"Winner :{winner}\n")
    summPoll.write("-------------------------------\n")
    print("-------------------------------")
```
