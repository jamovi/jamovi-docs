.. sectionauthor:: Laiton Hedley 

=========================
Transformations Overview
=========================
   The aim of this section is to provide users a short guide on conducting common data transformations in jamovi.
   This guide is designed for users who understand the below data transformations but are unsure how to perform them using the jamovi software.
   Below we provide a brief description of each transformation with links to the step-by-step documentation to perform each (further external information can be accessed by clicking on the name of each transformation).

   It is assumed for the guides linked below that you have already loaded your data into jamovi. 
   If you have not, navigate to the three horizontal lines in the top left corner of jamovi, select ``Open`` → ``This PC`` and then choose your data file. 
   Otherwise if you do not have your own data and are looking for a sample dataset, you can use the built-in datasets available in jamovi. 
   We will be using the built-in dataset ``ToothGrowth`` which can be found by again clicking the three horizontal lines in the top left corning, clicking ``Open`` → ``Built-in library`` → ``ToothGrowth``. 
   For the cautious learner, it may be worth following along with this dataset before applying the desired transformations to your own data.

z-score Transformation
----------------------
    In short, a `z-score <https://en.wikipedia.org/wiki/Standard_score>`_ (or standard score) is the number of standard deviations a raw value is from the overall mean of the variable being measured.
    The z-score transformation standardises your variable, so it has a mean of 0 and a standard deviation of 1.
    Calculating a z-score is useful for comparing variables measured on different scales and for identifying outliers in your data.
    Thankfully jamovi has made z-score transformations for an entire column of data a seamless process, for a step-by-step guide see :doc:`here <tr_z_scores>`.
    

Normalisation Transformation (Min-Max Scaling)
----------------------------------------------
    A `Normalisation <https://towardsai.net/p/machine-learning/a-practical-walkthrough-of-min-max-scaling>`_ transformation (or Min-Max Scaling) rescales the values of a variable to a specified range, typically between 0 and 1. 
    By doing so, the minimum value of the variable becomes 0, and the maximum value becomes 1, with all other values proportionally adjusted within this range.
    This transformation is useful when you want to ensure that all variables are on the same scale and to improve interpretability of the data. 
    Normalisation transformations can be easily performed in jamovi, see :doc:`here <tr_norm>` for the step-by-step guide.

Square Root Transformation
--------------------------
   A `Square Root <https://en.wikipedia.org/wiki/Square_root>`_ transformation involves taking the square root of a value.
   This transformation is often used on non-negative count data to reduce right skewness, stabilise variance, and ensure the data is normally distributed. 
   Square root transformations can be done easily in jamovi, see :doc:`here <tr_sqr_rt>` for the step-by-step guide.

Logarithmic 10 Transformation
--------------------------
    `Logarithmic 10 <https://doi.org/10.1177/00045632211050531>`_ (or log10) transformation involves taking the logarithm of each value in a dataset to compress large numbers and expand small numbers.
    We may use a logarithmic 10 transformation to reduce right skewness, stabilise variance, make data more normally distributed, reduce the influence of outliers, and compress data with a wide range.
    Logarithmic transformations are particularly useful for data that spans several orders of magnitude or has an exponential growth pattern.
    Jamovi makes peforming logarithmic transformations easy, see :doc:`here <tr_log_10>` for the step-by-step guide.

Natural Logarithmic Transformation 
----------------------------------
    A `Natural Logarithmic <https://doi.org/10.1177/00045632211050531>`_ (or ln) transformation involves taking the natural logarithm (base e) of each value in a dataset. 
    Similar to the logarithmic 10 transformations, natural logarithmic transformations are used to reduce right skewness, stabilise variance, and make data more normally distributed.
    Natural logarithmic transformations are also useful for data that grows exponentially or spans several orders of magnitude.
    For a step-by-step guide on how to perform a natural logarithmic transformation in jamovi, see :doc:`here <tr_nat_log> ` for the step-by-step guide.


Exponential Transformation 
---------------------------
    Placeholder information 


Absolute Transformation
---------------------------
    Placeholder information


Box-Cox Transformation
----------------------
    Placeholder information


Quadratic Transformation
------------------------
    Placeholder information







----------------------


   **Topics covered:**
   - z-score transformation
   - logarithmic transformation
   - square root transformation

.. toctree::
   :maxdepth: 1
    tr_z_scores
    tr_norm
    tr_sqr_rt
    tr_log_10
    tr_nat_log

.. ----------------------------------------------------------------------------