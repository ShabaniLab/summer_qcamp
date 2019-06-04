# Installing a Python distribution and the scientific stack

The easiest way to get the Python scientific stack is to install the
Anaconda distribution from https://www.anaconda.com/distribution/

Download the Python 3.7 installer (64 bits) and simply follows the
instructions. Once you are done you can start Python from the command line
by typing `python`, or you can use Anaconda Navigator to start VS Code or
Jupyter Notebook.


### Note

> Anaconda installer offers to install VS Code for you as part of the install
process. If you do not have a good text/code editor VS Code is a nice editor so
you can install it.


### Note

> If you do not ask the installer to add Python to the PATH on Windows, remember
to use the Anaconda Prompt instead of the standard command promt.


The Anaconda distribution comes with all the packages you need (Numpy, Scipy,
Matplotlib, Jupyter) with the exception of Qiskit. If you do not use Anaconda
you can install them using pip:

```bash
>>> pip install numpy scipy matplotlib
```

Anaconda provides a package manager to install additional libraries named
`conda` and in general you should use it. However there is no package for
qiskit so to install it you have to use `pip` from the command line.

```bash
>>> pip install qiskit
```

### Note

> During installation, you might see the warning message Failed to build qiskit.
This is a non-fatal error that does not affect installation.

To test your installation start Python (or a notebook) and import qiskit:

```python
import qiskit
qiskit.__qiskit_version__
```

You should get something similar to:

```python
{'qiskit': '0.10.3', 'qiskit-terra': '0.8.1', 'qiskit-ignis': '0.1.1', 'qiskit-aer': '0.2.1', 'qiskit-ibmq-provider': '0.2.2', 'qiskit-aqua': '0.5.1'}
```
