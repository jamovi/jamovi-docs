.. sectionauthor:: Laiton Hedley

========
Overview
========

    When analysing data, it is common for data to come in in a somewhat messy format. It's often necessary to "tidy" and transform our data so that it is in a form suitable for our analyses. This may involve computing sum scores for each partipant, excluding outliers, recoding responses, transforming response variables to different scales, aggregation (such as computing mean response time for each participant), etc.

    The following describes the various data manipulation and transformation facilities that jamovi provides.

==============
Data Variables
==============

    - Setting data type and measure type
    - Missing values
    - Adding labels to levels
    - Reordering levels
    - 'Retain unused levels in analyses'
    - Some existing content https://www.jamovi.org/user-manual.html#data-variables

==================
Computed Variables
==================

    Computed variables allow us to compute a new column of values, (typically) using values from the existing columns. For example, a computed column might provide z-scores for a particular column in the data set, or it might compute a sum for participant responses to survey questions.

    Values are computed using simple formulas such as:

        Z(response)

        Q1 + Q2 + Q3 + Q4

    where ``response``, and ``Q1`` .. ``Q4`` refer to existing columns in the data set.

    The simplest way to add a new computed variable to a data set is to select the ``Add`` (variable) button from the ``Data`` tab. Selecting ``Append`` under ``Computed variables`` will add a new computed column to the very right of the data set. To configure the computed variable, select either ``Setup`` from the ``Data`` tab, or double click on the column header. This will present you with the variable editor which looks as follows (for computed variables).

    |computed_screenshot|

    Here you can name the new column, and add a description if you desire. Selecting the small fx button will bring down a list of the functions available, and a list of variables you can use to compose your formula. It's possible to construct your formula simply by typing directly into the formula box, or by selecting the formulas and variables from the lists and double-clicking them to insert them.

    A number of functions are available. See :ref:`list-of-functions` for details.

    Computed variables are ideal for one-off computations, but where the same computation needs to be applied many times across many columns (For example, reverse scoring a number of responses), creating a computed variable for each column becomes tedious. In contrast, ``Transformed variables`` allow for the same transform to be applied across any number of columns. Further, transformed variables are ideal for "if-then" recoding of variables.

=====================
Transformed Variables
=====================

    ``Transformed variables`` are better suited for more complex transformations (such as reverse scoring and recoding variables) and allow the same transform to be applied across multiple columns of data.
    To add a new transformed variable to a data set, select the ``Add`` (variable) button from the ``Data`` tab.  Under ``Transformed Variable`` select ``Append``, this will add a new Transformed column to the very right of the data set. To configure the Transformed variable, select either ``Setup`` from the ``Data`` tab, or double click on the column header. This will present you with the variable editor which looks like this:

    |Transformed_Variable|

    Here you can name the new column, and add a description of the transformation - this can be helpful if you wish to use the same transformation multiple times. To perform the transformation, we select the ``Source variable``, that is the column of data to transform.
    Additionally, you must select ``using transform``, which allows you to either select an existing transformation, or create a new one by selecting ``Create New Transform...``.
    When creating a new transformation, you will be presented with a formula editor (like the computed variables option).
    Here you can enter the formula for your transformation, using the ``$source`` variable to refer to the source variable you selected earlier.

    For example, we may have a survey item that needs to be reversed score, using the ``New Transformed Variable`` option, you could create a new transformation with the formula:

      ``7 - $source``

    In this example, ``$source`` would be item_3 and we are assuming a 6-point Likert scale (hence the 7 minus):

    We should yield results where 6 becomes 1, 5 becomes 2, 4 becomes 3, and so on:

    .. list-table:: Example of Reverse Scoring
       :header-rows: 1

       * - Item_1
         - Item_2
         - Item_3
         - 7 - $source
       * - 4
         - 3
         - 3
         - 4
       * - 3
         - 4
         - 6
         - 1
       * - 4
         - 4
         - 2
         - 5

    Once created, this transformation can be applied across any number of such variables (such as items_1, items_2, and so on) -- we will explore this shortly.

