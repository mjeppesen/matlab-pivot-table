# pivot_table: Pivot Tables For Matlab

## Introduction
This function calculates a [pivot table](https://en.wikipedia.org/wiki/Pivot_table) (similar to those created in Excel, R, or pandas (python) from a matlab [table](http://au.mathworks.com/help/matlab/ref/table.html). In other words, in is able to summarise a large dataset by aggregating it in to groups, and then applying a function to those groups (such as `sum`, `max` etc.)

Pivot tables are an easy and quick way to analyse data. In fact, I would not be surprised if a built-in pivot table function is added to a future Matlab release, in which case this document could easily be out of date and the `pivot_table` function no longer required.

Other pivot table functions exist on the Matlab File Exchange, such as [pivottable](https://au.mathworks.com/matlabcentral/fileexchange/30547-pivottable) and [mat2piv.m](https://au.mathworks.com/matlabcentral/fileexchange/47446-mat2piv-m), but these use cell arrays or other data structures, rather than matlab tables. In my opinion, [tables in Matlab](http://au.mathworks.com/help/matlab/ref/table.html) are the best and most efficient way to process and analyse large datasets which mix different types of data (text, numbers etc.)

## Example

If you have a table in Matlab:

        >> x = table(...
        >>         {'foo'; 'bar'; 'foo'}, ...
        >>         [-1; 2; 4], ...
        >>         'VariableNames', {'Name', 'Value'});

        x =

            Name     Value
            _____    _____

            'foo'    -1
            'bar'     2
            'foo'     4

The you can make a pivot table with:

        p = pivot_table(x, 'Name', 'Value', @sum);


