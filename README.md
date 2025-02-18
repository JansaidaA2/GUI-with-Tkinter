# GUI-with-Tkinter
Tkinter Apps


# Python GUI Applications

This repository contains two Python GUI applications built using the Tkinter library. The applications are:

1. **Frontend App**
2. **Password Generator App**

3. ### Code Snippet 
```python
import tkinter as tk

def on_button_click():
    label.config(text='Button clicked')
    print('hello world')

root = tk.Tk()
root.title('Simple tkinter app')
root.geometry('200x300')

label = tk.Label(root, text='Hello world')
label.pack(pady=20)

button = tk.Button(root, text='touch me', command=on_button_click)
button.pack(pady=20)

root.mainloop()

### password generator:


from tkinter import Tk, Label, BOTTOM, IntVar, Spinbox, StringVar, Button, Entry
import random, string
import pyperclip

root = Tk()
root.geometry("400x400")
root.resizable(0, 0)
root.title("PYTHON PROJECT - PASSWORD GENERATOR")

Label(root, text='PASSWORD GENERATOR', font='arial 15 bold').pack()
Label(root, text='Python', font='arial 15 bold').pack(side=BOTTOM)

pass_label = Label(root, text='PASSWORD LENGTH', font='arial 10 bold').pack()
pass_len = IntVar()
length = Spinbox(root, from_=8, to_=32, textvariable=pass_len, width=15).pack()
pass_str = StringVar()

def Generator():
    password = []
    if pass_len.get() >= 4:
        password.append(random.choice(string.ascii_uppercase))
        password.append(random.choice(string.ascii_lowercase))
        password.append(random.choice(string.digits))
        password.append(random.choice(string.punctuation))
        for _ in range(pass_len.get() - 4):
            password.append(random.choice(string.ascii_uppercase + string.ascii_lowercase + string.digits + string.punctuation))
        random.shuffle(password)
    else:
        for _ in range(pass_len.get()):
            password.append(random.choice(string.ascii_uppercase + string.ascii_lowercase + string.digits + string.punctuation))
    pass_str.set(''.join(password))

def Copy_password():
    pyperclip.copy(pass_str.get())

Button(root, text='GENERATE PASSWORD', command=Generator).pack(pady=5)
Entry(root, textvariable=pass_str).pack()
Button(root, text='COPY TO CLIPBOARD', command=Copy_password).pack(pady=5)

root.mainloop()
