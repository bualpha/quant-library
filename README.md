# Quant Library

This serves as a library of helpful books, sites, code samples, notebooks, blog posts, and many other resources for people to read through
if they're interested in learning more about quant finance.

These resources are vetted by [BU Alpha](https://github.com/bualpha/), a quant research team developed within the [BU Finance and Investment Club](http://buinvest.org).

Within each of the directories is a `README.md` file, which has links to books, sites, blog posts, and other links. Lecture notes, papers, code and notebooks are all stored in the repository in their respective formats, i.e. `.py`, `.ipynb`, `.pdf` and other types of file extensions.


## Setting up a Development Environment

If you want to experiment with some of the concepts mentioned within the papers, we suggest writing some [Python](https://www.python.org/about/) code. We've written about how to setup a development environment below, using [Anaconda](https://docs.continuum.io/anaconda/); a package manager for Python and Python distribution that allows you to create separate virtual environments for various development tasks.

**Installing Anaconda**:
  1. [Install Anaconda](https://www.continuum.io/downloads)
  2. After installing Anaconda, open up your terminal or command prompt and type `conda create --name pydata35 python=3.5 anaconda`; this will create a [conda environment](https://conda.io/docs/using/envs.html) and you will be able to use different mathematical & statistical libraries
  3. Then, in your terminal, run `source activate pydata35`
  4. Done!

The steps above are for a very simple setup with the most fundamental scientific computing libraries such as [numpy](http://www.numpy.org/), [pandas](http://pandas.pydata.org/), [matplotlib](https://matplotlib.org/), and [IPython](https://ipython.org/). You should be able to follow all of the steps for Linux, Windows, and macOS.

If you want a deeper understanding of how these libraries work and why they're important to the PyData community, check out Scott Sanderson's [PyData Toolbox](https://github.com/ssanderson/pydata-toolbox) talk.

## Getting Started

So now that you've installed Anaconda and have Python on your machine, you can start writing some code. Say you want to describe some stock data using measures of centrality (means) or measures of dispersion (variance). First we'll need a way to get some stock data. To make this easier, you can install [pandas-datareader](https://github.com/pydata/pandas-datareader), by running:

`pip install pandas-datareader`

You should now have that installed. You can check that this is true by running:

`pip freeze`

Which will output all existing Python packages in your conda environment to your terminal.

After doing so, you can open up an [IPython REPL](http://ipython.readthedocs.io/en/stable/interactive/tutorial.html) and run the following code:

```
# import the libraries we'll need
# pandas_datareader uses pandas under the hood

In [1]: import pandas_datareader as pdr

In [2]: import datetime

# set a start and end date you want for your data
In [3]: start = datetime.datetime(2010, 1, 1)

In [4]: end = datetime.datetime(2017, 1, 1)

# request stock pricing data about Netflix from Yahoo Finance
In [5]: data = pdr.DataReader('NFLX', 'yahoo', start, end)

In [5]: data.describe()
Out[5]:
              Open         High          Low        Close    Adj Close  \
count  1762.000000  1762.000000  1762.000000  1762.000000  1762.000000
mean     48.994822    49.818289    48.170577    49.022988    49.022988
std      35.372219    35.913746    34.812488    35.380533    35.380533
min       6.960000     7.178571     6.931428     7.018571     7.018571
25%      16.883215    17.274286    16.451429    16.916429    16.916429
50%      37.448570    38.154286    36.959286    37.647855    37.647855
75%      68.640715    69.236071    67.815716    68.449283    68.449283
max     131.190002   133.270004   126.389999   130.929993   130.929993

             Volume
count  1.762000e+03
mean   2.738449e+07
std    2.393028e+07
min    1.616300e+06
25%    1.347185e+07
50%    2.116330e+07
75%    3.294988e+07
max    3.155418e+08
```

And once we have that `data` variable, we can go ahead and do all sorts of analysis on it. You can also save that data as a `csv` file by running:

```
In [6]: data.to_csv('NFLX_data.csv')
```

You can also do this in an [IPython Notebook](https://ipython.org/notebook.html), which is recommended if you want to more in-depth analysis.

## Directory Structure

Here is the current directory structure as of August 28th, 2017:

```
quant-library/
├── LICENSE
├── README.md
├── code-and-notebooks
│   └── generating-correlation-matrices.ipynb
├── computer-science
│   ├── MathForCS.pdf
│   ├── README.md
│   └── machine-learning
│       └── README.md
├── finance
│   ├── README.md
│   └── algo-trading
│       ├── 101FormulaicAlphas.pdf
│       ├── BuildingDiversifiedPortfolios-OutperformOOS.pdf
│       ├── DrawdownWhenToWorry.pdf
│       ├── HierarchicalRiskParity.pdf
│       ├── MIT18S096-FactorModels.pdf
│       ├── MeasuringFactorExposures-AQR-WhitePaper.pdf
│       └── README.md
├── math
│   ├── README.md
│   ├── linear-algebra
│   │   ├── README.md
│   │   └── RandomMatrixTheory.pdf
│   └── optimization
│       ├── CVXPortfolio.pdf
│       └── README.md
└── statistics
    ├── README.md
    ├── StupidMining.pdf
    └── bayesian
        ├── BayesianComputationInFinance.pdf
        └── ThinkBayes.pdf

10 directories, 23 files
```

## Questions?

If you find a typo, bug in any code, or have any questions, feel free to open an issue on our [GitHub issue tracker](https://github.com/bualpha/quant-library/issues).

## Contribute

If you want to add some resource to the repository, feel free to open a pull request and fill out the [template](https://github.com/bualpha/quant-library/blob/master/.github/PULL_REQUEST_TEMPLATE.md).
We ask that any papers you submit please be in PDF format, and any lecture notes also include a link to a video lecture that accompanies the notes.