Recoding Variables
------------------

    *Transformed variables* are also ideal for recoding variables, i.e., recoding ``1-4`` and ``5-10`` cigarettes per day to ``Smoker`` and ``0`` cigarettes per day to ``Non-smoker``, or recoding values greater than or equal to 85 as a ``High Distinction``, greater than 75 as a ``Distinction``, etc.
    Recoding is performed by adding recode conditions with the ``Add recode condition`` button. Each recode condition is made up of a condition, i.e. ``$source == '1-4'``, or ``$source >= 85``, and a value to use if that condition is true, i.e. ``'Smoker'``, ``'High Distinction'``

    See the following example:

    |Recode_Variable|

    Adding the additional conditions for the C and P grades would result in a transformed variable that would perform the following recoding.

    .. list-table:: Example of Recoding
       :header-rows: 1

       * - Exam Score
         - Grade
       * - 50
         - P
       * - 90
         - HD
       * - 44
         - F
       * - 76
         - D
       * - 66
         - C

    Note that when evaluating recode conditions, jamovi evaluates each condition one after another, and uses the value from the first condition that resolves to be true. In the above example, this allowed us to express the ``Distinction`` condition as ``$source >= 75``, rather than the longer ``$source < 85 and $source >= 75``. Values greater or equal to 85 will already been taken care of by the first condition.

Transforming Multiple Variables
-------------------------------

There are situations where we need to transform multiple varibles. For example, there may be a number of items in our survey data set which need to be reverse scored. To save the need for creating each individual transformed variable, one after another, jamovi allows for multiple transformed variables to be created in a single step.

In this approach, select the variables to transform (either by holding down ctrl or ⌘ and clicking the colum headers, or selecting multiple variables under the ``Variables`` tab), and then select ``Transform`` from the ``Data`` tab. For each variable selected, a matching transformed variable will created, with the ``Source variable`` set accordingly. This allows you to define a single transform, and apply it across multiple variables at once.

===================
Row and V Functions
===================

Functions in jamovi can be either *Row functions* or *Variable functions*.

Row Functions
-------------

*Row functions* only make use of other values in the same row. For example, the function ``MEAN(A, B, C)`` will result in a column of values where each cell's value is only computed from the values in its row.

.. list-table:: Example of the MEAN() Function
   :header-rows: 1

   * - A
     - B
     - C
     - MEAN(A, B, C)
   * - 1
     - 3
     - 4
     - 2.33
   * - 6
     - 3
     - 1
     - 3.33
   * - 5
     - 5
     - 9
     - 6.33

V Functions
-----------

*V functions* or *Variable functions* (typically prefixed with the letter ``V``), compute values using the entire variable. For example, ``VMEAN(A)`` computes the mean of the *entire* variable ``A``.

.. list-table:: Example of the VMEAN() Function
   :header-rows: 1

   * - A
     - B
     - C
     - VMEAN(A)
   * - 1
     - 3
     - 4
     - 4
   * - 6
     - 3
     - 1
     - 4
   * - 5
     - 5
     - 9
     - 4

It's possible to combine Row and V functions together. For example, to compute a z-score, we might use the function

  ``(A - VMEAN(A)) / VSTDEV(A)``

