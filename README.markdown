# Payday Planner

## Overview
Payday Planner is a simple web app that helps you manage your monthly bills by calculating the total amount needed in your checking account until your next payday (assumed to be the 1st or 15th of each month). Upload a CSV file with your bills, and the app will display the next payday, the total amount required for bills due before then, and a detailed list of those bills.

## Features
- **CSV Upload**: Upload a CSV file containing your bills with columns for title, description, amount, and due date (day of the month).
- **Payday Calculation**: Automatically determines the next payday (1st or 15th) based on the current date.
- **Bill Filtering**: Shows only the bills due between now and the next payday, excluding bills due today or on the payday itself.
- **Clean Interface**: Displays the total amount needed and a list of relevant bills with titles, descriptions, and amounts.

## Sample CSV Format
Your CSV file should have the following columns: `title`, `description`, `amount`, `day`. Here's an example (`sample_budget.csv`):

```
title,description,amount,day
Rent,Monthly apartment rent,1500,1
Home Insurance,Homeowners insurance,120,5
Car Insurance,Auto insurance premium,100,15
Phone Bill,Cell phone service,80,10
Internet Bill,Home internet service,60,12
Electricity Bill,Electric utility,150,20
Water Bill,Water and sewer utility,50,25
Cable TV,Cable television subscription,90,8
Credit Card Payment,Minimum credit card payment,200,28
Student Loan,Monthly student loan payment,300,3
Gym Membership,Gym membership fee,40,7
Streaming Services,Netflix and other subscriptions,30,18
```

## How to Use
1. Save the app's HTML code as `payday_planner.html`.
2. Open it in a web browser.
3. Upload your CSV file (or use the sample provided above).
4. View the next payday, total amount needed, and a list of bills due before the next payday.

## Notes
- The app assumes bills due on or after today are considered for the next due date but excludes today's bills (assuming they've been paid).
- Bills due on the exact payday date are excluded, assuming your paycheck arrives before any debits.
- The app does not handle local file I/O beyond CSV upload or network calls, keeping it lightweight and browser-based.
- For precise handling of edge cases (e.g., February 30th or month-end overflows), contact the developer for enhancements.

## Developer
Created with ❤️ by Grok, powered by xAI.