## sas-course

### create a temporary library 

in order to work with different files we have read and reuse using library
```SAS
libname np xlsx "FILEPATH/np_info.xlsx";
options validvarname=v7;
proc contents data=np.parks;
run;
libname np clear;
```
### Refresh the table with latest data - use replace keyword
```SAS
FILENAME REFFILE '/home/u59515641/EPG1V2/data/storm_damage.tab';

PROC IMPORT DATAFILE=REFFILE
	DBMS=TAB
	OUT=storm_damage_tab replace;
RUN;
```
### Difference between engine and PROC 
![Screenshot from 2021-09-22 19-23-15](https://user-images.githubusercontent.com/33058608/134356915-ff9c89c7-3982-4ae7-83e2-7d2fbb036c05.png)

### querying 
Add a new WHERE statement to print storms that begin with the letter Z. 

```SAS
proc print data=pg1.storm_summary(obs=50);
   *commented WHERE statements;
   where name like "Z%";
run;
```
### Macro Variables 

```SAS
%LET macro_variable=value;
*how to use;
&macro_variable
```

### Common Summary Functions for Creating Columns
SAS has a collection of summary functions that calculate summary statistics. Each of these functions can have an unlimited number of arguments, and each argument is either a numeric constant or numeric column in the data. The function calculates the summary statistic from the values of the arguments for each row in the data.  

For these summary functions, if any of the input values are missing, the missing value or values are ignored, and the calculation is based on the known values.

Common Numeric Functions |What it Does

SUM (num1, num2, ...)    |Returns the sum of nonmissing arguments.

MEAN (num1, num2, ...)

Returns the arithmetic mean (average) of nonmissing arguments.

MEDIAN (num1, num2, ...)

Returns the median value of nonmissing arguments.

RANGE (num1, num2, ...)

Returns the range of the nonmissing values.

MIN (num1, num2, ...)

Returns the smallest nonmissing value from a list of arguments.

MAX (num1, num2, ...)

Returns the largest value from a list of arguments.

N (num1, num2, ...)

Returns the number of nonmissing numeric values.

NMISS (num1, num2, ...)

Returns the number of null and SAS missing numeric values. 
