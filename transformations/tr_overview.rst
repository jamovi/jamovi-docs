.. sectionauthor:: Laiton Hedley 

==============================================
Manipulations and Transformations Overview
==============================================
   The aim of this section is to provide users a short overview of the common manipulations and transformations avaialble in jamovi.
   This documentation is designed for jamovi users who understand their desired manipulation or transformation but are unsure how to perform them using our software.
   It is assumed that you have already loaded your data into jamovi, if you are unsure how to do this see `First steps in jamovi <https://docs.jamovi.org/_pages/um_2_first-steps.html>`_.
   
==================================================================================================
New Computed Variable vs New Transformed Variable 
==================================================================================================
    In jamovi there are two main routes to perform manipulations and transformations.
    If you click on a blank column (or the header of a blank column), you will see several options above your spreadsheet, including ``New Computed Variable`` and ``New Transformed Variable`` (the ``New Data Variable`` option allows you to manually input data, which we will ignore for now).
    The ``New Computed Variable`` option is best used when you want to manipulate or transform a single column of data (or generate a simulated column of data).
    The ``New Transformed Variable`` option is better suited for more complex manipulations and transformations, especially when you would like to apply the same manipulation or transformation to multiple columns of data.
    Although both approaches can achieve similar outcomes, there are two key differences.
    First is how you refer to the variable (i.e., the column of data) you would like to manipulate or transform. For example, when applying a base-10 logarithmic transformation, both methods use the `LOG10` function. 
    However, the difference lies in how you “call” or refer to the variable.
    Using ``New Computed Variable``, you would simply use the column name.
    So if your column of data is called `variable_name`, you would write `LOG10(variable_name)`.
    In contrast, using ``New Transformed Variable``, you instead assign the variable you would like to manipulate or transform as the ``Source variable``, which will appear as `$SOURCE` when calling a function. 
    So the same transformation would be written as `LOG10($SOURCE)`.
    Second, ``New Computed Variable`` is typically used for simple, one-off tasks, whereas ``New Transformed Variable`` is usually used for more complex workflows and reusable transformations. 
    ``New Transformed Variable`` is often better suited for more complex manipulations, such as recoding levels in a variable based on specific criteria.
    Imagine you have a column where participants self-report their smoking habits as Daily, Weekly, Monthly, Occasionally, and Never. Perhaps you want to recode this into a binary variable indicating whether participants are smokers (Daily, Weekly, Monthly, Occasionally) or non-smokers (Never).
    Using the ``New Computed Variable`` option, you could use the following::

        IF(`variable_name` == "Never", "non-smoker", "smoker")
    
    This would create a new column with the values recoded as smoker and non-smoker.
    In contrast, using the ``New Transformed Variable`` option, you would click ``Source variable`` and select `variable_name`. 
    Then click ``using transform``, followed by ``create new``. 
    Next to the plus symbol, click ``Add recode condition``. 
    This allows you to recode your variable using the same if/then logic in a more user-friendly way.
    Additionally, this same manipulation can be saved for later if you have a similar column of data to recode. 
    The same applies for transformations: the ``New Transformed Variable`` option allows you to save and re-apply the same transformation to additional columns seamlessly.
    
    More information on both the ``New Computed Variable`` and ``New Transformed Variable`` options can be found `here <https://docs.jamovi.org/_pages/um_4_spreadsheet.html>`_.
    For additional information on the ``New Transformed Variable`` option (especially for transforming multiple variables), see this `blog post <https://blog.jamovi.org/index.php/2021/08/12/transforming-multiple-variables-in-jamovi/>`_.
    With that out of the way, below are more details on the common manipulations and transformations made accessible in jamovi.

===========================================================
Common Data Manipulations and Transformations using jamovi  
===========================================================
    Below we provide a summary table of the common data manipulations and transformations made possible using jamovi.
    We provide a brief definition of each manipulation and transformation, where to find it in jamovi (or if it requires custom inputs), the function to be called, and an example use case of this function.
    For each use case we have used 'variable_name' as a placeholder for the name of your variable or column of data. 
    At times, you may want to use multiple columns of data within a manipulation or transformation, such as calculating the participant's mean or the summation across a range of scale items. 
    Therefore, in the example use cases below we will refer to additional columns of data as 'variable_name_2', 'variable_name_3' and so on. 
    Hopefully your naming conventions are better than ours, but at least this should make the example use cases clear and easy to follow.

    Below, we provide a summary table of common data manipulations and transformations available in jamovi.
    For each manipulation or transformation, we include a brief definition, where to find it in jamovi (or whether it requires custom input), the function to call, and an example use case.
    In each use case, we use `variable_name` as a placeholder for the name of your variable (i.e., your column of data).
    Sometimes you may want to use multiple columns within a single manipulation or transformation, such as calculating across a set of scale items each participant's mean or their summed scores.
    For this reason, the example use cases below refer to additional columns as `variable_name_2`, `variable_name_3`, and so on.
    Hopefully your naming conventions are better than ours, but this should keep the examples clear and easy to follow.

