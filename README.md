# pivot_table: Pivot Tables For Matlab

## Introduction
This function calculates a [pivot table](https://en.wikipedia.org/wiki/Pivot_table) (similar to those created in Excel, R, or pandas (python) from a matlab [table](http://au.mathworks.com/help/matlab/ref/table.html). In other words, in is able to summarise a large dataset by aggregating it in to groups, and then applying a function to those groups (such as `sum`, `max` etc.)

Pivot tables are an easy and quick way to analyse data. In fact, I would not be surprised if a built-in pivot table function is added to a future Matlab release, in which case this document could easily be out of date and the `pivot_table` function no longer required.

Other pivot table functions exist on the Matlab File Exchange, such as [pivottable](https://au.mathworks.com/matlabcentral/fileexchange/30547-pivottable) and [mat2piv.m](https://au.mathworks.com/matlabcentral/fileexchange/47446-mat2piv-m), but these use cell arrays or other data structures, rather than matlab tables. In my opinion, [tables in Matlab](http://au.mathworks.com/help/matlab/ref/table.html) are the best and most efficient way to process and analyse large datasets which mix different types of data (text, numbers etc.)

## Example

If you have a table in Matlab:

        >> x = table(...
                 {'foo'; 'bar'; 'foo'}, ...
                 [-1; 2; 4], ...
                 'VariableNames', {'Name', 'Value'});

        x =

            Name     Value
            _____    _____

            'foo'    -1
            'bar'     2
            'foo'     4

(*NOTE*: >> above means the Matlab prompt, i.e. you should type or copy & paste what comes after the >> into the prompt.)

Then you can make a pivot table with:

        >> pivot_table(x, 'Name', 'Value', @sum)


        ans =

            Name     sum_of_Value
            _____    ____________

            'bar'    2
            'foo'    3

The format is:

        p = pivot_table(t, aggregate_by, data, function_handle, varargin)

where:
 - `t` is a Matlab table containing the data you wish to turn into a pivot table

 - `aggregate_by` is the name of column in `t` you wish to use to aggregate the data (or a cell array of the columns names, if you wish to aggregate by more than one column).

 - `data` is the name of the column in `t` containing the data you wish to analyse (or a cell array of the column names, if you wish to analyse more than one column).

 - `function_handle` is a handle to the function you wish to use to analyse the data (e.g. @sum, @mean, @max etc.)

## Installation

Download the repository, place it somewhere on your computer, and add the directory which contains `pivot_table.m` to the Matlab path. E.g.:

        >> addpath('C:\Users\foo\Documents\matlab-pivot-table');

## More examples

### Aggregation by more than one column. First, create a table:

        >> x = table(...
            {'foo'; 'bar'; 'foo'; 'foo'}, ...
            {'a'; 'b'; 'c'; 'a'}, ...
            [-1; 2; 4; 7], ...
            'VariableNames', {'Name', 'Letter', 'Value'});

        x =

            Name     Letter    Value
            _____    ______    _____

            'foo'    'a'       -1
            'bar'    'b'        2
            'foo'    'c'        4
            'foo'    'a'        7

Then create the pivot table:

        >> pivot_table(x, {'Name', 'Letter'}, 'Value', @sum)

        p =

            Name     Letter    sum_of_Value
            _____    ______    ____________

            'bar'    'b'       2
            'foo'    'a'       6
            'foo'    'c'       4


## Analyse data from more than one column.
First, create a table:

        >> x = table(...
            {'foo'; 'bar'; 'foo'}, ...
            [-1; 2; 4], ...
            [1; 1; 1], ...
            'VariableNames', {'Name', 'value_1', 'value_2'});

        x =

            Name     value_1    value_2
            _____    _______    _______

            'foo'    -1         1
            'bar'     2         1
            'foo'     4         1

Then, create the pivot table:
        >> p = pivot_table(x, 'Name', {'value_2', 'value_1'}, @sum)

        p =

            Name     sum_of_value_2    sum_of_value_1
            _____    ______________    ______________

            'bar'    1                 2
            'foo'    2                 3

## Tests

`pivot_table.m` comes with a unit testing suite `test_pivot_table.m`. You can use this to verify that the code works on your machine by running `runtests` in Matlab, from inside the directory which contains test_pivot_table.m


## License
Licensed under the MIT license:

    Copyright (c) 2016 Matthew Jeppesen

    Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.


