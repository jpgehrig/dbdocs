Consider the columns of each table of `HR` sample schema.

- Table HR.COUNTRIES

- Table HR.DEPARTMENTS

- Table HR.EMPLOYEES

- Table HR.JOBS

- Table HR.JOB_HISTORY

- Table HR.LOCATIONS

- Table HR.REGIONS

### 4.3.1 Table HR.COUNTRIES

Table 4-3 HR.COUNTRIES Table Description

| Column Name    | Null?      | Type           |
|:---------------|:-----------|:---------------|
| `COUNTRY_ID`   | `NOT NULL` | `CHAR(2)`      |
| `COUNTRY_NAME` |            | `VARCHAR2(40)` |
| `REGION_ID`    |            | `NUMBER`       |

### 4.3.2 Table HR.DEPARTMENTS

Table 4-4 HR.DEPARTMENTS Table Description

| Column Name       | Null?      | Type           |
|:------------------|:-----------|:---------------|
| `DEPARTMENT_ID`   | `NOT NULL` | `NUMBER(4)`    |
| `DEPARTMENT_NAME` | `NOT NULL` | `VARCHAR2(30)` |
| `MANAGER_ID`      |            | `NUMBER(6)`    |
| `LOCATION_ID`     |            | `NUMBER(4)`    |

### 4.3.3 Table HR.EMPLOYEES

Table 4-5 HR.EMPLOYEES Table Description

| Column Name      | Null?      | Type           |
|:-----------------|:-----------|:---------------|
| `EMPLOYEE_ID`    | `NOT NULL` | `NUMBER(6)`    |
| `FIRST_NAME`     |            | `VARCHAR2(20)` |
| `LAST_NAME`      | `NOT NULL` | `VARCHAR2(25)` |
| `EMAIL`          | `NOT NULL` | `VARCHAR2(20)` |
| `PHONE_NUMBER`   |            | `VARCHAR2(20)` |
| `HIRE_DATE`      | `NOT NULL` | `DATE`         |
| `JOB_ID`         | `NOT NULL` | `VARCHAR2(10)` |
| `SALARY`         |            | `NUMBER(8,2)`  |
| `COMMISSION_PCT` |            | `NUMBER(2,2)`  |
| `MANAGER_ID`     |            | `NUMBER(6)`    |
| `DEPARTMENT_ID`  |            | `NUMBER(4)`    |

### 4.3.4 Table HR.JOBS

Table 4-6 HR.JOBS Table Description

| Column Name  | Null?      | Type           |
|:-------------|:-----------|:---------------|
| `JOB_ID`     | `NOT NULL` | `VARCHAR2(10)` |
| `JOB_TITLE`  | `NOT NULL` | `VARCHAR2(35)` |
| `MIN_SALARY` |            | `NUMBER(6)`    |
| `MAX_SALARY` |            | `NUMBER(6)`    |

### 4.3.5 Table HR.JOB_HISTORY

Table 4-7 HR.JOB_HISTORY Table Description

| Column Name     | Null?      | Type           |
|:----------------|:-----------|:---------------|
| `EMPLOYEE_ID`   | `NOT NULL` | `NUMBER(6)`    |
| `START_DATE`    | `NOT NULL` | `DATE`         |
| `END_DATE`      | `NOT NULL` | `DATE`         |
| `JOB_ID`        | `NOT NULL` | `VARCHAR2(10)` |
| `DEPARTMENT_ID` |            | `NUMBER(4)`    |

### 4.3.6 Table HR.LOCATIONS

Table 4-8 HR.LOCATIONS Table Description

| Column Name      | Null?      | Type           |
|:-----------------|:-----------|:---------------|
| `LOCATION_ID`    | `NOT NULL` | `NUMBER(4)`    |
| `STREET_ADDRESS` |            | `VARCHAR2(40)` |
| `POSTAL_CODE`    |            | `VARCHAR2(12)` |
| `CITY`           | `NOT NULL` | `VARCHAR2(30)` |
| `STATE_PROVINCE` |            | `VARCHAR2(25)` |
| `COUNTRY_ID`     |            | `CHAR(2)`      |

### 4.3.7 Table HR.REGIONS

Table 4-9 HR.REGIONS Table Description

| Column Name   | Null?      | Type           |
|:--------------|:-----------|:---------------|
| `REGION_ID`   | `NOT NULL` | `NUMBER`       |
| `REGION_NAME` |            | `VARCHAR2(25)` |
