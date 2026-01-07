.. sectionauthor:: Laiton Hedley 

==========================
z-score Transformation
==========================

| To perform a z-score transformation in jamovi, you should already have your data loaded into jamovi. 
If you do not have your own data and are looking for a sample dataset, you can use the built-in datasets available in jamovi. 
The example data set can be found by clicking the three horizontal lines in the top left corner of jamovi, selecting ``Open``, and then ``Built-in library``.
   | In the formula editor, you can use the ``ZSCORE()`` function to calculate z-scores for a variable.
   | For example, to calculate z-scores for the variable ``score``, enter:

   .. code-block:: text

      ZSCORE(score)

   | You can give the new variable a name, such as ``score_z``.

-  | The z-score transformation standardizes your variable, so it has a mean of 0 and a standard deviation of 1.
   | This is useful for comparing variables measured on different scales.



.. ----------------------------------------------------------------------------
