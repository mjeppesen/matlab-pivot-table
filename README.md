# pivot_table: Pivot Tables For Matlab

## Introduction
This function calculates a [pivot table](https://en.wikipedia.org/wiki/Pivot_table) (similar to those created in Excel, R, or pandas (python) from a matlab [table](http://au.mathworks.com/help/matlab/ref/table.html). In other words, in is able to summarise a large dataset by aggregating it in to groups, and then applying a function to those groups (such as `sum`, `max` etc.)

Pivot tables are an easy and quick way to analyse data, and the lack of  built-in pivot table function in matlab makes it harder to use as a data analysis language. It is such a serious omission, that I expect it will be added in a future release, which means this document could easily be out of date and the `pivot_table` function no longer required.

Other pivot table functions exist on the Matlab File Exchange, such as [pivottable](https://au.mathworks.com/matlabcentral/fileexchange/30547-pivottable) and [mat2piv.m](https://au.mathworks.com/matlabcentral/fileexchange/47446-mat2piv-m), but these use cell arrays or other data structures, rather than matlab tables. In my opinion, [tables in Matlab](http://au.mathworks.com/help/matlab/ref/table.html) are the best and most efficient way to process and analyse large datasets which mix different types of data (text, numbers etc.)

## Usage

