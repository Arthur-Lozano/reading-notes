# Jupyter Labs
- JL is a next-gen web-based user interface for Projecdt Jupyter.
- JL enables you to work with documents and activities such as Jupyter notebooks, text editors, terminals and custom components in a flexible, intergrated, and extensible manner.
- Text editor includes syntax highlighting and configuable indentation.
- Terminals for JLN provide full support for system shells on Mac, linux and Powershell.
- All popular image formats are supported as standalone files and in notebooks.
- JSON files can be edited as cell outputs or searchable tree views.
- Vega files can be rendered as files or cell outputs.

## Jupyter Notebooks
- its a new way to work easily with data and code seamlessly.
- Jupyter has two modes: Command/Edit.
- command mode is designed to easily navigate and change the framework of your book, which is composed of cells which keeps your data, notes and code in little containers.

## Commands 
- Keyboard Shortcuts: a(add cell above), b(add cell below), c(copy), v(paste), x(cut), dd(delete), z(undo), shift+z(redo), y(cell format: Code), m(cell format: Markdown).
- Edit Mode: press enter to edit the current active cell, which will be in Markdown mode.
*italics*
**bold**
- unordered list
- unordered list
1. ordered list
2. ordered list
> blockquote
---
Type some `inline code` adn the rest of your text.
Or type in a block of code.
```
using 3 backticks then ending with 3 more backticks
```
Create equations $ x^2 $ using latex
www.jupyter.org
Create customized [links](www.jupyter.org)

## Coding
- when you run code in the cell blocks, it will appear below that cell block.
- the numbered square brackets to the left of the cell blocks is the execution order.
- Use the Run command in the menu to save time by running multiple cells at the same time.

## Numpy
- Numpy is a commonly used Python data analysis package. It allows you to speed up your workflow and interface with other packages in the Python ecosystem. 
- Almost every data analysis or machine learning package for Python uses Numpy in some way.

### List of List for CSV Data
- import the csv library
- Open winequality-red.csvfile.
- with file open, create a new csv.reader object.
- pass in teh keyword argument delimter = ";" to make sure that the records are split up on the semicolon character instead of the default comma character.
- call the list type to get all the rows from the file.
- assign the result to wines.
- `import csv`
  `with open('winequality-red.csv', 'r') as f:`
  `wines = list(csv.reader(f, delimiter=';'))`
- `print(wines[:3])`
- `[['fixed acidity', 'volatile acidity', 'citric acid', 'residual sugar', 'chlorides', 'free sulfur dioxide', 'total sulfur dioxide', 'density', 'pH', 'sulphates', 'alcohol', 'quality'], ['7.4', '0.7', '0', '1.9', '0.076', '11', '34', '0.9978', '3.51', '0.56', '9.4', '5'], ['7.8', '0.88', '0', '2.6', '0.098', '25', '67', '0.9968', '3.2', '0.68', '9.8', '5']]`
- The data has been read into a list of lists. Each innter list is a row from teh ssvfile. Each item in the entire list of lists is represented as a strings, which will make it harder to do computations.
- The data consist of three row, the first of which contains column headers. Each row after the header row represents wines. The first element of each row is the `fixed acidity`, the second is the `volatile acidity`, and so on.
- Find the average quality of wine:
- `qualities = [float(item[-1]) for item in wines[1:]] sum(qualities) / len(qualities)`

## Creating a Numpy Array
- find the average wine quality with Numpy.
- Create a Numpy array using the `numpy.array` function
- One of the limiations of Numpy is that all the elements in an array have to be of the same type. We want all the elements to be float elements for easy computation, so leave off the header row because it contains *strings*.
- import the `numpy` package.
- Pass the list of Lists `wines` into the `array` function, which converts it into a Numpy array.
- exclude the header row with list slicing.
- specify the keyword argument `dtype` to make sure each element is converted to a float.
- `import csv`
  `with open("winequality-red.csv", 'r') as f:`
  `wines = list(csv.reader(f, delimiter=";"))`
  `import numpy as np`
  `wines = np.array(wines[1:], dtype=np.float)`
- if we display `wines`, we'll now get a Numpy array:
- `array([[ 7.4 , 0.7 , 0. , ..., 0.56 , 9.4 , 5. ],
[ 7.8 , 0.88 , 0. , ..., 0.68 , 9.8 , 5. ],
[ 7.8 , 0.76 , 0.04 , ..., 0.65 , 9.8 , 5. ],
...,
[ 6.3 , 0.51 , 0.13 , ..., 0.75 , 11. , 6. ],
[ 5.9 , 0.645, 0.12 , ..., 0.71 , 10.2 , 5. ],
[ 6. , 0.31 , 0.47 , ..., 0.66 , 11. , 6. ]])`

## Alternative Numpy Array Creation Methods
- the are a variety of methods that you can use to create Numpy arrays. You can create an array where every element is zero. The below code will create an array with `3` rows and `4` columns, where every element is `0`, using numpy.zeros:
- `import numpy as np`
- `empty_array = np.zeros((3, 4))`
- `empyt_array`
- It's usefull to create an array with all zero elements in cases when you ned an array of fixed size, but don't have any values for it yet.
- You can also create an array where each element is a random number using `numpy.random.rand`.
- `np.random.rand(3, 4)`
- `array([[ 0.2247223 , 0.92240549, 0.14541893, 0.61731257],[ 0.00154957, 0.82342197, 0.74044906, 0.11466845],[ 0.6152478 , 0.14433138, 0.13009583, 0.22981301]])`.

## Numpy to Read In Files
- It's possible to use Numpy to directly read csv or other files into arrays. We can do this by the `numpy.genfromtxt` function. Use it to read our initial data on red wines.
- Use the `genfromtxt` function to read in the `winequality-red.csv` file.
- Specify the keyword argument `delimter=";"` so that the fields are parsed correctly.
- Specify the keyword argument `skip_header=1` so that the header row is skipped.
- `wines = np.genfromtxt("whinequality-red.csv", delimiter=";", skip_header=1)`.
- `wines` will end up looking the same as if we read it into the list then converted it to an array of floats. Numpy will automatically pick a data type for the elements in an array based on their format.

### Reference
- https://jupyterlab.readthedocs.io/en/stable/getting_started/overview.html
- https://www.dataquest.io/blog/numpy-tutorial-python/