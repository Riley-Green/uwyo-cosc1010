# Riley Green
# UWYO COSC 1010
# Submission Date : 11/19/24
# HW 05
# Lab Section: Thursday 6:10 - 8
# Sources, people worked with, help given to: Internet and book
# your
# comments
# here
# Homework Question: create pixel art using python and spreadsheets 


import openpyxl
from openpyxl.styles import PatternFill

wb = openpyxl.Workbook()
sheet = wb.active

for col in sheet.columns:
    sheet.column_dimensions[col[0].column_letter].width = 3  
for row in sheet.rows:
    sheet.row_dimensions[row[0].row].height = 18 

color_dict = {
    'light_green': 'FF99CC00',  # Body
    'dark_green': 'FF006400',   # Leaves
    'blue': 'FF0000FF',         # Pupils
    'white': 'FFFFFFFF',        # Eyes
    'black': 'FF000000',        # Outline
    'pink': 'FFFFC0CB',         # Flower
    'brown': 'FF8B4513',        # Flower Stem
}

pixel_art = {
    # Body and Leaves
    (1, i): 'light_green' for i in range(1, 13),
    (2, i): 'light_green' for i in range(1, 13),
    (3, i): 'light_green' for i in range(1, 13),
    (4, i): 'pink' for i in range(3, 11),
    (5, i): 'pink' for i in range(3, 11),
    # Eyes and Face
    (5, 5): 'blue', (5, 6): 'blue', (5, 7): 'blue', (5, 8): 'blue', (5, 9): 'blue',
    (6, 5): 'white', (6, 6): 'white', (6, 7): 'white', (6, 8): 'white', (6, 9): 'white',
    (7, 5): 'black', (7, 6): 'black', (7, 7): 'black', (7, 8): 'black', (7, 9): 'black',
    # Flower 
    (4, i): 'pink' for i in range(3, 11),
    (5, i): 'pink' for i in range(3, 11),
    # Body details
    (8, i): 'brown' for i in range(5, 10),
    (9, i): 'brown' for i in range(5, 10),
    # Body and Limbs
    (10, i): 'light_green' for i in range(5, 9),
    (11, i): 'light_green' for i in range(5, 9),
}

for (row, col), color in pixel_art.items():
    fill = PatternFill(start_color=color_dict[color], end_color=color_dict[color], fill_type="solid")
    sheet.cell(row=row, column=col).fill = fill  


wb.save("venusaur_pixel_art.xlsx")
print("Pixel art of Venusaur created and saved as 'venusaur_pixel_art.xlsx'")

