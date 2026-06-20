# Enterprise IAM Lab 

## Objective
The Enterprise IAM Lab was designed to demonstrate practical Identity and Access Management (IAM) skills by simulating an enterprise identity environment using Microsoft Entra ID P2. The lab implements RBAC, Conditional Access, Administrative Units, MFA, and Identity Governance to showcase how organizations enforce least privilege, secure user access, and support Zero Trust security principles.

### Skills Learned
- Applying RBAC and Administrative Units to enforce least privilege and delegated administration for users.
- Automating user group assignments using Dynamic Groups.
- Designing and implementing Conditional Access policies to restrict and grant access based off conditions.
- Practical experience with Identity Governance concepts, including Access Reviews and Entitlement Managment.
- Strenghtened critical thinking and problem-solving skills through designing security controls and troubleshooting identity and access scenarios.

### Tools Used
- Microsoft Entra ID P2 for implementing RBAC, Conditional Access, MFA, Identity Governance and Administrative Units.
- Microsoft Authenticator for MFA enrollment and authentication security.
- Microsoft Azure Portal for tenant administration and identity configuration.
- Access Reviews and Entitlement Management to simulate identity governance workflows.

## Steps

### Step 1: Create Users
- Created member and guest accounts representing different departments and roles within the organization. These users serve as the foundation for implementing RBAC, Conditional Access, and Identity Governance throughout the lab.
  
<img width="1919" height="1079" alt="Screenshot 2026-06-15 171101" src="https://github.com/user-attachments/assets/3bf31f89-ab00-474d-b8bf-aecd0c0db023" />


### Step 2: Create Groups
- Department based security groups were created and dynamic groups were implemented to automate user assignments based on department attributes. The addition of dynamic groups reduced administrative overhead and ensured users were automatically placed into the correct groups as their attributes change.
- The second screenshot shows an example where, S.Jones (HR Admin) and E.Carter (HR user) were assigned to the HR Users group based on their department attribute.
  
 <img width="1915" height="1079" alt="Screenshot 2026-06-15 171210" src="https://github.com/user-attachments/assets/42adfcc6-29fa-412d-b90c-95e521d384db" />
 <img width="1919" height="1079" alt="Screenshot 2026-06-15 171152" src="https://github.com/user-attachments/assets/3d9bf8b0-cd18-4d2e-bad1-dd327182e6cf" />


### Step 3: Administrative Units
- Implemented Administrative Units to enforce delegated administration and least privilege. Even though each departments Admin was assigned the User Authenticator role, they were scoped only to users within their respective departments.
- To test the configuration, I attempted to reset passwords for both E.Carter (HR User) and L.Brown (Finance User) while signed in as S.Jones (HR Admin). The password reset succeeded for E.Carter but failed for L.Brown, demonstrating that Administrative Units administrative permissions were effectively limited to only the HR department.
  
  <img width="1912" height="1079" alt="Screenshot 2026-06-15 181404" src="https://github.com/user-attachments/assets/4c81ded6-921f-4a71-856b-b6d22c0466de" />
  <img width="1919" height="1079" alt="Screenshot 2026-06-15 181428" src="https://github.com/user-attachments/assets/3582299d-2bd1-4f12-a4ef-343d5d83323c" />


### Step 4: RBAC
- Implemented RBAC to ensure each user's permissions aligned with their responsibilities. Department Admins were assigned the User Administrator role, while Administrative Units restricted their authority to their respective departments.
- In the screenshot below, M.Webbs' (IT admin) is shown with multiple roles. Because this account created the tenant, it was automatically assigned the Global Administrator role. Additionally, the account was given the User Administator and Authentication Administrator roles to simulate an IAM team responsible for managing users, MFA, and authentication methods across the entire tenant.
  
 <img width="1919" height="1079" alt="Screenshot 2026-06-15 171714" src="https://github.com/user-attachments/assets/e6fb7bb3-7e8b-4a8b-8c91-38ca5a02127e" />

 
### Step 5: Authentication & MFA
- Implemented phishing-resistant MFA for admins and required MFA enrollment for all users in the tenant to strenghten authenticaton security.
- To test the configuration, I signed in as S.Jones (HR Admin) and confirmed the user was prompted to register and complete MFA enrollment before gaining access.
  
  <img width="1910" height="1078" alt="Screenshot 2026-06-15 180330" src="https://github.com/user-attachments/assets/c8399242-ac13-4038-ab99-78cc580443f2" />


### Step 6: Conditional Access
- Implemented Conditional Access policies to strenghten access security and support Zero Trust principles.
- I configured the following policies:
   - Require MFA for all admin accounts
   - Block legacy authentication protocols that don't support MFA
   - Block access from login attempts outside of trusted locations
   - Restrict guest and contractor accounts from accessing adminstrative functions
 - As shown in the second screenshot below, I validated these controls by attempting to view Microsoft Entra administrative roles while signed in as A.Lee (Contractor). Access was denied, confirming that guest users were successfully restricted from administrative functions.
 
<img width="1919" height="1037" alt="Screenshot 2026-06-15 174958" src="https://github.com/user-attachments/assets/ae608113-718d-4fd4-bafe-50812aec45e6" />
<img width="1914" height="1079" alt="Screenshot 2026-06-15 181012" src="https://github.com/user-attachments/assets/ea9e30b7-88e8-4b81-8d12-ab13e6a160ca" />


### Step 7: Identiy Goverance / Excessive Permission Simulation
- To demonstrate Identity Governance workflows, I simulated a scenario where S.Jones (HR Admin) was accidentally assigned the Authentication Administrator role, granting them tenant wide authentication privileges. This role assignment violated principles of least privilege aand separation of duties by providing excessive access outside the user's job responsibilities.
- To resolve the issue, I created an Access Review for the HR Users group to identify and evaluate excessive permissions. The review flagged the innapropiate role assignment, and the Authentication Administrator role was removed and S.Jones privileges were set back to their properly scoped administrative role.
  
<img width="1646" height="562" alt="Screenshot 2026-06-17 181705" src="https://github.com/user-attachments/assets/d958edf0-b59d-41a7-a562-67db1d72e92f" />
<img width="1917" height="334" alt="Screenshot 2026-06-17 205435" src="https://github.com/user-attachments/assets/8851fa91-69e6-45ad-bf37-8472b33a669e" />



### Step 8: Entitlement Management
- To conclude the lab, I implemented an Entitlement Management scenario where A.Lee (Contractor) requested an Access Package granting access to Finance department applications. Requests required approval from J.Smith (Finance Admin). Two scenarios were created to demonstrate when access should and shouldn't be granted.
### Scenario 1: Access Denied
   - In this scenario A.Lee requested access to Finance applications without providing a legitmiate business justification. The request was denied by J.Smith demonstrating the principles of least privilege and preventing unnecessary access to sensitive resources.


   <img width="1917" height="899" alt="Screenshot 2026-06-17 190722" src="https://github.com/user-attachments/assets/b4bcdbf2-1bf0-4583-9389-da5fbbe36e2e" />

### Scenario 2: Temporary Access Granted
   - In the second scenario A.Lee requested temporary access to the Finance applications due to a change in job responsibilities requiring collaboration with the Finance department. Because the request included a valid business justification, J.Smith approved the request and A.Lee was temporarily assigned to the Finance Users group while retaining guest user status. This scenario demonstrated how Entitlement Management allows organizations to balance security with operational needs by providing time-bound access via approval and business justification.

  <img width="1649" height="503" alt="Screenshot 2026-06-17 192114" src="https://github.com/user-attachments/assets/069902e1-ee68-42ec-9dd3-faabb70fde8d" />
