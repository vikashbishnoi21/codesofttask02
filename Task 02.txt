import tkinter as tk
from tkinter import messagebox

# Function to add a task
def add_task():
    task = entry.get()
    if task != "":
        listbox.insert(tk.END, task)
        entry.delete(0, tk.END)
    else:
        messagebox.showwarning("Input Error", "Please enter a task!")

# Function to delete selected task
def delete_task():
    try:
        selected = listbox.curselection()
        listbox.delete(selected)
    except:
        messagebox.showwarning("Delete Error", "Please select a task to delete!")

# Function to mark task as done
def mark_done():
    try:
        selected = listbox.curselection()[0]
        task = listbox.get(selected)
        listbox.delete(selected)
        listbox.insert(tk.END, f"✔ {task}")
    except:
        messagebox.showwarning("Mark Done Error", "Please select a task to mark as done!")

# GUI window setup
root = tk.Tk()
root.title("To-Do List App")
root.geometry("400x400")
root.config(bg="#f2f2f2")

# Entry field
entry = tk.Entry(root, width=30)
entry.pack(pady=10)

# Add Task button
add_button = tk.Button(root, text="Add Task", command=add_task, bg="#4caf50", fg="white")
add_button.pack(pady=5)

# Delete Task button
delete_button = tk.Button(root, text="Delete Task", command=delete_task, bg="#f44336", fg="white")
delete_button.pack(pady=5)

# Mark as Done button
done_button = tk.Button(root, text="Mark as Done", command=mark_done, bg="#2196f3", fg="white")
done_button.pack(pady=5)

# Listbox to display tasks
listbox = tk.Listbox(root, width=45, height=10, selectbackground="#a3c1da")
listbox.pack(pady=10)

# Run the GUI loop
root.mainloop()
