# python-homework

Financial Analysis
----------------------------
Total Months: 86
Total: $38382578
Average  Change: $-2315.12
Greatest Increase in Profits: Feb-2012 ($1926159)
Greatest Decrease in Profits: Sep-2013 ($-2196167)
In addition, your final script should both print the analysis to the terminal and export a text file with the results.



import os
import csv


budget_data_csv = os.path.join("C:\\Users\\buchh\\Desktop\\Python-homework\\budget_data.csv")


text_path = "output.txt"


total_months = 0
total_revenue = 0
revenue = []
previous_revenue = 0
month_of_change = []
revenue_change = 0
greatest_decrease = ["", 9999999]
greatest_increase = ["", 0]
revenue_change_list = []
revenue_average = 0



with open('budget_data.csv') as csvfile:  
    csvreader = csv.DictReader(csvfile)

    
    for row in csvreader:

        
        total_months += 1

        
        total_revenue = total_revenue + int(row["Profit/Losses"])

      
        revenue_change = float(row["Profit/Losses"])- previous_revenue
        previous_revenue = float(row["Profit/Losses"])
        revenue_change_list = revenue_change_list + [revenue_change]
        month_of_change = [month_of_change] + [row["Date"]]
       

       
        if revenue_change>greatest_increase[1]:
            greatest_increase[1]= revenue_change
            greatest_increase[0] = row['Date']

        
        if revenue_change<greatest_decrease[1]:
            greatest_decrease[1]= revenue_change
            greatest_decrease[0] = row['Date']
    revenue_average = sum(revenue_change_list)/len(revenue_change_list)
