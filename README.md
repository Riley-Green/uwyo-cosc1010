# Riley Green
# UWYO COSC 1010
# Submission Date : 10/28/24
# HW 02
# Lab Section: Thursday 6:10 - 8
# Sources, people worked with, help given to:
# your
# comments
# here
# Homework Question: Write a program that can translate between plain text and Morse code to ultimately print the message "Go Pokes"



def main():
    morse_code_dict = {
        'A': '.-', 'B': '-...', 'C': '-.-.', 'D': '-..', 'E': '.', 
        'F': '..-.', 'G': '--.', 'H': '....', 'I': '..', 'J': '.---', 
        'K': '-.-', 'L': '.-..', 'M': '--', 'N': '-.', 'O': '---', 
        'P': '.--.', 'Q': '--.-', 'R': '.-.', 'S': '...', 'T': '-', 
        'U': '..-', 'V': '...-', 'W': '.--', 'X': '-..-', 'Y': '-.--', 
        'Z': '--..'
    }

    input_string = "Go Pokes"

    morse_code_output = ""

    for char in input_string:
        if char.isalpha():
            morse_code_output += morse_code_dict[char.upper()] + " "
        elif char == " ":
            morse_code_output += "  "

    print(morse_code_output.strip())

#Result = --. ---  .--. --- -.- . ...





