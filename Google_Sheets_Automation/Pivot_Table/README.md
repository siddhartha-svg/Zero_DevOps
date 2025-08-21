Automated Data Calculation Formulas
This document outlines the spreadsheet formulas used to automatically calculate the summary table from the raw data.
Formulas by POC/Severity
The following table provides the formulas used for each category and severity level.
POC/Severity
Critical
High
Medium
Total
PROD
=SUMIF(D:D, "Prod", E:E)
=SUMIF(D:D, "Prod", F:F)
=SUMIF(D:D, "Prod", I:I)
=M2+N2+O2
SES/HPSA
=SUMIF(D:D, "HPSA", E:E) + SUMIF(D:D, "SES", E:E)
=SUMIF(D:D, "HPSA", F:F) + SUMIF(D:D, "SES", F:F)
=SUMIF(D:D, "HPSA", I:I) + SUMIF(D:D, "SES", I:I)
=M3+N3+O3
DBA
=SUMIF(D:D, "DBA", E:E)
=SUMIF(D:D, "DBA", F:F)
=SUMIF(D:D, "DBA", I:I)
=M4+N4+O4
Non Prod (TDC/STG/UAT)
=SUMIF(D:D, "TDC-NP", E:E) + SUMIF(D:D, "Staging-NP", E:E) + SUMIF(D:D, "SDC-NP", E:E)
=SUMIF(D:D, "TDC-NP", F:F) + SUMIF(D:D, "Staging-NP", F:F) + SUMIF(D:D, "SDC-NP", F:F)
=SUMIF(D:D, "TDC-NP", I:I) + SUMIF(D:D, "Staging-NP", I:I) + SUMIF(D:D, "SDC-NP", I:I)
=M5+N5+O5
Non Prod (VZI)
=SUM(FILTER($E$1:$E$30, ISNUMBER(MATCH($D$1:$D$30, {"JDK-K2view","JDK-opt/app/","JDK-SPARK","JDK-SPARK-UIM","jenkins","Fortify"},0))))
=SUM(FILTER($F$1:$F$30, ISNUMBER(MATCH($D$1:$D$30, {"JDK-K2view","JDK-opt/app/","JDK-SPARK","JDK-SPARK-UIM","jenkins","Fortify"},0))))
=SUM(FILTER($I$1:$I$30, ISNUMBER(MATCH($D$1:$D$30, {"JDK-K2view","JDK-opt/app/","JDK-SPARK","JDK-SPARK-UIM","jenkins","Fortify"},0))))
=M6+N6+O6

How It Works
SUMIF(range, criteria, sum_range): This is the primary function used. It looks for a specific text string (criteria) within a given column (range) and adds up the values from a different column (sum_range) on the same rows where it finds a match. For example, =SUMIF(D:D, "Prod", E:E) finds every row with "Prod" in column D and sums the corresponding values from column E.
+: We use the plus sign to add the results of multiple SUMIF functions when a category has several different text strings associated with it (e.g., "HPSA" and "SES" both fall under "SES/HPSA").
SUM(FILTER(...)) with ISNUMBER(MATCH(...)): This is a more advanced formula used for the Non Prod (VZI) category. It allows you to check for multiple criteria at once from a list.
MATCH($D$1:$D$30, {"..."}, 0): This looks for any of the listed terms (e.g., "JDK-K2view") within the Comments column (D). It returns the row number if it finds a match and an error if it doesn't.
ISNUMBER(...): This function checks whether the MATCH result is a number. This effectively gives us TRUE for every row that contains one of the listed terms and FALSE for the others.
FILTER(...): This function uses the TRUE/FALSE list to filter the Critical column (E), keeping only the values on the rows that matched.
SUM(...): Finally, SUM adds all the filtered values together to give the total.
=M2+N2+O2: The Total column is a simple addition of the three severity columns to the left of it.
This approach provides a robust way to categorize and sum data from various sources into a single, clean summary.
