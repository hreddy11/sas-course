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


### Common Character Functions for Creating Columns
SAS has many functions you can use to manipulate character columns. The arguments include one or more character columns in your data. These are a few of the many character functions you can use: 

Character Function

What it Does

UPCASE (char)  LOWCASE(char) 

Changes letters in a character string to uppercase or lowercase

PROPCASE (char,<delimiters>) 

Changes the first letter of each word to uppercase and other letters to lowercase

CATS (char1, char2, ...)

Concatenates character strings and removes leading and trailing blanks from each argument

SUBSTR (char, position, <length>)

Returns a substring from a character string

	
### Common Date Functions for Creating Columns
SAS date functions are incredibly helpful for creating and manipulating SAS dates.  

These functions extract information from the SAS date column or value provided in the argument:

Date Function

What it Does

MONTH (SAS-date)

 Returns a number from 1 through 12 that represents the month

YEAR (SAS-date)

 Returns the four-digit year

DAY (SAS-date)

 Returns a number from 1 through 31 that represents the day of the month

WEEKDAY (SAS-date)

 Returns a number from 1 through 7 that represents the day of the week (Sunday=1)

QTR (SAS-date)

 Returns a number from 1 through 4 that represents the quarter

These functions enable you to create SAS date values from the arguments.

 

Date Function

What it Does

TODAY () 

Returns the current date as a numeric SAS date value (no argument is required because the function reads the system clock)

MDY (month, day, year)

 Returns a SAS date value from numeric month, day, and year values

YRDIF (startdate, enddate, 'AGE')

 Calculates a precise age between two dates


### Using Numeric Functions to Change Precision
These functions can be used to truncate decimal values.

Function

What it Does

CEIL (number)

Returns the smallest integer that is greater than or equal to the argument.

FLOOR (number)

Returns the largest integer that is less than or equal to the argument.

INT (number)

Returns the integer value.

	
### Removing Characters from a String
These functions can be used to remove characters from a string.

Function

What it Does

COMPBL (string)

Returns a character string with all multiple blanks in the source string converted to single blanks.

COMPRESS (string <, characters>)

 Returns a character string with specified characters removed from the source string.

STRIP (string)

Returns a character string with leading and trailing blanks removed.
	
	
### Identifying Character Positions
These functions return a numeric value that identifies the location of selected characters

Function

What it Does

LENGTH (string)

Returns the length of a non-blank character string, excluding trailing blanks; returns 1 for a completely blank string.

ANYDIGIT (string)

Returns the first position at which a digit is found in the string.

ANYALPHA (string)

Returns the first position at which an alpha character is found in the string.

ANYPUNCT (string)

Returns the first position at which punctuation character is found in the string.
	
	
### Building Character Strings
These functions can be used to combine strings into a single character value. The arguments can be either character or standard numeric values.

Function

What it Does

CAT (string1, ... stringn)

Concatenates strings together, does not remove leading or trailing blanks.

CATS (string1, ... stringn)

Concatenates strings together, removes leading or trailing blanks from each string.

CATX ('delimiter', string1, ... stringn)

Concatenates strings together, removes leading or trailing blanks from each string, and inserts the delimiter between each string.
