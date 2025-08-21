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
