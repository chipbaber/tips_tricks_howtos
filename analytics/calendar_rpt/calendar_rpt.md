# How to Develop a Calendar Report in Oracle Data Visualizer

## Introduction

In the current release of OAC the ability to do calendar based vizualizations is very limited. The only option at the time of this recording was to leverage the Calendar Heat Map Custom Vizualization which for my purpose was not the best option. 

We'll show you

* Import a sample data set
* Create custom calculations on a date field.
* Leverage the List Vizualization to create a calendar display. 

[How to Develop a Calendar Report in Oracle Data Visualizer](youtube:xxxxxxx)



## Task 1: Create Database User with Grants

As the user **ADMIN**, issue the below SQL Statements

1.  Create Database User

    ```
    <copy>
	create user vector identified by "{password}";
	grant dwrole to vector;
    </copy>
    ```

2.  Grant Database User Access to DBMS Packages

    ```
    <copy>
    grant execute on DBMS_CLOUD to vector;
    grant execute on DBMS_VECTOR to vector;
    </copy>
    ```

## Task 2: Update Access Control List

As the user **ADMIN**, issue the following PL/SQL Code

1. Grant Non-Admin User Permission to Access OCI Gen AI Provider

    ```
    <copy>
	BEGIN
	DBMS_NETWORK_ACL_ADMIN.APPEND_HOST_ACE (
	  HOST         => 'inference.generativeai.us-chicago-1.oci.oraclecloud.com',
	  ACE          => xs$ace_type(
		  PRIVILEGE_LIST => xs$name_list('http'),
		  PRINCIPAL_NAME => 'vector',
		  PRINCIPAL_TYPE => xs_acl.ptype_db));
	END;
	/	
    </copy>
    ```

    If you would like to see what existing ACL Priviledges exist, execute the following SQL Statement

    ```
    <copy>
	select a.host, b.principal, b.privilege, b.is_grant 
    from dba_network_acls a, dba_network_acl_privileges b
    where a.acl = b.acl;     
    </copy>
    ```

    

## Acknowledgements
  * **Authors:** Chip Baber, Director Cloud Engineering, Oracle Code Innovate
  * **Last Updated By/Date:** Chip Baber, Sept 18, 2024

Copyright (C)  Oracle Corporation.

Permission is granted to copy, distribute and/or modify this document
under the terms of the GNU Free Documentation License, Version 1.3
or any later version published by the Free Software Foundation;
with no Invariant Sections, no Front-Cover Texts, and no Back-Cover Texts.
A copy of the license is included in the section entitled [GNU Free Documentation License](files/gnu-free-documentation-license.txt)