(but it's also possible to use the more concise ``Z(...)`` function!)

Grouping with V Functions
-------------------------

Several V functions allow a ``group_by`` parameter, allowing the calculation of values within groups.
Perhaps you have a dataset with a column labelled Dosage to indicate the treatment each participant recieved, say 50mgs vs 100mgs vs 150mgs.
You'd likely wish to compute the mean score of some outcome variable for each Dosage group separately (without the scores from one treatment being combined with those from another).
This is made possible by calling the VMEAN function with the ``group_by`` argument:

  ``VMEAN(outcome, group_by = Dosage)``

.. list-table:: Example of the VMEAN() Function with group_by argument
   :header-rows: 1

   * - Dosage
     - outcome
     - VMEAN(outcome, group_by = Dosage)
   * - 150mgs
     - 4
     - 4.33
   * - 150mgs
     - 4
     - 4.33
   * - 150mgs
     - 5
     - 4.33
   * - 100mgs
     - 3
     - 3
   * - 100mgs
     - 2
     - 3
   * - 100mgs
     - 4
     - 3
   * - 50mgs
     - 1
     - 1.33
   * - 50mgs
     - 2
     - 1.33
   * - 50mgs
     - 1
     - 1.33

.. _list-of-functions:

====================
⚡ List of Functions
====================

.. list-table:: Functions available in jamovi
   :header-rows: 1
   :widths: 30 50 20

   * - Function
     - Description
     -
   * - ``Z(var)``
     - z-score: the number of standard deviations a raw value is from the overall mean.
     - `More info <https://en.wikipedia.org/wiki/Standard_score>`__
   * - ``ABSZ(var)``
     - short-hand for ``ABS(Z(var))``
     -
   * - ``SCALE(var)``
     - synonym for ``Z()``
     -
   * - ``LN(var)``
     - Natural logarithm (base *e*): the natural logarithm (base e) of each value in a column of data.
     - `More info <https://doi.org/10.1177/00045632211050531>`__
   * - ``LOG10(var)``
     - Log base 10: the logarithm (base 10) of each value in a column of data.
     - `More info <https://doi.org/10.1177/00045632211050531>`__
   * - ``SQRT(var)``
     - Square root: the square root of each value in a column of data.
     - `More info <https://en.wikipedia.org/wiki/Square_root>`__
   * - ``EXP(var)``
     - Exponential: raises *e* to the power of each value in a column of data.
     - `More info <https://en.wikipedia.org/wiki/Exponential_function>`__
   * - ``ABS(var)``
     - Absolute value: converts all negative values in a column of data to their positive counterparts, while leaving positive values unchanged.
     - `More info <https://en.wikipedia.org/wiki/Absolute_value>`__
   * - ``ROUND(var, n)``
     - Rounding: adjusts each value in a column of data to a specified number of decimal places or to the nearest whole number.
     - `More info <https://en.wikipedia.org/wiki/Rounding>`__
   * - ``RANK(var)``
     - Ranking: assigns an ordinal rank to each value in a column of data based on its position relative to other values.
     - `More info <https://en.wikipedia.org/wiki/Ranking_(statistics)>`__
   * - ``FLOOR(var)``
     - Floor: returns the greatest integer that is less than each value in a column of data, effectively rounding down to the nearest whole number.
     - `More info <https://en.wikipedia.org/wiki/Floor_and_ceiling_functions>`__
   * - ``CEILING(var)``
     - Ceiling: returns the smallest integer that is greater than or equal to each value in a column of data, effectively rounding up to the nearest whole number.
     - `More info <https://en.wikipedia.org/wiki/Floor_and_ceiling_functions>`__
   * - | ``MIN(var)``
       | ``VMIN(var)``
     - Minimum: identifies the lowest value in a row or column of data.
     - `More info <https://en.wikipedia.org/wiki/Maximum_and_minimum>`__
   * - | ``MAX(var)``
       | ``VMAX(var)``
     - Maximum: identifies the highest value in a row or column of data.
     - `More info <https://en.wikipedia.org/wiki/Maximum_and_minimum>`__
   * - ``STDEV(var1, var2, ...)``
     - Standard deviation: measures the amount of variation in a set of values.
     - `More info <https://en.wikipedia.org/wiki/Standard_deviation>`__
   * - ``SUM(var1, var2, ...)``
     - Summation: calculates the total of items (or columns of data) by adding them together.
     - `More info <https://en.wikipedia.org/wiki/Summation>`__
   * - ``MEAN(var1, var2, ...)``
     - Participant Mean: Calculates the mean score across multiple variables for each participant or row of data.
     - `More info <https://en.wikipedia.org/wiki/Mean>`__

Understanding Formulas
----------------------

 - numbers are numbers
 - labels or text surrounded by backticks refer to variables
 - values surrounded by quotes are text values
 - adding two numbers together performs arithmetic
 - adding two text values together performs concatenation
 - adding a number and a text value together, results in the number being converted to text
 - ``and`` and ``or``

==============
Filtering Data
==============

Introduce general principles of filtering data

... and why you can't use *V functions* in filters (sad face) (we'll need to link to this explanation)

==================
Restructuring Data
==================

Restructuring data in jamovi (at this time) is provided by the jReshape and jTransform modules.

===================
Common Data Recipes
===================

Excluding outliers
Reverse scoring survey items
Computing a sum score (say an extraversion questionaire)
Recoding a continuous variable to categories
Recoding/reducing the number of categories
Split by functionality (jamovi does this poorly)
Analysing a subset of data
String concatenation



.. .. list-table:: Transformations Easily Accesible in jamovi
..    :header-rows: 1

