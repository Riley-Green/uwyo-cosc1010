# Riley Green
# UWYO COSC 1010
# Submission Date : 11/11/24
# HW 04
# Lab Section: Thursday 6:10 - 8
# Sources, people worked with, help given to:
# your
# comments
# here
# Homework Question: write a program that given a date of the format MM/DD/YYYY, your program will then state the day of the week the day occurs on


from pathlib import Path 

input_path = Path("./prompt.txt")
output_path = Path("./out.txt")

contents = input_path.read_text()
lines = contents.splitlanes()

output_content = ""
for line in lines:
    parts = line.split()
    for part in parts:
        left, right = part.split(":")
        right = int(right)

        if left == 'w':
            output_content += ' ' * right
        elif left == '*': 
            output_content += '*' * right

    output_content += "\n"

output_content.write_text(output_content)
