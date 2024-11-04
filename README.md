# Riley Green
# UWYO COSC 1010
# Submission Date : 11/04/24
# HW 03
# Lab Section: Thursday 6:10 - 8
# Sources, people worked with, help given to:
# your
# comments
# here
# Homework Question: write a program that given a date of the format MM/DD/YYYY, your program will then state the day of the week the day occurs on

def is_leap_year(year):
    return year % 4 == 0 and (year % 100 != 0 or year % 400 == 0)

def get_jan_first_day(year):
    y = year - 1
    day = (36 + y + (y // 4) - (y // 100) + (y // 400)) % 7
    return day

def is_valid_date(month, day, year):
    if year < 1 or month < 1 or month > 12 or day < 1:
        return False

    days_in_month = {
        1: 31, 2: 29 if is_leap_year(year) else 28, 
        3: 31, 4: 30, 5: 31, 6: 30, 
        7: 31, 8: 31, 9: 30, 10: 31, 
        11: 30, 12: 31
    }

    return day <= days_in_month[month]

def get_day_of_week(month, day, year):
    if not is_valid_date(month, day, year):
        return None

    jan_first_day = get_jan_first_day(year)
    
    days_in_month = {
        1: 31, 2: 28, 3: 31, 4: 30, 
        5: 31, 6: 30, 7: 31, 8: 31, 
        9: 30, 10: 31, 11: 30, 12: 31
    }

    if is_leap_year(year):
        days_in_month[2] = 29

    days_passed = sum(days_in_month[m] for m in range(1, month)) + (day - 1)
    
    day_of_week = (jan_first_day + days_passed) % 7
    return day_of_week

def main():
    days_of_week = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"]

    date_input = input("Enter a date (MM/DD/YYYY): ")
    
    try:
        month, day, year = map(int, date_input.split('/'))
    except ValueError:
        print(f"{date_input} Invalid Date")
        return
    
    day_of_week_index = get_day_of_week(month, day, year)

    if day_of_week_index is None:
        print(f"{date_input} Invalid Date")
    else:
        print(f"{date_input} {days_of_week[day_of_week_index]}")