..    * - Transformation
..      - Definition
..      - Found Under
..      - Function in jamovi
..      - Example Use Case
..    * - z-score (standard score) so scale and z do the same thing - why do we have both in jamovi?
..      -  A `z-score <https://en.wikipedia.org/wiki/Standard_score>`_ (or standard score) is the number of standard deviations a raw value is from the overall mean of the variable being measured. The z-score transformation standardises your variable, so it has a mean of 0 and a standard deviation of 1.
..      - Statistical
..      - `Z`
..      - Z(variable_name)
..    * - Standard score (z-score) Do we even want this? - we already have z-score...?
..      -  A `z-score <https://en.wikipedia.org/wiki/Standard_score>`_ or standard score is the number of standard deviations a raw value is from the overall mean of the variable being measured. The z-score transformation standardises your variable, so it has a mean of 0 and a standard deviation of 1.
..      - Statistical
..      - `SCALE`
..      - SCALE(variable_name)
..    * - Logarithmic 10
..      - `Logarithmic 10 <https://doi.org/10.1177/00045632211050531>`_ transformation involves taking the logarithm of each value in a dataset to compress large numbers and expand small numbers.
..      - Math
..      - `LOG10`
..      - LOG10(variable_name)
..    * - Natural Logarithmic
..      -  A `Natural Logarithmic <https://doi.org/10.1177/00045632211050531>`_ transformation involves taking the natural logarithm (base e) of each value in a dataset, similarly to the logarithmic 10 transformation it is used to reduce right skewness, stabilise variance, and make data more normally distributed.
..      - Math
..      - `LN`
..      - LN(variable_name)
..    * - Square Root
..      - A `Square Root <https://en.wikipedia.org/wiki/Square_root>`_ transformation takes the square root of a variable. This transformation is often used on non-negative count data to reduce right skewness, stabilise variance, and ensure the data is normally distributed.
..      - Math
..      - `SQRT`
..      - SQRT(variable_name)
..    * - Exponential
..      - An `exponential <https://en.wikipedia.org/wiki/Exponential_function>`_ transformation raises a constant (often e or 10) to the power of each value, which turns differences in the original variable into multiplicative changes. Small increases become much larger on the transformed scale, and larger values are amplified the most.
..      - Math
..      - `EXP`
..      - EXP(variable_name)
..    * - Box-Cox
..      - A `Box–Cox transformation <https://en.wikipedia.org/wiki/Power_transform#Box%E2%80%93Cox_transformation>`_ finds an exponent (λ) to make the distribution of your data closer to normal and make it's variance more stable; it can only be used for positive continuous data typically when the data are skewed or show non-constant spread.
..      - Statistical
..      - `BOXCOX`
..      - BOXCOX(variable_name)
..    * - Interquartile Range
..      - The Interquartile Range tells you how spread out the middle 50% of your data is by calculating Q3 minus Q1. It is useful because it can help flag unusually low or high scores using the common boxplot rule of values below Q1 minus 1.5 times the IQR or above Q3 plus 1.5 times the IQR.
..      - Statistical
..      - `IQR`
..      - IQR(variable_name)
..    * - Ranking
..      - `Ranking <https://en.wikipedia.org/wiki/Ranking_(statistics)>`_ assigns an ordinal rank to each value in a dataset based on its position relative to other values. The smallest value receives the rank of 1, the next smallest receives rank 2, and so on. This transformation is useful for non-parametric analyses or when you want to focus on the order of values rather than their actual magnitudes.
..      - Statistical
..      - `Rank`
..      - RANK(variable_name)
..    * - Rounding
..      - `Rounding <https://en.wikipedia.org/wiki/Rounding>`_ a variable involves adjusting each value to a specified number of decimal places or to the nearest whole number. This transformation is often used to simplify data presentation, reduce precision for reporting purposes, or prepare data for certain analyses that require integer values.
..      - Statistical
..      - `ROUND` Note that the 3 in the example use case rounds `variable_name` to 3 decimal places. This can be adjusted to say 1 or 2 for 1 or 2 decimal places respectively, or to 0 for whole numbers.
..      - ROUND(variable_name, 3)
..    * - Absolute
..      - Taking the `absolute value <https://en.wikipedia.org/wiki/Absolute_value>`_ simply converting all negative values in a dataset to their positive counterparts, while leaving positive values unchanged. This transformation is often used to focus on the magnitude of values without regard to their direction (ignoring whether values are positive or negative).
..      - Math
..      - `ABS`
..      - ABS(variable_name)
..    * - Absolute Interquartile Range
..      - The Absolute Interquartile Range tells you how spread out the middle 50% of your data is by calculating Q3 minus Q1. It is useful because it can help flag unusually low or high scores using the common boxplot rule of values below Q1 minus 1.5 times the IQR or above Q3 plus 1.5 times the IQR.
..      - Statistical
..      - `ABSIQR`
..      - ABSIQR(variable_name)
..    * - Absolute z-score (or Absolute standard score)
..      - The number of absolute standard deviations a raw value is from the overall mean of the variable being measured. The z-score transformation standardises your variable, so it has a mean of 0 and a standard deviation of 1, the absolute z-score takes the absolute value of this transformation ignoring the sign.
..      - Statistical
..      - `ABSZ`
..      - ABSZ(variable_name)
..    * - Floor
..      - The `Floor <https://en.wikipedia.org/wiki/Floor_and_ceiling_functions>`_  function essentially takes a real number and returns the greatest integer that is less than that number, effectively rounding down to the nearest whole number.
..      - Statistical
..      - `FLOOR`
..      - FLOOR(variable_name)
..    * - Ceiling
..      - The `Ceiling <https://en.wikipedia.org/wiki/Floor_and_ceiling_functions>`_ function takes a real number and returns the smallest integer that is greater than or equal to that number, effectively rounding up to the nearest whole number.
..      - Statistical
..      - `CEILING`
..      - CEILING(variable_name)
..    * - Mininum
..      - `Mininum or Min values <https://en.wikipedia.org/wiki/Maximum_and_minimum>`_ are the lowest values in a row or column of data, this transformation can be used when you want to identify the highest score across multiple variables for each participant or row of data.
..      - Statistical
..      - `MIN`
..      - MIN(variable_name, variable_name_2)
..    * - Maximum
..      - `Maximum or Max values <https://en.wikipedia.org/wiki/Maximum_and_minimum>`_ are simply the highest values in a row or column of data, this transformation can be used when you want to identify the highest score across multiple variables for each participant or row of data.
..      - Statistical
..      - `MAX`
..      - MAX(variable_name, variable_name_2, variable_name_3)
..    * - Standard deviation
..      - `Standard deviation <https://en.wikipedia.org/wiki/Standard_deviation>`_ is a measure of the amount of variation or dispersion in a set of values. A low standard deviation indicates that the values tend to be close to the mean (average) of the set, while a high standard deviation indicates that the values are spread out over a wider range.
..      - Statistical
..      - `STDEV`
..      - STDEV(variable_name, variable_name_2)
..    * - Summation
..      - `Summation or Sum <https://en.wikipedia.org/wiki/Summation>`_ calculates the total of items (or columns of data) by adding them together. Typically used to aggregate scores across multiple items in a scale for a total score.
..      - Statistical
..      - `SUM`
..      - SUM(variable_name, variable_name_2, variable_name_3, variable_name_4)
..    * - Participant Mean
..      - Calculates the `mean (average) <https://en.wikipedia.org/wiki/Mean>`_ score across multiple variables for each participant or row of data. Typically used when you have multiple items measuring the same construct and you wish to create a composite score for each participant.
..      - Statistical
..      - `MEAN`
..      - MEAN(variable_name, variable_name_2, variable_name_3, variable_name_4)
..    * - Reverse Scoring
..      - To catch `acquiescence response bias <https://en.wikipedia.org/wiki/Acquiescence_bias>`_ (participants who aways agree or disgree in self-report) `reverse-coded items <https://en.wikipedia.org/wiki/Acquiescence_bias>`_ are used, which requires them to be `Reverse Scored <https://en.wikipedia.org/wiki/Acquiescence_bias>`_. Reverse scoring ensures that all items are aligned in the same direction before creating a total or composite score.
..      - Custom
..      - Requires manually choosing the maximum value possible value of this item (plus one) and subtract the items score from this value. In this example, we will imagine we have data with a 5-point likert scale. Perhaps we have on item that is reverse coded, so we would create a new transformed variable with the function `6 - $source` or `6 - variable_name` to reverse code the item.
..      - 6 - variable_name
..    * - Recoding items (from strings or words into different strings or words).
..      - `Recoding <https://en.wikipedia.org/wiki/Data_recode>`_ involves changing the values or strings of a variable based on specified criteria. Recoding items is often used to group categories, create binary variables, or collapse levels in your independent variable for analysis.
..      - Custom
..      - Requires manually specifying the recoding criteria using "if then" statements. For example, perhaps you have a column of data indicating the Smoking habits of your participants from Daily, Weekly, Monthly, Occasionally, and Never. Perhaps you want to recode this into a binary variable indicating whether participants are smokers (Daily, Weekly, Monthly) or non-smokers ('Never'). You could use the following: IF(`variable_name` == "Never", "non-smoker", "smoker")
..      - IF(`variable_name` == "Never", "non-smoker", "smoker")
..    * - Recoding items (from numbers to strings or words).
..      - `Recoding <https://en.wikipedia.org/wiki/Data_recode>`_ involves changing the values or strings of a variable based on specified criteria. Recoding items is often used to group categories, create binary variables, or collapse levels in your independent variable for analysis.
..      - Custom
..      - Requires manually specifying the recoding criteria using "if then" statements. For example, perhaps you have a column of data asking participants to rate their pain on a scale from 1 to 5, where 1 is 'no pain' and 5 is 'extreme pain'. You might want to recode these numerical ratings into descriptive categories such as 'low', 'moderate', and 'high' pain levels. You could use the following: IF(variable_name <=2, 'low',IF(variable_name == 3, 'moderate', 'high')). Generally, this kind of complicated recoding (using nested IF statements) is easier done via the `New Transformed Variable` option.
..      - IF(variable_name <=2, 'low',IF(variable_name == 3, 'moderate', 'high')).


