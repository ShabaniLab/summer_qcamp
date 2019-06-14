# Python traceback

A traceback in Python is what accompanies an exception. Knowing how to decipher
one help you locating bug faster.

## Simple case:

```bash
>>> '' + 1
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: can only concatenate str (not "int") to str
```

Here we attempt to carry out a fairly meaningless operation by adding a number
and a character string. Python complains that this is not possible and raise
a TypeError exception. Lets have a closer look at the traceback structure:
- first Python let us know that it will the location of the error ending by the
  most recent call last.  So to know exactly where the error occurred you
  should go all the way to the bottom of the traceback.
- next Python will list the location of each function call that lead to the
  error. The last entry is the function in which the error occurred.
- finally we get the error name and the error message.

Lets look at a more complicated example.

## A more complex case:

```bash
>>> import matplotlib.pyplot as plt
>>> plt.plot([1, 1], [2, 3], legend=1)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/Users/mdartiailh/anaconda3/envs/qiskit/lib/python3.7/site-packages/matplotlib/pyplot.py", line 2789, in plot
    is not None else {}), **kwargs)
  File "/Users/mdartiailh/anaconda3/envs/qiskit/lib/python3.7/site-packages/matplotlib/axes/_axes.py", line 1666, in plot
    lines = [*self._get_lines(*args, data=data, **kwargs)]
  File "/Users/mdartiailh/anaconda3/envs/qiskit/lib/python3.7/site-packages/matplotlib/axes/_base.py", line 225, in __call__
    yield from self._plot_args(this, kwargs)
  File "/Users/mdartiailh/anaconda3/envs/qiskit/lib/python3.7/site-packages/matplotlib/axes/_base.py", line 405, in _plot_args
    seg = func(x[:, j % ncx], y[:, j % ncy], kw, kwargs)
  File "/Users/mdartiailh/anaconda3/envs/qiskit/lib/python3.7/site-packages/matplotlib/axes/_base.py", line 312, in _makeline
    seg = mlines.Line2D(x, y, **kw)
  File "/Users/mdartiailh/anaconda3/envs/qiskit/lib/python3.7/site-packages/matplotlib/lines.py", line 404, in __init__
    self.update(kwargs)
  File "/Users/mdartiailh/anaconda3/envs/qiskit/lib/python3.7/site-packages/matplotlib/artist.py", line 957, in update
    ret = [_update_property(self, k, v) for k, v in props.items()]
  File "/Users/mdartiailh/anaconda3/envs/qiskit/lib/python3.7/site-packages/matplotlib/artist.py", line 957, in <listcomp>
    ret = [_update_property(self, k, v) for k, v in props.items()]
  File "/Users/mdartiailh/anaconda3/envs/qiskit/lib/python3.7/site-packages/matplotlib/artist.py", line 953, in _update_property
    .format(type(self).__name__, k))
AttributeError: 'Line2D' object has no property 'legend'
```

You should remember the following:
- first look at the bottom of the traceback to identify the error that occurred
- next look at the functions called starting from the bottom and go up. Try to
  find a function a you know (because you wrote it or because you used it in
  another case) and see if the error message make sense in its context.

Here the example is a bit silly since you have to go all the way to your call
where there is also a 'legend' which apparently we should not use. However
along the way, we see a line where `Line2D` is created and after that it is
apparently updated (meaningful names are important), which can help you
get a bit of context.
