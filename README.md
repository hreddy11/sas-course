## sas-course

###create a temporary library 

in order to work with different files we have read and reuse using library
```SAS
libname np xlsx "FILEPATH/np_info.xlsx";
options validvarname=v7;
proc contents data=np.parks;
run;
libname np clear;
```