..     In jamovi there are two main routes to perform manipulations and transformations of data; ``Computed variables`` and ``Transformed variables``.
..     ``Computed variables`` are the simpler of the two, and are best when you want to manipulate or transform a single column of data (or generate a simulated column of data), where as


..     Using the ``New Computed Variable`` option, you could use the following::

..         IF(`variable_name` == "Never", "non-smoker", "smoker")

..     This would create a new column with the values recoded as smoker and non-smoker.
..     In contrast, using the ``New Transformed Variable`` option, you would click ``Source variable`` and select `variable_name`.
..     Then click ``using transform``, followed by ``create new``.
..     Next to the plus symbol, click ``Add recode condition``.
..     This allows you to recode your variable using the same if/then logic in a more user-friendly way.
..     Additionally, this same manipulation can be saved for later if you have a similar column of data to recode.
..     The same applies for transformations: the ``New Transformed Variable`` option allows you to save and re-apply the same transformation to additional columns seamlessly.

..     More information on both the ``New Computed Variable`` and ``New Transformed Variable`` options can be found `here <https://docs.jamovi.org/_pages/um_4_spreadsheet.html>`_.
..     For additional information on the ``New Transformed Variable`` option (especially for transforming multiple variables), see this `blog post <https://blog.jamovi.org/index.php/2021/08/12/transforming-multiple-variables-in-jamovi/>`_.
..     With that out of the way,
 below are more details on the common manipulations and transformations made accessible in jamovi.

