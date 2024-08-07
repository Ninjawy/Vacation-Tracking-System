# (VacationTrackingSystem)
---

## Vision

A Vacation Tracking System (VTS) will provide individual employees with the 
capability to manage their own vacation time, sick leave, and personal time off, 
without having to be an expert in company policy or the local facility’s leave 
policies.

### Index
1. [Requirements](#requirements)
    1.i  [Functional requirements](#functional)
    1.ii [Non-Functional requirements](#nonfunctional)
2. [Use Cases](#usecases)
3. [Use Case Actors](#usecasesactors)
4. [Use Case: Manage Time](#managetime)
5. [Database Diagram](#dbdiagram)
6. [Use Case Diagram](#usecasediagram)
7. [Flow Diagram](#flowdiagram)
8. [Sequence Diagram](#sequencediagram)
---



## Requirements <a name="requirements"></a>


#### Functional requirements <a name="functional"></a>:

1. Flexible System for Leave Requests: The system must follow company policies and rules for validating and verifying leave time requests;
2. Manager Approval: It should enable manager approval of leave requests if needed;
3. Access to Past and Future Requests: The system must provide access to leave requests from the previous 12 months and allow future requests up to 18 months in advance;
4. Email Notifications: The system should use email to notify managers for approval and inform employees about request status changes;
9. Override Capabilities: HR and system admins should be able to override rules, with the system keeping track of these changes;
10. Direct Leave Awarding: The system must allow managers to directly award personal leave time, within set limits;
11. Web-Based UI for Internal Systems: It should provide a web-based interface for other internal systems to review an employee's vacation request summary;
12. Integration with HR Systems: The system should connect with existing HR systems to pull necessary employee information and updates.

#### Non-Functional requirements <a name="nonfunctional"></a>:

1. Ease of Integration and Compatibility: The system should be complementary and easy to integrate, supporting single sign-on (SSO) mechanisms for authentication.
2. Activity Logging: The system must keep activity logs for all transactions.


---

## Use Cases <a name="usecases"></a>
- [x] Manage Time
- [ ] Approve Request
- [ ] Award Time
- [ ] Edit Employee Record
- [ ] Manage Locations
- [ ] Manage Leave Categories
- [ ] Override Leave Records
- [ ] Back Up System Logs

---

## Use Case Actors <a name="usecasesactors"></a>:

1. Employee
    i. Manage Time
2. Manager
    i. Aprrove Request
   ii. Manage Time
3. HR Clerk
    i. Edit Employee Record
    ii. Manage Locations
    iii. Manage Leave Categories
    iv. Override Leave Records
4. System Admin
    i. Back Up System Logs

---

## Use case name: Manage Time <a name="managetime"></a>
 ###### Actor: Employee
 ###### Goal: The employee wishes to submit a new request for vacation time.
 ###### Preconditions: The employee is authenticated by the portal framework and identified as an employee of the company with privileges to manage his or her own vacation time. 
###### 1. Employee selects a link from the intranet portal to access the VTS.
2. VTS displays current status and balances of employee’s vacation time for past 6 months and up to 18 months in the future.
3. Employee selects a vacation category with a positive balance to create a new request.
4. VTS prompts for date(s) and time, providing a visual calendar for selection.
5. Employee selects dates, hours, and enters a title and description, then submits the request.
6. If the information is incomplete or incorrect, errors are highlighted and documented for correction.
7. Employee can amend the information or cancel the request.
8. If complete and valid, employee returns to the VTS home page. If approval is needed, an email is sent to the manager.
13. Vacation request is marked as pending approval.
14. Manager responds via email link or by logging into the VTS through the intranet portal.
15. Manager may need to authenticate to access the VTS.
16. VTS shows manager’s vacation requests and a section for pending approvals. Manager reviews each request individually.
17. Manager views request details and approves or disapproves, providing an explanation if disapproved. Request status is updated accordingly.
18. An email notification of approval or rejection is sent to the employee. Manager returns to the VTS home page to handle other requests, make their own request, or exit the application.

###### Alternate flow: Withdraw Request
 ###### Goal: The employee wants to withdraw an outstanding request for vacation time.
 ###### Preconditions: An employee has made a vacation time request, and that request has yet to be approved or denied by an authorized manager.
1. The employee accesses the VTS home page via the intranet portal, which authenticates their access.
2. The VTS home page shows a summary of vacation time requests, outstanding balances, and the status of all active requests for the past 6 months and up to 18 months in the future.
3. The employee selects a vacation request that is pending approval to withdraw.
4. The VTS prompts the employee to confirm the withdrawal of the request.
5. Upon confirmation, the request is removed from the manager’s list of pending approvals.
6. The system sends a notification email to the manager.
7. The request status is updated to withdrawn.

 ###### Alternate flow: Cancel Approved Request
 ###### Goal: The employee wants to cancel an approved vacation time request.
 ###### Preconditions: The employee has a vacation time request that has been approved and is scheduled for some time in the future or the recent past (previous 5 business days). See also main flow preconditions.
1. Employee accesses the VTS home page via the intranet portal, which authenticates their access.
2. The VTS home page shows a summary of vacation requests, outstanding balances by category, and the status of all active requests for the past 6 months and up to 18 months in the future.
3. Employee selects a vacation request to cancel, which must be either in the future or recent past and previously approved.
4. For future requests, the employee confirms cancellation. For recent past requests, the employee must confirm and provide a brief explanation. Upon approval, an email notification is sent to the manager, the request status is updated to canceled, and the used time allowances are returned to the employee. Cancellation can be aborted, leaving the request unchanged.
5. Employee returns to the VTS home page, where summaries are updated to reflect any changes.
 ###### Alternate flow: Edit Pending Request
 ###### Goal: The employee wants to edit the description or title of a pending request.
**Preconditions:** An employee has submitted a vacation time request that is pending manager approval.

1. Employee accesses the VTS home page via the intranet portal, which authenticates and verifies the employee’s access rights.
2. The VTS home page shows a summary of vacation requests, outstanding balances, and the status of all active requests for the past 6 months and up to 18 months in the future.
3. Employee selects a pending request to edit.
4. The VTS provides an editable view of the request, allowing changes to the title, comments, dates, or the option to delete or withdraw the request.
5. Employee makes changes and submits them to the system.
6. If the request is withdrawn, the VTS prompts for confirmation. If changes are made, they are accepted, and the employee is returned to the VTS home page. If there are errors, the VTS redisplays the editing page with highlighted issues and explanations.

**Additional Notes:** 

- The description provides functional details from the employee’s perspective but lacks non-functional requirements and domain-specific information.
- Non-functional requirements should cover aspects like performance, security, and scalability.
- Domain knowledge includes specific rules such as workday hours, location-specific policies, and validation rules managed by HR.
- Relevant domain information is typically found in company policies or employee manuals, which should be referenced rather than duplicated.

---

## Database-Entity Diagram <a name="dbdiagram"></a>:
1. Employees: Stores information about employees in VTS;
2. Manager: A relation which stores manager and employees of his/her responsability;
3. HRClerk: A relation which stores HR clerk and employees of his/her responsabilit;
4. Location: Stores necessary information about location/site on which the employee works;
2. VacationRequests: Stores vacation requests made by employees;
3. SystemLogs: Records various actions, events, and changes within the system for auditing and monitoring purposes.

![E-R Database tables](https://github.com/user-attachments/assets/94fbe986-0912-4aeb-84ec-a77fca58bcd2)


---
## Usecase Diagram: <a name="usecasediagram"></a>
![UseCaseDiagram](https://github.com/user-attachments/assets/9565d6d9-69e0-437f-ad64-39ecdf6d294a)

---
## FLow Diagram: <a name="flowdiagram"></a>:
![EmployeeFlowchart](https://github.com/user-attachments/assets/5777efd8-0961-4131-8c73-f98bdbcb9e26)
![ManagerFlowChart](https://github.com/user-attachments/assets/2913864a-1665-49d3-8d85-a255b8f7cf37)
![HRClerkFLowChart](https://github.com/user-attachments/assets/3eea3066-51ba-48bc-bf72-cfeafc0e9d37)


---

## Sequence Diagram <a name="sequencediagram"></a>
![EmployeeSequenceDiagram1](https://github.com/user-attachments/assets/51d918b1-e55c-4cd2-ab16-862ee19395a2)
![EmployeeSequenceDiagram2](https://github.com/user-attachments/assets/45c4498d-6f6b-40c4-aa14-6b47ab9eeded)
![ManagerSequenceDiagram](https://github.com/user-attachments/assets/cb903c1d-6028-4d56-b6a1-b6779a7f1cca)
![HRClerkSequenceDiagram](https://github.com/user-attachments/assets/0557d860-951f-4c6b-a416-fc544c31e48e)



