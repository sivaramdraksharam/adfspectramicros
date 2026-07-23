# adfspectramicros
Application Development Framework using Oracle14c jdeveloper studio, oracle 19c database for 3 days. Developing microservices using spectra (Rancher desktop) for installing single note using kubernetes.

The curriculum follows Oracle's Model-View-Controller architecture leveraging Java 17/21 capabilities supported by the 14c platform. It transitions from data backends to business logic, task flows, and rich user interfaces.

Day 1: The Model Layer – ADF Business Components (ADF BC)

Objective: Learn to declaratively map a relational database to business objects, expose data control APIs, and handle transactional business logic

Topics Covered:
Introduction to ADF 14c & MVC Architecture: Understanding the Fusion Middleware stack.Entity Objects (EO): Creating the database persistence layer; handling validation.View Objects (VO): Querying, filtering, and joining data.Application Modules (AM): Transaction management and exposing data controls to the UI.Java 17/21 Integration: Utilizing updated language syntax in business logic customizations

Practical Example: Employee Management Backend:
-----------------------------------------------
Scenario: Build a backend service to manage an organization's departments and employees using standard DEPT and EMP database tables.

Step-by-Step Task:
1. Create a Fusion Web Application Workspace in JDeveloper 14c.
2. Generate an Entity Object for Employees (EmployeesEO) and Departments (DepartmentsEO).
3. Build a master-detail View Object relation (EmpDeptFkLink) to dynamically bind matching employees to selected departments.
4. Implement a declarative validation rule on EmployeesEO (e.g., Salary must be greater than 1000).
5. Add both VOs to an Application Module (HrAppModule)

Verification: Run the ADF Business Component Browser directly in JDeveloper to test data insertion, query capabilities, and validation constraints without a web interface.




