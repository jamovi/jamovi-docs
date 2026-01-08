.. sectionauthor:: Laiton Hedley 

==============================================
Data Manipulation and Transformations Overview
==============================================
   The aim of this section is to provide users a short overview of the common data manipulations and transformations avaialble in jamovi.
   This documentation is designed for users who understand their desired manipulation or transformation but are unsure how to perform them using the jamovi software.
   It is assumed that you have already loaded your data into jamovi. If you are unsure how to do this see `the spread sheet breakdown <https://docs.jamovi.org/_pages/um_2_first-steps.html>`_ for help getting started with the jamovi interface.
   
==================================================================================================
Which one should I use? ``New Computed Variable`` vs ``New Transformed Variable``
==================================================================================================

   In jamovi there are two routes to perform a data transformation, if you click on a blank column (or row of a blank column header), you will see above your spread sheet a few options including ``New Computed Variable`` and ``New Transformed Variable`` (the ``New Data Variable`` option allows you to manually input data which we will ignore for now).
   The ``New Computed Variable`` option is best chosen when you're seeking to apply a transformation to a single variable (or to generate simulate some data using the options provided in jamovi). 
   The ``New Transformed Variable`` option is better suited for complex transformations, especially when you'd like to apply the same transformation to multiple columns of data. 
   This is made possible because the ``New Transformed Variable`` option also allows for the intuitive use of "if then" statements to create more complex transformations and data handling. 
   For example, perhaps you would like to apply a logarithmic transformation but want to avoid errors such as attempting to take the logarithm of negative values or zero. 
   You could embed an if else statements to avoid taking the logarithm of zeros and recode negative numbers to missing values.
   While it is possible to use the ``New Computed Variable`` option to create similar complex transformations, it can be more time consuming if you have many columns of data to transform. 
   
   Generally, applying transformations using either way is similar for both options with a minor difference - that being how you reference the `variable` you'd like to transform.
   For example, when applying a logarithmic 10 transformation, both methods would simply involve using the `LOG10`` option.
   The difference lies within how you 'call' or refer to your `variable` or column of data you'd like to transform.
   For example, using ``New Computed Variable`` you would simply use the column name of variable, so if your variable is called `variable_name`, you would place the function as `LOG10(variable_name)`.
   In contrast, using ``New Transformed Variable`` you would need instead `$SOURCE` to call the variable, so to apply the same transformation you would call the function as `LOG10($SOURCE)`.
   More information on both the ``New Computed Variable`` and ``New Transformed Variable`` options can be found `here <https://docs.jamovi.org/_pages/um_4_spreadsheet.html>`_. 
   For better understanding of when to use the ``New Transformed Variable`` option, see our `blog post <https://blog.jamovi.org/index.php/2021/08/12/transforming-multiple-variables-in-jamovi/>`_.
   With that out of the way, below is a table listing the common data transformations available in jamovi. 

=============================================
Placeholder Heading Transformation Table..... 
=============================================
Here we provide a summary table of the data transformations covered in this section.
For each transformation the function to be called in jamovi is provided along with a brief definition and example use case. 
For each use case we have used 'variable_name' as a placeholder for the name of your variable/column of data. 
At times, you may want to use multiple columns of data within a transformation. 
In the example use cases below, when a transformation requires additional columns of data we will refer to these as 'variable_name_2', 'variable_name_3' and so on. 
Hopefully you're naming conventions are better than ours, but at least this should make the example use cases clear and easy to follow.

