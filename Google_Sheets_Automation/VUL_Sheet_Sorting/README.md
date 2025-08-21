# Data Aggregation & Pivot Table Instructions

This document outlines the steps and criteria for aggregating data and generating a pivot table from a source report.

### Data Aggregation Rules

A new "Comments" column should be added to the end of the original table. The following rules are used to populate this column based on the content of other columns:

* **PROD**: If the `Environment` column contains "PRODUCTION", the comment should be "Prod".
* **INFO/LOW**: If the `Severity` column contains "Info" or "Low", the comment should be "Info/low".
* **DBA**: If the `HostName` column contains "vd", the comment should be "DBA".
* **HPSA**: If the `Plugiun Output` column contains "opsware", the comment should be "HPSA".
* **SES**: If the `Vuln Name` column contains "RHEL", the comment should be "SES".
* **TDC-NP**: If the `FQDN` column contains "tdc", the comment should be "TDC-NP".
* **Windows**: If the `OS` column contains "Windows", the comment should be "Windows".
* **numpy**: If the `Plugiun Output` column contains "numpy", the comment should be "numpy".
* **jenkins**: If the `Plugiun Output` column contains "jenkins", the comment should be "jenkins".
* **K2VIEW-JDK**: If the `Plugiun Output` column contains "/apps/k2view/apps/openlogic-openjdk", the comment should be "K2VIEW-JDK".
* **JDK-SPARK**: If the `Plugiun Output` column contains "opt/app/SPARK/SPARK/jdk-/", the comment should be "JDK-SPARK".
* **MQM-Jre**: If the `Plugiun Output` column contains "/app/mqm/java/jre64/", the comment should be "MQM-Jre".
* **JDK-UIM**: If the `Plugiun Output` column contains "/opt/app/fabric/apps/openlogic-openjdk", the comment should be "JDK-UIM".
* **Fortify**: If the `Plugiun Output` column contains "/jitr/rbm/fortifyLinux/", the comment should be "Fortify".
* **Microfocus**: If the `Plugiun Output` column contains "/apps/opt/microfocus/Discovery/bin/libcrypto", the comment should be "Microfocus".
* **rbmtmp**: If the `Plugiun Output` column contains "/jitr/rbm/rbmtmp/tiwarvi/", the comment should be "rbmtmp".
* **k2view-pgsql**: If the `Plugiun Output` column contains "opt/apps/k2view/apps/pgsql-9.6/bin/postgres", the comment should be "k2view-pgsql".
* **Tornado**: If the `Plugiun Output` column contains "/usr/local/lib64/python3.6/site-packages/tornado", the comment should be "Tornado".
* **WAS-Libs/PY-365**: If the `Plugiun Output` column contains "/opt/app/PY-365/lib/libcrypto.so", the comment should be "WAS-Libs/PY-365".
* **K2VIEW-Postgres**: If the `Plugiun Output` column contains "/apps/k2view/apps_fabric-6.5.9_186-HF15/pgsql-13.3/bin/postgres", the comment should be "K2VIEW-Postgres".
* **K2view-pgsql-libcrypto/ssl**: If the `Plugiun Output` column contains "/apps/k2view/apps/pgsql-9.6/lib/libcrypto.so", the comment should be "K2view-pgsql-libcrypto/ssl".
* **Node**: If the `Plugiun Output` column contains "/opt/VIS2/nodejs-8.6.0-0/common/bin/openssl.bin", the comment should be "Node".
* **Pgsql-libcurl**: If the `Plugiun Output` column contains "/apps/k2view/apps/pgsql-9.6/lib/libcrypto.so.1.1", the comment should be "Pgsql-libcurl".
* **SDC-NP**: If the `DataCenterName` column contains "Sacramento", the comment should be "SDC-NP".
* **WAS-Libs**: If the `Plugiun Output` column contains "/usr/lib64/libcrypto.so.", the comment should be "WAS-Libs".
* **HTTPD-/opt/IBM**: If the `Plugiun Output` column contains "/opt/IBM/HTTPServer855A/bin/httpd", the comment should be "HTTPD-/opt/IBM".

### Pivot Table Instructions

1.  **Insert Pivot Table**: Create a new pivot table in a new sheet.
2.  **Rows**: Set the `Comments` column as the pivot table's rows.
3.  **Columns**: Set the `Severity` column as the pivot table's columns.
4.  **Values**: Set the `IPAddress` column as the pivot table's values.



