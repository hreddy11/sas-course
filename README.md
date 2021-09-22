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
