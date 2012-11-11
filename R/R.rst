===============================================================================
R Cheat Sheet
===============================================================================

:Author: Mario Rodas
:Version: 0.1

Getting Help
===============================================================================

======================= =======================================================
Command			Description
======================= =======================================================
help(cmd) # or ?cmd	Display the documentation for *cmd*.
??cmd			Search the documentation with *cmd* in title.
args(cmd)		Display the arguments of *cmd*.
example(cmd)		Display examples of *cmd*.
help.start()		View the documenation supplied by R.
RSiteSearch("phrase")	Search "phrase" in search.r-project.org
======================= =======================================================

Reading files
===============================================================================

=============================== ===============================================
Command				Description
=============================== ===============================================
read.table("filename.txt")	Reads tabular file.
read.csv("filename.csv")	Reads csv file.
=============================== ===============================================

Statistics Functions
===============================================================================

=============== ===============================================================
Command		Description
=============== ===============================================================
mean(x)		mean
median(x)	median
sd(x)		Standard deviation
var(x)		Variance
cor(x, y)	Correlation
cov(x, y)	Covariance
=============== ===============================================================

Data Manipulation Functions
===============================================================================

=============== ===============================================================
Command		Description
=============== ===============================================================
which		Which indices are TRUE.
=============== ===============================================================


Misc. Functions
===============================================================================

=============== ===============================================================
Command		Description
=============== ===============================================================
demo()		Demostration R scripts.
data()		Show data sets.
getwd()		Get current working dir.
setwd(dir)	Set current working dir.
=============== ===============================================================

Tips & Tricks
===============================================================================

Installling external packages
-------------------------------------------------------------------------------

1. Install from source:

.. code:: console

   $ R CMD INSTALL mypkg -l /my/own/R-packages/

2. Install from CRAN_ directly:

.. code:: rconsole

    > install.packages("mypkg", lib="/my/own/R-packages/")

3. Downloading and installing:

.. code:: rconsole

    > download.file("http://example.com/pkg.tar.gz", destfile="~/pkg.tar.gz")
    > install.packages("~/pkg.tar.gz", repos=NULL)


Install Bioconductor Packages
-------------------------------------------------------------------------------

Bioconductor_ provides nice R packages.

http://www.bioconductor.org/install/

.. code:: rconsole

    > source("http://bioconductor.org/biocLite.R")
    > biocLite("Rgraphviz")


Tools
===============================================================================
RStudio
  | http://www.rstudio.org/
  | Ubuntu ppa: ppa:aims/aims-desktop


Links
===============================================================================

R-project
  | http://www.r-project.org

R-project search engine
  | http://www.rseek.org/

The Comprehensive R Archive Network
  | http://cran.r-project.org/

Stackoverflow
  | http://stackoverflow.com/

R bloggers
  | http://www.r-bloggers.com/

..  Links: {{{

.. _Bioconductor: http://www.bioconductor.org/
.. _CRAN: http://cran.r-project.org/

.. }}}

.. vim:ft=rst:tw=79:noet:
