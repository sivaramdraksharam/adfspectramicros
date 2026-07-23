# adfspectramicros
Application Development Framework using Oracle14c jdeveloper studio, oracle 19c database for 3 days. Developing microservices using spectra (Rancher desktop) for installing single note using kubernetes.

Day2
-----
The Controller Layer – ADF Task Flows & Data Binding

Objective: Master application navigation, modular page design, and binding backend fields tightly to screen elements using the ADF Model (Binding)
layer.

Topics Covered:
---------------
1. ADF Page Definitions & Executables: Understanding how pages fetch data.
2. Unbounded vs. Bounded Task Flows: Differentiating between global site routes and reusable, parameterized modular UI wizards.
3. Router & Method Call Activities: Conditional navigation paths and executing Java methods before rendering screens.
4. Task Flow Parameters: Passing context safely between isolated sub-sections of an application

Practical Example: Multi-Step Employee Hiring Wizard
-----------------------------------------------------
Scenario: Create a self-contained, repeatable, three-step checkout/onboarding workflow wizard.

1. Create a Bounded Task Flow (create-employee-flow-definition.xml) with a designated train layout.
2. Drop three View activities representing steps: Personal Details, Job Assignments, and Salary Review.
3. Drag a Method Call activity to the entry point of the flow that executes the CreateInsert operation on the Employees View Object.
4. Map a Router activity checking if a mandatory department parameter was provided; route users to an error screen if empty.
5. Add final task-flow-return activities handling standard transaction options (Commit or Rollback) to either persist or discard data safely.

