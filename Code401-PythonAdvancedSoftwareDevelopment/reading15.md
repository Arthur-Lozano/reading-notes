# Matplotlib Tutorial

- single most used Python package for 2D-graphics
- provides both a very quick way to visualize data from Python and publication-quality figures in many formats.

## Ipython and the pylab mode

- Ipython is an enhanced interactive Python shell that has lots of interesting features including named inputs and outputs, access to shell commands, improved debugging and a lot more. 
- pyplot - provides a convenient interface to the matplotlib object-oriented plotting library.

## Simply plot

- import numpy as np
- get data from the sine and cosine functions: `x = np.linespace(-np.pi, np.pi, 256, endpoint=True)`
- assign to vars: `C, S = np.cos(x), np.sin(x)`
- X is not a numpy array with 256 values.
- Matplot: control defaults of almost every property in matplotlib: figure size and dip, line width, color and style, axes, axis and grid props, text, font and so on.

## Changing colors and line widths

- `plt.figure(figzise=(10, 6), dip=80)`
- `plt.plot(X, C, color="blue", linewidth=2.5, linestyle="-")`
- `plt.plot(X, S, color="red",  linewidth=2.5, linestyle="-")`

## Setting limits

- `plt.xlim(X.min()*1.1, X.max()*1.1)`
- `plt.ylim(C.min()*1.1, C.max()*1.1)`

## Setting ticks

- changes the amount of points/labels that run across the x and y axis
- `plt.xticks( [-np.pi, -np.pi/2, 0, np.pi/2, np.pi])`
- `plt.yticks([-1, 0, +1])`

## Setting tick labels

- changes x, y tick labels
- `plt.xticks([-np.pi, -np.pi/2, 0, np.pi/2, np.pi],[r'$-\pi$', r'$-\pi/2$', r'$0$', r'$+\pi/2$', r'$+\pi$'])`
- `plt.yticks([-1, 0, +1],[r'$-1$', r'$0$', r'$+1$'])`

## Add legend

- mini graph in the top right of larger graph
- `plt.plot(X, C, color="blue", linewidth=2.5, linestyle="-", label="cosine")`
- `plt.plot(X, S, color="red",  linewidth=2.5, linestyle="-", label="sine")`
- `plt.legend(loc='upper left', frameon=False)`

### Reference 
- https://github.com/rougier/matplotlib-tutorial