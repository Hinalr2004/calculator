import tkinter as tk
from tkinter import messagebox

# Function to evaluate the expression
def evaluate_expression():
    try:
        result = eval(entry.get())
        entry.delete(0, tk.END)
        entry.insert(tk.END, str(result))
    except Exception as e:
        messagebox.showerror("Error", "Invalid Input")

# Function to clear the entry
def clear_entry():
    entry.delete(0, tk.END)

# Create the main window
root = tk.Tk()
root.title("Simple Calculator")
root.geometry("300x400")

# Entry widget for the expression
entry = tk.Entry(root, font=("Arial", 20), bd=10, insertwidth=2, width=15, borderwidth=4, justify='right')
entry.grid(row=0, column=0, columnspan=4)

# Button layout
buttons = [
    ('7', 1, 0), ('8', 1, 1), ('9', 1, 2), ('/', 1, 3),
    ('4', 2, 0), ('5', 2, 1), ('6', 2, 2), ('*', 2, 3),
    ('1', 3, 0), ('2', 3, 1), ('3', 3, 2), ('-', 3, 3),
    ('0', 4, 0), ('.', 4, 1), ('+', 4, 2), ('=', 4, 3),
    ('C', 5, 0)
]

# Create buttons
for (text, row, col) in buttons:
    if text == '=':
        button = tk.Button(root, text=text, padx=20, pady=20, font=("Arial", 18), command=evaluate_expression)
    elif text == 'C':
        button = tk.Button(root, text=text, padx=20, pady=20, font=("Arial", 18), command=clear_entry)
    else:
        button = tk.Button(root, text=text, padx=20, pady=20, font=("Arial", 18), command=lambda t=text: entry.insert(tk.END, t))
    button.grid(row=row, column=col, sticky="nsew")

# Run the application
root.mainloop()