.. list-table:: Transformations Easily Accesible in jamovi
   :header-rows: 1

   * - Transformation
     - Definition
     - Found Under
     - Function in jamovi
     - Example Use Case
   * - z-score (standard score) so scale and z do the same thing - why do we have both in jamovi? 
     -  A `z-score <https://en.wikipedia.org/wiki/Standard_score>`_ (or standard score) is the number of standard deviations a raw value is from the overall mean of the variable being measured. The z-score transformation standardises your variable, so it has a mean of 0 and a standard deviation of 1.
     - Statistical
     - `Z`
     - Z(variable_name)
   * - Standard score (z-score) Do we even want this? - we already have z-score...?
     -  A `z-score <https://en.wikipedia.org/wiki/Standard_score>`_ or standard score is the number of standard deviations a raw value is from the overall mean of the variable being measured. The z-score transformation standardises your variable, so it has a mean of 0 and a standard deviation of 1.
     - Statistical
     - `SCALE`
     - SCALE(variable_name)   
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
     - A `Square Root <https://en.wikipedia.org/wiki/Square_root>`_ transformation takes the square root of a variable. This transformation is often used on non-negative count data to reduce right skewness, stabilise variance, and ensure the data is normally distributed.
     - Math
     - `SQRT`
     - SQRT(variable_name) 
   * - Exponential
     - An `exponential <https://en.wikipedia.org/wiki/Exponential_function>`_ transformation raises a constant (often e or 10) to the power of each value, which turns differences in the original variable into multiplicative changes. Small increases become much larger on the transformed scale, and larger values are amplified the most.
     - Math
     - `EXP`
     - EXP(variable_name)
   * - Box-Cox
     - A `Box–Cox transformation <https://en.wikipedia.org/wiki/Power_transform#Box%E2%80%93Cox_transformation>`_ finds an exponent (λ) to make the distribution of your data closer to normal and make it's variance more stable; it can only be used for positive continuous data typically when the data are skewed or show non-constant spread.
     - Statistical
     - `BOXCOX`
     - BOXCOX(variable_name)
   * - Interquartile Range
     - The Interquartile Range tells you how spread out the middle 50% of your data is by calculating Q3 minus Q1. It is useful because it can help flag unusually low or high scores using the common boxplot rule of values below Q1 minus 1.5 times the IQR or above Q3 plus 1.5 times the IQR.
     - Statistical
     - `IQR`
     - IQR(variable_name)
   * - Ranking 
     - `Ranking <https://en.wikipedia.org/wiki/Ranking_(statistics)>`_ assigns an ordinal rank to each value in a dataset based on its position relative to other values. The smallest value receives the rank of 1, the next smallest receives rank 2, and so on. This transformation is useful for non-parametric analyses or when you want to focus on the order of values rather than their actual magnitudes.
     - Statistical
     - `Rank`
     - RANK(variable_name)
   * - Rounding 
     - `Rounding <https://en.wikipedia.org/wiki/Rounding>`_ a variable involves adjusting each value to a specified number of decimal places or to the nearest whole number. This transformation is often used to simplify data presentation, reduce precision for reporting purposes, or prepare data for certain analyses that require integer values. 
     - Statistical
     - `ROUND` Note that the 3 in the example use case rounds `variable_name` to 3 decimal places. This can be adjusted to say 1 or 2 for 1 or 2 decimal places respectively, or to 0 for whole numbers.
     - ROUND(variable_name, 3)
   * - Absolute
     - Taking the `absolute value <https://en.wikipedia.org/wiki/Absolute_value>`_ simply converting all negative values in a dataset to their positive counterparts, while leaving positive values unchanged. This transformation is often used to focus on the magnitude of values without regard to their direction (ignoring whether values are positive or negative).
     - Math
     - `ABS`
     - ABS(variable_name)
   * - Absolute Interquartile Range
     - The Absolute Interquartile Range tells you how spread out the middle 50% of your data is by calculating Q3 minus Q1. It is useful because it can help flag unusually low or high scores using the common boxplot rule of values below Q1 minus 1.5 times the IQR or above Q3 plus 1.5 times the IQR.
     - Statistical 
     - `ABSIQR`
     - ABSIQR(variable_name)
   * - Absolute z-score (or Absolute standard score)
     - The number of absolute standard deviations a raw value is from the overall mean of the variable being measured. The z-score transformation standardises your variable, so it has a mean of 0 and a standard deviation of 1, the absolute z-score takes the absolute value of this transformation ignoring the sign.
     - Statistical
     - `ABSZ`
     - ABSZ(variable_name)
   * - Floor
     - The `Floor <https://en.wikipedia.org/wiki/Floor_and_ceiling_functions>`_  function essentially takes a real number and returns the greatest integer that is less than that number, effectively rounding down to the nearest whole number.
     - Statistical
     - `FLOOR`
     - FLOOR(variable_name)
   * - Ceiling
     - The `Ceiling <https://en.wikipedia.org/wiki/Floor_and_ceiling_functions>`_ function takes a real number and returns the smallest integer that is greater than or equal to that number, effectively rounding up to the nearest whole number.
     - Statistical
     - `CEILING`
     - CEILING(variable_name)
   * - Mininum 
     - `Mininum or Min values <https://en.wikipedia.org/wiki/Maximum_and_minimum>`_ are the lowest values in a row or column of data, this transformation can be used when you want to identify the highest score across multiple variables for each participant or row of data.
     - Statistical
     - `MIN`
     - MIN(variable_name, variable_name_2)
   * - Maximum
     - `Maximum or Max values <https://en.wikipedia.org/wiki/Maximum_and_minimum>`_ are simply the highest values in a row or column of data, this transformation can be used when you want to identify the highest score across multiple variables for each participant or row of data.
     - Statistical
     - `MAX`
     - MAX(variable_name, variable_name_2, variable_name_3)
   * - Standard deviation
     - `Standard deviation <https://en.wikipedia.org/wiki/Standard_deviation>`_ is a measure of the amount of variation or dispersion in a set of values. A low standard deviation indicates that the values tend to be close to the mean (average) of the set, while a high standard deviation indicates that the values are spread out over a wider range.
     - Statistical 
     - `STDEV`
     - STDEV(variable_name, variable_name_2)
   * - Summation
     - `Summation or Sum <https://en.wikipedia.org/wiki/Summation>`_ calculates the total of items (or columns of data) by adding them together. Typically used to aggregate scores across multiple items in a scale for a total score. 
     - Statistical
     - `SUM`
     - SUM(variable_name, variable_name_2, variable_name_3, variable_name_4) 
   * - Participant Mean 
     - Calculates the `mean (average) <https://en.wikipedia.org/wiki/Mean>`_ score across multiple variables for each participant or row of data. Typically used when you have multiple items measuring the same construct and you wish to create a composite score for each participant.
     - Statistical
     - `MEAN`
     - MEAN(variable_name, variable_name_2, variable_name_3, variable_name_4)
   * - Reverse Scoring 
     - To catch `acquiescence response bias <https://en.wikipedia.org/wiki/Acquiescence_bias>`_ (participants who aways agree or disgree in self-report) `reverse-coded items <https://en.wikipedia.org/wiki/Acquiescence_bias>`_ are used, which requires them to be `Reverse Scored <https://en.wikipedia.org/wiki/Acquiescence_bias>`_. Reverse scoring ensures that all items are aligned in the same direction before creating a total or composite score.
     - Custom 
     - Requires manually choosing the maximum value possible value of this item (plus one) and subtract the items score from this value. In this example, we will imagine we have data with a 5-point likert scale. Perhaps we have on item that is reverse coded, so we would create a new transformed variable with the function `6 - $SOURCE` or `6 - variable_name` to reverse code the item.
     - 6 - variable_name
   * - Recoding items (from strings or words into different strings or words).
     - `Recoding <https://en.wikipedia.org/wiki/Data_recode>`_ involves changing the values or strings of a variable based on specified criteria. Recoding items is often used to group categories, create binary variables, or collapse levels in your independent variable for analysis.
     - Custom 
     - Requires manually specifying the recoding criteria using "if then" statements. For example, perhaps you have a column of data indicating the Smoking habits of your participants from Daily, Weekly, Monthly, Occasionally, and Never. Perhaps you want to recode this into a binary variable indicating whether participants are smokers (Daily, Weekly, Monthly) or non-smokers ('Never'). You could use the following: IF(`variable_name` == "Never", "non-smoker", "smoker")
     - IF(`variable_name` == "Never", "non-smoker", "smoker") 
   * - Recoding items (from numbers to strings or words).
     - `Recoding <https://en.wikipedia.org/wiki/Data_recode>`_ involves changing the values or strings of a variable based on specified criteria. Recoding items is often used to group categories, create binary variables, or collapse levels in your independent variable for analysis.
     - Custom 
     - Requires manually specifying the recoding criteria using "if then" statements. For example, perhaps you have a column of data asking participants to rate their pain on a scale from 1 to 5, where 1 is 'no pain' and 5 is 'extreme pain'. You might want to recode these numerical ratings into descriptive categories such as 'low', 'moderate', and 'high' pain levels. You could use the following: IF(variable_name <=2, 'low',IF(variable_name == 3, 'moderate', 'high')). Generally, this kind of complicated recoding (using nested IF statements) is easier done via the `New Transformed Variable` option.
     - IF(variable_name <=2, 'low',IF(variable_name == 3, 'moderate', 'high')). 

       
=================================================
How to turn your data from wide to long format
=================================================

    Placeholder information, more to come...  




   **Topics covered:**
   - stuff
  
  

.. toctree::
   :maxdepth: 1
   

.. ----------------------------------------------------------------------------