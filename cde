import tkinter as tk
import ast

root = tk.Tk()
root.title("Calculator")
# Writing a function to get button clicked and add it to entry widget
i = 0

# This function gets the number to be added and adds it to input
def get_number(num):
    global i
    # Insert the num at index i
    display.insert(i, num)
    # Increment the index
    i += 1

def get_operation(operator):
    global i
    length = len(operator)
    display.insert(i, operator)
    i += length

def clear_all():
    display.delete(0, tk.END)

def calculate():
    entire_string = display.get()
    try:
        # Parse and evaluate the expression safely
        node = ast.parse(entire_string, mode="eval")
        result = eval(compile(node, '<string>', 'eval')
        clear_all()
        display.insert(0, result)
    except Exception:
        clear_all()
        display.insert(0, "Error")

def undo():
    entire_string = display.get()
    if len(entire_string):
        new_string = entire_string[:-1]
        clear_all()
        display.insert(0, new_string)
    else:
        clear_all()
        display.insert(0, "")

# Let's first add an input field, which will be the Entry widget
display = tk.Entry(root)
display.grid(row=1, columnspan=6, sticky="w"+"e")

# Adding buttons for 1 to 9
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9]
counter = 0
for x in range(3):
    for y in range(3):
        button_text = numbers[counter]
        button = tk.Button(root, text=str(button_text), width=5, height=2, command=lambda text=button_text: get_number(text))
        button.grid(row=x + 2, column=y)
        counter += 1

# Adding zero on row 5
button = tk.Button(root, text="0", width=5, height=2, command=lambda: get_number(0))
button.grid(row=5, column=1)

# Adding AC and = button
tk.Button(root, text="AC", width=5, height=2, command=lambda: clear_all()).grid(row=5, column=0)
tk.Button(root, text="=", width=5, height=2, command=lambda: calculate()).grid(row=5, column=2)

# Adding the delete/undo button
tk.Button(root, text="<-", width=5, height=2, command=lambda: undo()).grid(row=5, column=4)

# Now column 3 is empty, let's fill it up with operations
count = 0
operations = ['+', '-', '*', '/', '*3.14', "%", "(", "**", ")", "**2"]
for x in range(4):
    for y in range(3):
        if count < len(operations):
            button = tk.Button(root, text=operations[count], width=5, height=2,
                               command=lambda text=operations[count]: get_operation(text))
            count += 1
            button.grid(row=x + 2, column=y + 3)

root.mainloop()
