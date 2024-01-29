# BinaryTopologicalSpaces

¡Hi there!

Let's suppose we have a binery topological space $(\mathcal{M}, X,Y)$ given by 
$$X = \lbrace a,b,c,d\rbrace, Y = \lbrace e,f,g,h,i\rbrace,\mathcal{M} = \lbrace (\emptyset ,\emptyset), (X,Y),(\lbrace a\rbrace,\lbrace e\rbrace),(\lbrace b\rbrace,\lbrace f\rbrace),(\lbrace a,b\rbrace,\lbrace e,f\rbrace)\rbrace,$$

you have to compute it in a txt file as:

```txt

```

To run in Google Collab :

```python
from tkinter import *
from tkinter import filedialog
import os

desktop_dir = os.path.expanduser("~/Desktop")

root = Tk()
root.withdraw()

#root.filename = filedialog.askopenfilename(initialdir='/',title="Select A File",filetypes=())
root.filename = filedialog.askopenfilename(initialdir=desktop_dir, title="Select A File", filetypes=(("txt files", "*.txt"),("all files", "*.*")))
print(root.filename)
root.destroy()


M = []
with open(root.filename, 'r') as file:
    lines = []
    for line in file:
        lines.append(line.strip())
    print(lines)
    partition1 = lines[0:1]
    partition2 = lines[2::]
    X = eval(lines[0])
    Y = eval(lines[1])
    for element in lines[2::]:
        if element == '[X,Y]':
            M.append([X, Y])
        else:
            M.append(eval(element))
```

To run from computer, in an IDE or even in a python notebook in VScode:

```python
from google.colab import files

# Upload a file and get the content
uploaded = files.upload()

# Extract the filename and content
filename = list(uploaded.keys())[0]
content = uploaded[filename].decode('utf-8')

M = []
lines = content.split('\n')
partition1 = lines[0:1]
partition2 = lines[2::]
X = eval(lines[0])
Y = eval(lines[1])
for element in lines[2::]:
    if element == '[X,Y]':
        M.append([X, Y])
    else:
        M.append(eval(element))

print("X:", X)
print("Y:", Y)
print("M:", M)
```