.. ===========================================================
.. Common Data Manipulations and Transformations using jamovi
.. ===========================================================
..     Below we provide a summary table of the common data manipulations and transformations made possible using jamovi.
..     We provide a brief definition of each manipulation and transformation, where to find it in jamovi (or if it requires custom inputs), the function to be called, and an example use case of this function.
..     For each use case we have used 'variable_name' as a placeholder for the name of your variable or column of data.
..     At times, you may want to use multiple columns of data within a manipulation or transformation, such as calculating the participant's mean or the summation across a range of scale items.
..     Therefore, in the example use cases below we will refer to additional columns of data as 'variable_name_2', 'variable_name_3' and so on.
..     Hopefully your naming conventions are better than ours, but at least this should make the example use cases clear and easy to follow.

..     Below, we provide a summary table of common data manipulations and transformations available in jamovi.
..     For each manipulation or transformation, we include a brief definition, where to find it in jamovi (or whether it requires custom input), the function to call, and an example use case.
..     In each use case, we use `variable_name` as a placeholder for the name of your variable (i.e., your column of data).
..     Sometimes you may want to use multiple columns within a single manipulation or transformation, such as calculating across a set of scale items each participant's mean or their summed scores.
..     For this reason, the example use cases below refer to additional columns as `variable_name_2`, `variable_name_3`, and so on.
..     Hopefully your naming conventions are better than ours, but this should keep the examples clear and easy to follow.

.. =================================================
.. How to turn your data from wide to long format
.. =================================================

..     Placeholder information, more to come...



.. toctree::
   :maxdepth: 1


.. ----------------------------------------------------------------------------


.. |computed_screenshot| image:: ../_images/tr_compute_variable.png
  :alt: Example transformation variable editor using the computed variable option.
  :class: centered
  :width: 37%

.. |Reverse_Score| image:: /_images/tr_reverse_score_likert.png
  :alt: How to reverse score a likert item using the transformed variable option.
  :class: centered
  :width: 37%


.. |Transformed_Variable| image:: /_images/tr_transformed_variable.png
  :alt: Example transformation variable editor using the transformed variable option.
  :class: centered
  :width: 37%


.. |Recode_Variable| image:: /_images/tr_transform_recode.png
  :alt: How to recode a variable using the transformed variable option.
  :class: centered
  :width: 37%
