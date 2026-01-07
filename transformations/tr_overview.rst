.. sectionauthor:: Laiton Hedley 

=========================
Data Manipulation and Transformations Overview
=========================
   The aim of this section is to provide users a short overview of the common data manipulations and transformations avaialble in jamovi.
   This documentation is designed for users who understand their desired manipulation or transformation but are unsure how to perform them using the jamovi software.
   It is assumed that you have already loaded your data into jamovi. If you are unsure how to do this, `here <https://docs.jamovi.org/_pages/um_2_first-steps.html>`_ for help.
   
==================================================================================================
Transformations: Which one should I use? ``New Computed Variable`` vs ``New Transformed Variable``
==================================================================================================

   In jamovi there are two routes to perform a data transformation, if you click on a blank column (or row of a blank column header), you will see above your spread sheet a few options including ``New Computed Variable`` and ``New Transformed Variable`` (the ``New Data Variable`` option allows you to manually input data which we will ignore for now).
   The ``New Computed Variable`` option is best chosen when you're seeking to apply a transformation to a single variable, whereas the ``New Transformed Variable`` option is more suited for applying transformations (and perhaps more complex ones) to multiple variables simultaneously. 
   You would likely prefer to use the ``New Transformed Variable`` option when you have a complex transformation that you'd like to apply to several columns of data. 
   This is made possible because the ``New Transformed Variable`` option also allows for the use of "if then" statements to create more complex transformations and avoid errors. 
   For example, perhaps you would like to apply a logarithmic transformation but want to avoid errors such as attempting to take the logarithm of negative numbers or zero. 
   You could embed an if else statements to avoid taking the logarithm of zeros and recode negative numbers to missing values.
   While it is possible to use the ``New Computed Variable`` option to create similar complex transformations, it can be more time consuming if you have many variables to transform. 
   
   Generally, applying transformations using either way is similar for both options with a minor difference.
   For example, if you wanted to apply a logarithmic 10 transformation to your data, both methods would simply involve calling the `LOG10`` function into the formula editor.
   The difference lies within how you 'call' your `variable` in the formula editor.
   For example, using ``New Computed Variable`` you would simply use the column name of variable, so if your variable is called `score`, you would place the function as `LOG10(score)`.
   In contrast, using ``New Transformed Variable`` you would need instead `$SOURCE` to call the variable, so to apply the same transformation you would call the function as `LOG10($SOURCE)`.
   More information on both the ``New Computed Variable`` and ``New Transformed Variable`` options can be found `here <https://docs.jamovi.org/_pages/um_4_spreadsheet.html>`_ 
   With that out of the way, let's explore some of the common data transformations available in jamovi! 

=============================================
Placeholder Heading Transformation Table..... 
=============================================
+-------------------+-------------------+-------------------+-------------------+
| Transformation    | Definition        | function          | Example           |
+===================+===================+===================+===================+
| z-score           | wewetwetwetwetwetwetewt       | Row 1 Col 3       | Row 1 Col 4       |
+-------------------+-------------------+-------------------+-------------------+
| Row 2 Col 1       | Row 2 Col 2       | Row 2 Col 3       | Row 2 Col 4       |
+-------------------+-------------------+-------------------+-------------------+
| Row 3 Col 1       | Row 3 Col 2       | Row 3 Col 3       | Row 3 Col 4       |
+-------------------+-------------------+-------------------+-------------------+
| Row 4 Col 1       | Row 4 Col 2       | Row 4 Col 3       | Row 4 Col 4       |
+-------------------+-------------------+-------------------+-------------------+
| Row 5 Col 1       | Row 5 Col 2       | Row 5 Col 3       | Row 5 Col 4       |
+-------------------+-------------------+-------------------+-------------------+
| Row 6 Col 1       | Row 6 Col 2       | Row 6 Col 3       | Row 6 Col 4       |
+-------------------+-------------------+-------------------+-------------------+
| Row 7 Col 1       | Row 7 Col 2       | Row 7 Col 3       | Row 7 Col 4       |
+-------------------+-------------------+-------------------+-------------------+
| Row 8 Col 1       | Row 8 Col 2       | Row 8 Col 3       | Row 8 Col 4       |
+-------------------+-------------------+-------------------+-------------------+
| Row 9 Col 1       | Row 9 Col 2       | Row 9 Col 3       | Row 9 Col 4       |
+-------------------+-------------------+-------------------+-------------------+
| Row 10 Col 1      | Row 10 Col 2      | Row 10 Col 3      | Row 10 Col 4      |
+-------------------+-------------------+-------------------+-------------------+
| Row 11 Col 1      | Row 11 Col 2      | Row 11 Col 3      | Row 11 Col 4      |
+-------------------+-------------------+-------------------+-------------------+
| Row 12 Col 1      | Row 12 Col 2      | Row 12 Col 3      | Row 12 Col 4      |
+-------------------+-------------------+-------------------+-------------------+
| Row 13 Col 1      | Row 13 Col 2      | Row 13 Col 3      | Row 13 Col 4      |
+-------------------+-------------------+-------------------+-------------------+
| Row 14 Col 1      | Row 14 Col 2      | Row 14 Col 3      | Row 14 Col 4      |
+-------------------+-------------------+-------------------+-------------------+
| Row 15 Col 1      | Row 15 Col 2      | Row 15 Col 3      | Row 15 Col 4      |
+-------------------+-------------------+-------------------+-------------------+
| Row 16 Col 1      | Row 16 Col 2      | Row 16 Col 3      | Row 16 Col 4      |
+-------------------+-------------------+-------------------+-------------------+
| Row 17 Col 1      | Row 17 Col 2      | Row 17 Col 3      | Row 17 Col 4      |
+-------------------+-------------------+-------------------+-------------------+
| Row 18 Col 1      | Row 18 Col 2      | Row 18 Col 3      | Row 18 Col 4      |
+-------------------+-------------------+-------------------+-------------------+
| Row 19 Col 1      | Row 19 Col 2      | Row 19 Col 3      | Row 19 Col 4      |
+-------------------+-------------------+-------------------+-------------------+
| Row 20 Col 1      | Row 20 Col 2      | Row 20 Col 3      | Row 20 Col 4      |
+-------------------+-------------------+-------------------+-------------------+



.. list-table:: Transformations Summary
   :header-rows: 1

   * - Transformation
     - Definition
     - 
   * - Alice
     - 29
     - Analyst
   * - Bob
     - 34
     - Engineer











----------------------


   **Topics covered:**
   - z-score transformation
   - logarithmic transformation
   - square root transformation

.. toctree::
   :maxdepth: 1
   

.. ----------------------------------------------------------------------------