```
=IF(ROW()=1, "Comments",
 IF(REGEXMATCH(U:U, "Info|Low"), "Info/Low",
 IF(REGEXMATCH(G:G, "PRODUCTION"), "Prod",
 IF(REGEXMATCH(C:C, "vd"), "DBA",
 IF(REGEXMATCH(G:G, "STAGING"), "Staging-NP",
 IF(REGEXMATCH(G:G, "USER ACCEPTANCE TEST"), "UAT",
 IF(REGEXMATCH(C:C, "tdc"), "TDC-NP",
 IF(REGEXMATCH(B:B, "^sacldiipva0([5-9]|[1-5][0-9]|6[0-5])$"), "SDC-NP",
 IF(REGEXMATCH(AH:AH, "RHEL"), "SES",
 IF(REGEXMATCH(I:I, "Windows"), "Windows",
 IF(REGEXMATCH(AS:AS, "opsware"), "HPSA",
 IF(REGEXMATCH(AS:AS, "/apps/k2view/apps/openlogic-openjdk"), "K2VIEW-JDK",
 IF(REGEXMATCH(AS:AS, "/apps/opt/uim/spark/spark-2.3.1-bin-hadoop2.7/project/jdk"), "JDK-SPARK",
 IF(REGEXMATCH(AS:AS, "opt/app/SPARK/SPARK/jdk"), "JDK-SPARK",
 IF(REGEXMATCH(AS:AS, "/app/mqm/java/jre64/"), "MQM-Jre",
 IF(REGEXMATCH(AS:AS, "/opt/app/fabric/apps/openlogic-openjdk"), "JDK-UIM",
 IF(REGEXMATCH(AS:AS, "numpy"), "numpy",
 IF(REGEXMATCH(AS:AS, "/opt/IBM/HTTPServer855/bin/httpd"), "Httpd-/opt/IBM",
 IF(REGEXMATCH(AS:AS, "jenkins"), "jenkins",
 IF(REGEXMATCH(AS:AS, "fortify"), "Fortify",
 IF(REGEXMATCH(AS:AS, "/apps/opt/microfocus/Discovery/bin/libcrypto"), "Microfocus",
 IF(REGEXMATCH(AS:AS, "rbmtmp"), "rbmtmp",
 IF(REGEXMATCH(AS:AS, "/apps/k2view/apps/pgsql"), "k2view-pgsql",
 IF(REGEXMATCH(AS:AS, "/opt/app/PY-365/lib/libcrypto.so"), "WAS-Libs/PY-365",
 IF(REGEXMATCH(AS:AS, "/usr/lib64/libcrypto.so."), "WAS-Libs",
 IF(REGEXMATCH(AS:AS, "/opt/app/uim/spark_bkp/jdk-17.0.12/"), "JDK-SPARK-UIM",
 IF(REGEXMATCH(AS:AS, "rbmtmp"), "rbmtmp",
 IF(REGEXMATCH(AS:AS, "/opt/VIS2/nodejs"), "Node",
 IF(REGEXMATCH(AS:AS, "/oracle/client/19.0.0.0/OPatch"), "Oracle_bkp",
 IF(REGEXMATCH(AS:AS, "/jenkins/Fortify/"), "Fortify",
 IF(REGEXMATCH(AS:AS, "/apps/opt/uim/spark/spark-2.3.1-bin-hadoop2.7/project/Hijack_UI_Project_PP/jdk180_421_64"), "JDK-SPARK-UIM",
 ""
 )))))))))))))))))))))))))))))
```



# MY-DATA-SHEET


──────────────────────📄EY2V────────────────────

> Add the coumn at thend with name of Comments 
> Insert pivot table in new sheet 
> From the table now making pivot table into 
─ Rows as Comments 
  Columns as Severity	
  Values as IPAddress
> S column : Severity Column :  check and tick mark it as Info and Low and in Comments as Info/low (Last column)
> G column : Environment Column : check and tick mark it as PRODUCTION add in Comments as Prod 
> G column : Environment Column : check and tick mark it as STAGING add in Comments as STAGING-NP 
> C column : FQDN Column : whichever server (box) names contain tdc , mark it in comments as TDC-NP
> AF column : Vuln Name : whichever box contain RHEL  mark it in comments as SES
> AQ column : Plugin Output : whichever box contain  /oracle/client/19.3.0.0.0/OPatch/  mark it in comments as UAT 
> AQ column : Plugin Output : whichever box contain  /opt/oracle.ahf/python/lib/libcrypto  mark it in comments as UAT
> AQ column : Plugin Output : whichever box contain  /usr/lib64/libcrypto.so.  mark it in comments as Lib64 
>  AQ column : Plugin Output :whichever box contain  /opt/app/SPARK/SPARK/jdk-17.0.  mark it in comments as JDK-SPARK/SPARK/jdk-17
> AQ column : Plugin Output : whichever box contain  /opt/app/jdk-17.0. mark it in comments as JDK-opt/app/SPARK/SPARK/jdk-17

──────────────────────────────────────────────────

```
=IF(ROW()=1, "Comments",
 IF(REGEXMATCH(U:U, "Info|Low"), "Info/Low",
 IF(REGEXMATCH(G:G, "PRODUCTION"), "Prod",
 IF(REGEXMATCH(G:G, "STAGING"), "Staging-NP",
 IF(REGEXMATCH(G:G, "USER ACCEPTANCE TEST"), "UAT",
 IF(REGEXMATCH(C:C, "tdc"), "TDC-NP",
 IF(REGEXMATCH(AH:AH, "RHEL"), "SES",
 IF(REGEXMATCH(AS:AS, "/opt/oracle.ahf/python/lib/libcrypto"), "HPSA",
 IF(REGEXMATCH(AS:AS, "/usr/lib64/libcrypto.so"), "Lib64",
 IF(REGEXMATCH(AS:AS, "/opt/app/SPARK/SPARK/jdk"), "JDK-SPARK",
 IF(REGEXMATCH(AS:AS, "/opt/app/jdk"), "JDK-opt/app/",
 IF(REGEXMATCH(AS:AS, "opsware"), "HPSA",
 IF(REGEXMATCH(AS:AS, "/mqm/data/MQHA/software/MQServer/lap/jre/ibm"), "MQM-Jre",
 IF(REGEXMATCH(AS:AS, "/opt/mqm/bin/"), "MQM-Bin",
 IF(REGEXMATCH(AS:AS, "/root/jdk"), "JDK-Root",
 IF(REGEXMATCH(AS:AS, "/opt/app/lib64_bkp"), "LIB64_bkp",
 ""
 ))))))))))))))))
```

─────────────────────────────────────────────────────

















