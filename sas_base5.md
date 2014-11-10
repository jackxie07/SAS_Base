sas_base5.markdown

# Chapter 5: Creating SAS Data Sets from Raw Data

## 1. Overview
### [1]Introduction
This shows you how to design the write a DATA step program to create a SAS data set from raw data that is stored in an external file. It also shows how to read data from a SAS data set and write observations out to a raw data file.

### [2]Objectives
* reference a SAS library
* reference a raw data file
* name a SAS data set to be created
* specify a raw data file to be read
* read standard character and numeric values in fixed fields
* create new variables and assign values
* select observations based on conditions
* read instream data
* submit and verify a DATA step program
* read a SAS data set and write the observations out to a raw data file


## 2. Raw Data Files
A raw data file is an external text file whose records contain data values that are organized in fields.

|Field Name|Starting Column|Ending Column|Description of Field|
|---|---|---|---|
|`ID`|1|4|patient ID number|
|`Name`|6|25|patient name|
|`ResHR`|27|29|resting heart rate|
|`MaxHR`|31|33|maximum heart rate during test|
|`RecHR`|35|37|recovery heart rate after test|
|`TimeMin`|39|40|time, complete minutes|
|`TimeSec`|42|43|time, seconds|
|`Tolerance`|45|45|comparison of stress test tolerance between this test and the last test(I=increased, D=decreased, S=same, N=no previous test)|

## 3. Steps to Create a SAS Data Set
Before reading the raw data from the file, you must first reference the SAS library in which you will store the data set. Then you can write a DATA step program to read the raw data file and create a SAS data set.

To read the raw data file, the DATA step must provide the following instructions to SAS:
* the location or name of the external text file
* a name for the new SAS data set
* a reference that identifies the external file
* a description of the data values to be read

After using the DATA step to read the raw data, you can use a PROC PRINT step to produce a list report that displays the data values that are in the new data set.

|To Do This|Use This SAS Statement|
|---|---|
|Reference a SAS data library|`LIBNAME` statement|
|Reference an external file|`FILENAME` statement|
|Name a SAS data set|`DATA` statement|
|Identify an external file|`INFILE` statement|
|Describe data|`INPUT` statement|
|Execute the DATA step|`RUN` statement|
|List the data|`PROC PRINT` statement|
|Execute the final program step|`RUN` statement|

## 4. Referencing a SAS Library
### Using a LIBNAME Statement
```sas
libname taxes 'c:\users\acct\qtr1\report';
```

## 5. Referencing a Raw Data File
### [1]Using a FILENAME Statement
Defining a Fully Qualified Filename:
```sas
filename tests 'c:\users\tmill.dat';
```

Defining an Aggregate Storage Location:
```sas
filename finance 'c:\users\personal\finances';
```

### [2]Referencing a Fully Qualified Filename
When you associate a fileref with an individual external file, you specify the fileref in subsequent SAS statements and commands.
```sas
data clinic.therapy;
	infile exercises;
	input Name $ City $ Age Sex Height;
run;
```

### [3]Referencing a File in an Aggregate Storage Location
To reference an external file with a fileref that points to an aggregate storage location, you specify the fileref followed by the individual filename in parentheses:
```sas
data clinic.therapy;
	infile tax(refund.dat);
	input Name $ Dept $ Site $;
run;
```

## 6. Writing a DATA Step Program
### [1]Naming the Data Set
The DATA statement indicates the beginning of the DATA step and names the SAS data set to be created.

### [2]Specifying the Raw Data File
When reading raw data, use he INFILE statement to indicate which file the data is in.
```sas
infile tests;
```
```sas
infile 'c:\irs\personal\refund.dat';
```

### [3]Column Input
When you use column input, your data must be:
* standard character or numeric values
* in fixed fields

#### Standard and non-standard numeric data
### [4]Describing the Data


## 7. Submitting the DATA Step Program
### [1]Verifying the Data
### [2]Checking DATA Step Processing
### [3]Listing the Data Set
### [4]Reading the Entire Raw Data Files
### [5]Invalid Data


## 8. Creating and Modifying Variables
### [1]SAS Expressions
### [2]Using Operators in SAS Expressions
### [3]More Examples of Assignment Statements
### [4]Data Constants


## 9. Subsetting Data



## 10. Reading Instream Data
### Example


## 11. Steps to Create a Raw Data File
### [1]Using the _NULL_ Keyword
### [2]Specifying the Raw Data File
### [3]Describing the Data


## 12. Additional Features
