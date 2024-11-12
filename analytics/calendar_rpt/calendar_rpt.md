# How to Develop a Calendar Report in Oracle Data Visualizer

## Introduction

In the current release of OAC the ability to do calendar based vizualizations is very limited. The only option at the time of this recording was to leverage the Calendar Heat Map Custom Vizualization which for my purpose was not the best option. During this tutorial we will showcase how to modify DV lists so that they build a make shift calendar of information items per day of the month. 

We'll show you

* Import a sample data set
* Create custom calculations on a date field.
* Create a filter to limit view to a single month
* Leverage the List Vizualization to create a calendar display view leveraging your filters. 

Please watch this first. Only the basic instructions and sample code will be provided below, the core guidance is inside the video itself. 
[How to Develop a Calendar Report in Oracle Data Visualizer](https://youtu.be/wmckqRVbWV4)

For other how to videos please visit my playlist [Technology and Coding](https://www.youtube.com/playlist?list=PLsnBif_-5JnA8Hzvp8e1bQ3fo6VEvYEB0)

Your end result will look like: 

![](images/2024-11-08-09-59-42.png)


## Task 1: Open DV and Upload the Sample Data Set


1.  Download the sample data set to your local machine. 

The sample csv file below can be found at: [Sample Data CSV] (https://raw.githubusercontent.com/chipbaber/tips_tricks_howtos/refs/heads/main/analytics/calendar_rpt/files/sample.csv)


## Task 2: Develop the Following Calculations

The calculations are needed to construct the calendar list view. In some cases the calculation will be created for you on .csv upload, however if you are leveraging a restricted data set I will include the examples for all. 

1. Create the Month column calculation.
    ```
    MonthNAME(Date)
    
    ```
![](images/2024-11-06-10-38-11.png) 

2. Create the muneric day of the week calc. 

    ```
   DAYOFWEEK(Date)
    ```
![](images/2024-11-06-10-41-46.png)

3. Create the alphabetical day of the week calc. 

  ```
  DAYNAME(Date)
  ```

4. Create the interaction week starting calculation.
  ```
  EXTRACTWEEK(Date)
  ``` 
  ![](images/2024-11-06-10-46-56.png)

## Task 3: Set the Display Date Format

1. Set the date format in the list report. 

  ```
  MMM DD: 
  ```
  

## Acknowledgements
  * **Authors:** Chip Baber, Director Cloud Engineering, Oracle Code Innovate
  * **Last Updated By/Date:** Chip Baber, Nov. 11, 2024

Copyright (C)  Oracle Corporation.

Permission is granted to copy, distribute and/or modify this document
under the terms of the GNU Free Documentation License, Version 1.3
or any later version published by the Free Software Foundation;
with no Invariant Sections, no Front-Cover Texts, and no Back-Cover Texts.
A copy of the license is included in the section entitled [GNU Free Documentation License](files/gnu-free-documentation-license.txt)