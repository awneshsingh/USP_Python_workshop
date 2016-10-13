# Python for Climate Data Analysis and Visualisation

[USP](http://www.usp.ac.fj/) / [Pacific Centre for Environment and Sustainable Development (PaCE-SD)](http://pace.usp.ac.fj/) Suva, Fiji, the 20 and 21 October 2016

Contact:

Nicolas Fauchereau

+ [@gmail](mailto:Nicolas.Fauchereau@gmail.com)
+ [@niwa](mailto:Nicolas.Fauchereau@niwa.co.nz)

<hr size=5>

### Table of contents

- [The Anaconda python distribution](#the-anaconda-python-distribution)
- [Installation of Some additional libraries](#installation-of-additional-libraries)
- [Running the IPython notebooks](#running-the-ipython-notebooks)
- [Troubleshooting](#troubleshooting)
- [Rendered notebooks](#rendered-notebooks)

<hr size=5>

## The Anaconda python distribution

For this tutorial, I **strongly** recommend installing the **Anaconda Python distribution**. It is a completely free enterprise-ready Python distribution for large-scale data processing, predictive analytics, and scientific computing. It includes the python interpreter itself, the python standard library as well as a set of packages exposing data structures and methods for data manipulation and scientific computing and visualization. In particular it provides [Numpy](http://www.numpy.org/), [Scipy](http://www.scipy.org/), [Pandas](http://pandas.pydata.org/), [Matplotlib](http://matplotlib.org/), [scikit-learn](http://scikit-learn.org/stable/), etc ... i.e. all the main packages we will be using during the tutorial. The full list of packages is available at:

[http://docs.continuum.io/anaconda/pkgs.html](http://docs.continuum.io/anaconda/pkgs.html)

The Anaconda python distribution (**NOTE**: select the version shipping with Python 3.5) must be downloaded from:

[http://continuum.io/downloads](http://continuum.io/downloads)

For your platform.

Once you have installed Anaconda, you can update to the latest compatible versions of all the pre-installed packages by running:

```
$ conda update conda
```

Then

```
$ conda update anaconda
```

In a terminal.

You also might want to install [pip](https://github.com/pypa/pip) to install packages from the [Python Package Index](http://pypi.python.org/pypi).

```
$ conda install pip
```

## Installation of additional libraries

### netcdf4

[netcdf4](https://github.com/Unidata/netcdf4-python) allows you to read and write netcdf files (version 3 and 4 supported), install it by:

```
$ conda install netcdf4
```

### Basemap

**Basemap** is a graphic library for plotting (static, publication quality) geographical maps (see [http://matplotlib.org/basemap/](http://matplotlib.org/basemap/)). **Basemap** is available directly in **Anaconda** using the conda package manager, install with:

```
$ conda install basemap
```

### Seaborn

[seaborn](http://web.stanford.edu/~mwaskom/software/seaborn/) is a Python visualization library based on matplotlib. It provides a high-level interface for drawing attractive statistical graphics. You should be able to install it with ```conda``` as well:

```
$ conda install seaborn
```
### xarray

[xarray](https://github.com/xarray/xarray) (previously *xray*) is a library aimed at bringing the power of Pandas to multidimensional labelled arrays, such as the ones usually associated with geophysical quantities varying along time and space dimensions (e.g. [time, latitudes, longitudes], [time, level, latitudes, longitudes], etc) and supports reading and writing netcdf files. It can be installed via `conda`:

```
$ conda install xarray
```

## Running the Jupyter notebooks

The material of the tutorial is in the form of [Jupyter notebooks](http://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/what_is_jupyter.html). In a nutshell a Jupyter notebook is a web-based (i.e. running in the browser) interactive computational environment where you can combine Python code execution, text, mathematics, plots and rich media into a single document, which makes it an ideal medium for teaching and exploring code.


After uncompressing the archive of the repo (or after cloning it with ```git```), navigate to the corresponding directory (containing the ```*.ipynb``` files, e.g. `session_1/notebooks`) and type:

```
$ jupyter notebook
```

That should bring up the Jupyter notebook dashboard (looking as below), you should be ready to go !

![](http://nbviewer.ipython.org/github/nicolasfauchereau/Python-for-data-analysis-and-visualisation/blob/master/session_1/notebooks/images/ipython_dashboard.png)

## Troubleshooting

You might run into some problems installing additional libraries via `conda` or `pip` and / or running the IPython notebooks, especially on Windows machines behind a proxy, here are a few solutions that may work:

**1. Proxy settings for conda:**

If you are behind a proxy, you could encounter some issues. Try first to
create a `.condarc` file (the '.' is important) in your HOME directory (on windows it should be `C:\Users\YOU`) and add the following lines:

```
proxy_servers:
    http: http://url:port
    https: http://url:port
```  

**2. specify proxy when using pip**

Again if you are behind a proxy, and if you are running into issues installing libraries via pip, try specifying the proxy to use at the command line, e.g.

```
pip install --proxy=http://url:port bearcart
```

**3. Set-up system-wide proxy settings**

+ On Macs: in your `${HOME}/.bash_profile`, insert these lines

```
export http_proxy=http://url:port
export https_proxy=http://url:port

```

+ On Linux machines, do the same as above in your `${HOME}/.bashrc`

+ On Windows machines:

  + As an administrator go to `Control Panel | System | Advanced Systems Settings | Advanced Tab | Environment Variables | System Variables | New` and set

  ```
  HTTP_PROXY=http://url:port/
  HTTPS_PROXY=https://url:port/
  ```

  + You can also do that in a command window by typing (the `$` represents the prompt)

  ```
  $ SET HTTP_PROXY=http://url:port/
  $ SET HTTPS_PROXY=http://url:port/
  ```

**4. use Firefox instead of internet explorer to open the notebooks**

  The Jupyter notebook is an interactive web-based 'notebook', where executable python code can be weaved with rich comments, graphic outputs etc, which make it ideal for presenting interactive tutorials. When (in a command prompt) you navigate to the directory where you have downloaded the notebooks and type (the $ sign represent the prompt):

  ```
  $ jupyter notebook
  ```

  a 'dashboard' with the list of notebooks should come up in your browser ... now if you are on windows, chances are that your default browser is Internet Explorer, which is generally bad news. If you encounter problems (blank page, notebooks not loading, kernel interruptions etc), it's probably because of Internet Explorer. What I suggest is that you download [Firefox](https://www.mozilla.org/en-US/firefox/new/) or [Chrome](https://www.google.com/chrome/browser/desktop/) for windows and make it the default browser (your can revert to Internet explorer being the default browser after the workshop if you really want)

**5. Specify localhost when calling the IPython notebook**

On some configurations, you might also need to call:

```
$ jupyter notebook --ip=127.0.0.1
```

To specify that the browser should connect to *localhost*

**6. Clear the cache**

If you are still running into issues (notably dashboard or jupyter notebook not displaying correctly), try *clearing the cache of your browser*

**7. Use an `incognito` window**

If all else fails (!), one thing that has been reported working is:

+ launch the `jupyter notebook` in no-browser mode:

```
jupyter notebook --no-browser
```

You should see an output in the terminal looking like:

```
...
The jupyter Notebook is running at: http://localhost:8888/
...
```

Note that the URL and port could be different in your case.

Open an `incognito` window from your browser and copy the URL (`http://localhost:8888/`) in the address bar

## Rendered notebooks

**SESSION 1**

+ [resources and acknowledgments](https://cdn.rawgit.com/nicolasfauchereau/USP_Python_workshop/master/session_1/notebooks/resources.html)

+ [Jupyter notebook
  overview](https://cdn.rawgit.com/nicolasfauchereau/USP_Python_workshop/master/session_1/notebooks/Jupyter_notebook.html)

+ [Python language basics](https://cdn.rawgit.com/nicolasfauchereau/USP_Python_workshop/master/session_1/notebooks/introduction_python.html)

+ [Numpy](https://cdn.rawgit.com/nicolasfauchereau/USP_Python_workshop/master/session_1/notebooks/Numpy.html)

+ [Scipy](https://cdn.rawgit.com/nicolasfauchereau/USP_Python_workshop/master/session_1/notebooks/Scipy.html)

+ [Matplotlib](https://cdn.rawgit.com/nicolasfauchereau/USP_Python_workshop/master/session_1/notebooks/Matplotlib.html)

+ [Pandas](https://cdn.rawgit.com/nicolasfauchereau/USP_Python_workshop/master/session_1/notebooks/Pandas.html)

**SESSION 2**

+ [More on pandas](https://cdn.rawgit.com/nicolasfauchereau/USP_Python_workshop/master/session_2/notebooks/Pandas.html)

+ [xarray](https://cdn.rawgit.com/nicolasfauchereau/USP_Python_workshop/master/session_2/notebooks/xarray.html)

+ [Basemap](https://cdn.rawgit.com/nicolasfauchereau/USP_Python_workshop/master/session_2/notebooks/Basemap.html)
