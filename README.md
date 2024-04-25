# SQL Queries for Employee Login Attempts 

## Apply filters to SQL Queries (Portfolio Project from Google Cybersecurity Professional Certificate)

### Project description
I am a security professional at a large organization. After discovering some potential security issues that involve login attempts and employee machines, I decided to examine the organization's database, using SQL filters to retrieve relevant records for further investigation. The database runs on MariaDB and the table format is detailed [here](https://github.com/averyth3archivist/SQLloginqueries/blob/38de08f19ad6839bbb0ced8246772bc69576bf04/Employee%20Log-in%20SQL%20Table%20Format.docx).

### 1. Retrieve after hours failed login attempts
A security incident after business hours occurred after business hours. Therefore, I needed to query all after hours login attempts that failed. **Figure 1** demonstrates how I created a SQL query to filter for this criteria. In my query, I selected all the data from ```log_in_attempts``` table and used a ```WHERE``` caluse with an ```AND``` operator to filter my results using two conditions. The first --- login attempts that occurred after 18:00 -> ```login_time > '18:00;``` and the second, ```success = FALSE```, which filters for failed login attempts.

![alt text][figure1]

[figure1]: https://github.com/averyth3archivist/SQLloginqueries/blob/7f416af7f8f001fb9868ca8ff8764db7893d147d/SQLfilters_Figure1.png "Figure 1"

***Figure 1.** Demonstration of SQL filter to identify all failed login attempts that occurred after 18:00 or business hours.*

The output is a table that returns all failed after hours login attempts.

### 2. Retrieve login attempts on specific dates
An incident of concern arose on May 9th, 2022. Consequently, any login activity on May 9th or the preceding day requires thorough investigation.

The provided SQL query demonstrates how to filter login attempts for specific dates. The query retrieves data from the ````log_in_attempts```` table and utilizes a ```WHERE``` clause with an ```OR``` operator to narrow down results to login attempts from either May 9th or May 8th, 2022. The conditions include ```login_date = '2022-05-08'``` to filter for logins on May 8th and ```login_date = '2022-05-09'``` to filter for logins on May 9th.

![alt text][figure2]

[figure2]: https://github.com/averyth3archivist/SQLloginqueries/blob/7f416af7f8f001fb9868ca8ff8764db7893d147d/SQLfilters_Figure2.png "Figure 2"

***Figure 2.** Demonstration of SQL filter to identify all login attempt that occurred on 2022-05-09 or 2022-05-08.*

### 3. Retrieve login attempts outside of Mexico
Upon reviewing the organization's login attempt data, it appeared there may have be an issue with login attempts originating from locations outside of Mexico. These attempts warranted further investigation.

![alt text][figure1]

[figure3]: https://github.com/averyth3archivist/SQLloginqueries/blob/7f416af7f8f001fb9868ca8ff8764db7893d147d/SQLfilters_Figure3.png "Figure 3"
***Figure 3.**Demonstration of SQL filter to retrieve all login attempts outside of Mexico*

The provided SQL query showcases how I filtered login attempts occurring outside of Mexico. The query begins by selecting all data from the ```log_in_attempts``` table and employs a WHERE clause with ```NOT``` to exclude entries from Mexico. I utilized the ```LIKE``` operator with the pattern ```MEX%``` to match Mexico, accounting for variations such as ```MEX``` and ```MEXICO``` in the dataset. The ```%``` symbol in ```LIKE``` represents any number of unspecified characters.

### 4. Retrieve employees in Marketing
My team needed to update computers for specific employees within the Marketing department. To proceed, it was necessary to gather details on which employee machines required updates.

![alt text][figure4]

[figure4]: https://github.com/averyth3archivist/SQLloginqueries/blob/7f416af7f8f001fb9868ca8ff8764db7893d147d/SQLfilters_Figure4.png "Figure 4"
***Figure 4.** Demonstration of SQL filter to identify employees in the Marketing department*

The provided SQL query exemplifies how I crafted a query to identify employee machines belonging to individuals in the Marketing department situated in the East building. The query begins by selecting all data from the ```employees``` table and incorporates a ```WHERE``` clause with ```AND``` to narrow down results to employees working in the Marketing department and located in the East building. I utilized ```LIKE``` with the pattern ```East%``` to match the East building designation in the ```office``` column, considering variations such as specific office numbers. The first condition, ```department = 'Marketing'```, filters for Marketing department employees, while the second condition, ```office LIKE 'East%'```, filters for those in the East building.

### 5. Retrieve employees in Finance or Sales
The update requirement extended to machines used by employees in the Finance and Sales departments. I needed to gather information solely on employees belonging to these two departments.
![alt text][figure5]

[figure5]: https://github.com/averyth3archivist/SQLloginqueries/blob/7f416af7f8f001fb9868ca8ff8764db7893d147d/SQLfilters_Figure5.png "Figure 5"
***Figure 5.** Demonstration of SQL filter to identify employees in the Finance and Sales departments*

The provided SQL query illustrates how I formulated a query to identify employee machines within the Finance or Sales departments. Beginning with selecting all data from the ```employees``` table, the query utilizes a ```WHERE``` clause with ```OR``` to isolate employees from either the Finance or Sales departments. The ```OR``` operator is employed instead of ```AND``` to capture all employees belonging to either department. The first condition, ```department = 'Finance'```, filters for employees from the Finance department, while the second condition, ```department = 'Sales'```, filters for those from the Sales department.

### 6. Retrieve all employees not in IT
An additional security update was required for all employees outside of the Information Technology or IT department. The following query identifies employees that satisfy this criteria. Starting with selecting all data from the ```employees``` table, the query employs a ```WHERE``` clause with ```NOT``` to exclude employees from this department.

![alt text][figure6]

[figure6]: https://github.com/averyth3archivist/SQLloginqueries/blob/7f416af7f8f001fb9868ca8ff8764db7893d147d/SQLfilters_Figure6.png "Figure 6"
***Figure 6.** Demonstration of SQL filter to identify employees in the IT department*

### Summary
I utilized SQL query filters to extract precise details regarding login attempts and employee machines. Leveraging two distinct tables, namely ```log_in_attempts``` and ```employees```, I employed operators such as ```AND```, ```OR```, and ```NOT``` to refine the search criteria tailored to each task. Additionally, I utilized the LIKE operator along with the wildcard symbol (```%```) to filter for specific patterns within the data.


