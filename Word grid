import tkinter as tk
import random
from tkinter import messagebox
from tkinter import*
from tkinter import PhotoImage
import pygame

root1 = tk.Tk()
root1.geometry("750x550")
root1.title("Welcome")
def word_grid_game():
    global root
    pygame.init()
    root=tk.Tk()
    root1.destroy()    
    root.title("Word Grid")
    def convert_to_grid(words_list):
        grid_size = int(len(words_list) ** 0.5)
    

        word_grid = [[None for _ in range(grid_size)] for _ in range(grid_size)]

        for i in range(grid_size):
            for j in range(grid_size):
                word_grid[i][j] = words_list[i * grid_size + j]

        return word_grid

    def on_cell_click(event, row, col):
        if not selected_cells or is_adjacent(row, col, selected_cells[-1]):
            selected_cells.append((row, col))
            cell = entry_grid[row][col]
            cell.config(bg='lightblue')

    def is_adjacent(row, col, prev_cell):
        return abs(row - prev_cell[0]) <= 5 and abs(col - prev_cell[1]) <= 5
    global selected_cells,score
    score=0
    def check_combined_word():
        global score
        combined_word = (''.join(word_grid[row][col] for row, col in selected_cells))
        if combined_word in words1_list:
             message_label.config(text=f"The word '{combined_word}' exists!",font=("Minion Pro",14))
             score+=1
             score_label.config(text=f"score:{score}",font=("Minion Pro",14))
        else:
             message_label.config(text=f"The word '{combined_word}' does not exist!",font=("Minion Pro",14))


    def reset_selection():
        global selected_cells
        for row, col in selected_cells:
            cell = entry_grid[row][col]
            cell.config(bg='Medium Purple')
        selected_cells=[]
        score=0
        score_label.config(text="")
        
    
# Example 2-letter words list

    words1_list =['boat','coat','tall','ball','july','crow' , 'five' , 'gain' , 'exit' , 'hide' , 'rice' , 'lace' , 'race' ]

    words_list=[]
    for i in words1_list:
        if len(i)%2==0:
            div_word1,div_word2=i[:len(i)//2] ,i[len(i)//2:]
            words_list.append(div_word1)
            words_list.append(div_word2)
        else:
            print("wrong input")
    print(random.shuffle(words_list))

# Convert words list to grid
    word_grid = convert_to_grid(words_list)

    

# Create a 2D list to hold the Entry widgets
    entry_grid = [[None for _ in range(len(word_grid[0]))] for _ in range(len(word_grid))]

# Populate the grid with Entry widgets and letters from the word grid
    for i in range(len(word_grid)):
        for j in range(len(word_grid[i])):
            entry = tk.Label(root, text=word_grid[i][j], padx= 30, pady=30, relief=tk.RAISED,font=("Minion Pro",20),borderwidth=15,bg="Medium Purple")
            entry.grid(row=i, column=j)
            entry.bind('<Button-1>', lambda event, row=i, col=j: on_cell_click(event, row, col))
            entry_grid[i][j] = entry

    selected_cells = []
    score=0

# Buttons
    check_button = tk.Button(root, text="Check Combined Word", command=check_combined_word,borderwidth=6,font=("Minion Pro",10),bg="White")
    check_button.grid(row=len(word_grid), columnspan=len(word_grid[0]))

    reset_button = tk.Button(root, text="Reset Selection", command=reset_selection,borderwidth=6,font=("Minion Pro",10),bg="White")
    reset_button.grid(row=len(word_grid) + 1, columnspan=len(word_grid[0]))
    def confirm_exit():
        
            root.destroy()
    
    exit_button =tk.Button(root, text="Exit", command=confirm_exit,borderwidth=6)
    exit_button.grid(row=len(word_grid)+2,columnspan=len(word_grid[0]))



 # Label to display the result
    
    message_label = tk.Label(root, text="")
    message_label.grid(row=0, column=80)
    score=0
    score_label=tk.Label(root,text=f" score :{score}",font=("Minion Pro",14))
    score_label.grid(row=1,column=80)
def sound_play():
        sound=pygame.mixer.Sound('music.mp3')
        sound.play()

photo=PhotoImage(file='image.png')
label1=Label(root1,image=photo)
label1.pack()

label2=tk.Label(root1,text="Welcome to the Word Grid Game!!",font=("ShowCard Gothic",30) )   
label2.place(x=350,y=300)
button1=tk.Button(root1,text="START",bg="white",font=("ShowCard Gothic",20),command=lambda:[word_grid_game(),sound_play()],borderwidth=8)
button1.place(x=600,y=500)

# Run the Tkinter main loop
root1.mainloop()