.. list-table:: Data Transformations Currently Available in jamovi
   :header-rows: 1

   * - Transformation
     - Definition
     - Found Under
     - Function in jamovi
     - Example Use Case
   * - Absolute
     - Placeholder information
     - Math
     - `ABS`
     - ABS(variable_name)
   * - Exponential
     - Placeholder information
     - Math
     - `EXP`
     - EXP(variable_name)
   * - Logarithmic 10
     - `Logarithmic 10 <https://doi.org/10.1177/00045632211050531>`_ transformation involves taking the logarithm of each value in a dataset to compress large numbers and expand small numbers.
     - Math
     - `LOG10`
     - LOG10(variable_name)
   * - Natural Logarithmic
     -  A `Natural Logarithmic <https://doi.org/10.1177/00045632211050531>`_ transformation involves taking the natural logarithm (base e) of each value in a dataset, similarly to the logarithmic 10 transformation it is used to reduce right skewness, stabilise variance, and make data more normally distributed.
     - Math
     - `LN`
     - LN(variable_name)
   * - Square Root
     - A `Square Root <https://en.wikipedia.org/wiki/Square_root>`_ transformation involves taking the square root of a value. This transformation is often used on non-negative count data to reduce right skewness, stabilise variance, and ensure the data is normally distributed.
     - Math
     - `SQRT`
     - SQRT(variable_name)
   * - Absolute Interquartile Range
     - Placeholder information
     - Statistical
     - `ABSIQR`
     - ABSIQR(variable_name)
   * - Absolute z-score (or Absolute standard score)
     - The number of absolute standard deviations a raw value is from the overall mean of the variable being measured. The z-score transformation standardises your variable, so it has a mean of 0 and a standard deviation of 1, the absolute z-score takes the absolute value of this transformation ignoring the sign.
     - Statistical
     - `ABSZ`
     - ABSZ(variable_name)
   * - Box Cox
     - Placeholder information
     - Statistical
     - `BOXCOX`
     - BOXCOX(variable_name)
   * - Interquartile Range
     - Placeholder information
     - Statistical
     - `IQR`
     - IQR(variable_name)
   * - Max
     - Placeholder information
     - Statistical
     - `MAX`
     - MAX(variable_name, variable_name_2)
   * - Mean
     - Placeholder information
     - Statistical
     - `MEAN`
     - MEAN(variable_name)
   * - Min
     - Placeholder information
     - Statistical
     - `MIN`
     - MIN(variable_name, variable_name_2)
   * - Rank
     - Placeholder information
     - Statistical
     - `Rank`
     - RANK(variable_name)
   * - Round
     - Placeholder information
     - Statistical
     - `ROUND` Note that the 3 in the example use case rounds `variable_name` to 3 decimal places. This can be adjusted to say 1 or 2 for 1 or 2 decimal places respectively, or to 0 for whole numbers.
     - ROUND(variable_name, 3)
   * - Floor
     - Placeholder information, rounds down to the nearest whole number/integer.
     - Statistical
     - `FLOOR`
     - FLOOR(variable_name)
   * - Cieling
     - Placeholder information, rounds up to the nearest whole number/integer.
     - Statistical
     - `CEILING`
     - CEILING(variable_name)
   * - Standard score (z-score)
     -  a `z-score <https://en.wikipedia.org/wiki/Standard_score>`_ or standard score is the number of standard deviations a raw value is from the overall mean of the variable being measured. The z-score transformation standardises your variable, so it has a mean of 0 and a standard deviation of 1.
     - Statistical
     - `SCALE`
     - SCALE(variable_name)
   * - Standard deviation
     - place holder information.
     - Statistical
     - `STDEV`
     - STDEV(variable_name, variable_name_2)
   * - Sum
     -  Placeholder information.
     - Statistical
     - `SUM`
     - SUM(variable_name, variable_name_2, variable_name_3)
   * - z-score (standard score)
     -  a `z-score <https://en.wikipedia.org/wiki/Standard_score>`_ (or standard score) is the number of standard deviations a raw value is from the overall mean of the variable being measured. The z-score transformation standardises your variable, so it has a mean of 0 and a standard deviation of 1.
     - Statistical
     - `Z`
     - Z(variable_name)


=====================================================
Placeholder Heading More Custom Transformations Table
=====================================================


   **Topics covered:**
   - stuff
  
  
  **Topics covered:**
  - stuff

.. toctree::
   :maxdepth: 1
   

.. ----------------------------------------------------------------------------