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
