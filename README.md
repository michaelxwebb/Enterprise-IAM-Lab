# Enterprise IAM Lab (In Progress)

## Objective
The Enterprise IAM Lab was designed to demonstrate practical Identity and Access Management (IAM) skills by simulating an enterprise identity environment using Microsoft Entra ID P2. The lab implements RBAC, Conditional Access, Administrative Units, MFA, and Identity Governance to showcase how organizations enforce least privilege, secure user access, and support Zero Trust security principles.

### Skills Learned
- Applying RBAC and Administrative Units to enforce least privilege for users.
- Ability to automate group assignments for users through dynamic groups.
- Designing and implementing Conditional Access policies to restrict and grant access based off conditions.
- Enhanced knowledge of Identity Governance concepts, including access reviews, and privileged access management.
- Development of critical thinking and problem-solving skills through designing security controls and troubleshooting identity and access scenarios.

### Tools Used
- Microsoft Entra ID P2 for implementing RBAC, Conditional Access, MFA, and Administrative Units.
- Microsoft Authenticator and Temporary Access Pass for MFA enrollment and authentication recovery.
- Microsoft Azure Portal for tenant administration and identity configuration.
- Access Reviews and Entitlement Management to simulate identity governance workflows

## Steps

### Step 1: Create Users
- In this step I created multiple users in the environment, both members and guest and assigned them to different departments so I could later assign roles, and access based on their relationship in the company.
<img width="1919" height="1079" alt="Screenshot 2026-06-15 171101" src="https://github.com/user-attachments/assets/3bf31f89-ab00-474d-b8bf-aecd0c0db023" />

### Step 2: Create Groups
- I then assigned users to distinct security groups depending on their department. To increase productivity I made dynamic groups to create automated group assignment based on specific constraints. For this specific project the user got assigned to the group based on what department they were in.
- Example: S.Jones (HR Admin) and E.Carter (HR user) were assigned to the HR Users group
 <img width="1915" height="1079" alt="Screenshot 2026-06-15 171210" src="https://github.com/user-attachments/assets/42adfcc6-29fa-412d-b90c-95e521d384db" />
 <img width="1919" height="1079" alt="Screenshot 2026-06-15 171152" src="https://github.com/user-attachments/assets/3d9bf8b0-cd18-4d2e-bad1-dd327182e6cf" />

### Step 3: Administrative Units
- In this Lab every admin in each department was given the User Administrator role. To practice least privilege I created administrative units to narrow the scope of those Admin roles to each Admin users respective department.
- To test the effects of the adminstrative unit I tried to change E.Carter (HR User) and L.Brown (Finance User), using S.Jones' (HR Admin) User Authenticator role. Because of the administrator unit S.Jones was only able to change E.Carter's password because that user is also in the HR department.
  <img width="1912" height="1079" alt="Screenshot 2026-06-15 181404" src="https://github.com/user-attachments/assets/4c81ded6-921f-4a71-856b-b6d22c0466de" />
  <img width="1919" height="1079" alt="Screenshot 2026-06-15 181428" src="https://github.com/user-attachments/assets/3582299d-2bd1-4f12-a4ef-343d5d83323c" />

### Step 4: RBAC
- Because I had different users with different roles within the company, I needed to ensure that each users access level was determined by that role. Each Admin user for their respective department was given a User administrator role to only manage the users in their departments. The admininstrative units that were mentioned previously allowed for delegated administration, ensuring the users only received permissions necessary to perform their responsibilities.
- In the screenshot below, M.Webbs' (IT admin) roles are shown. Because they are the creator of the tenant they were automatically assigned the Global Admin role alonside the User Admin role. Additionally the user was given the Authentication Admin role because they serve as the IAM team for the project, managing users, MFA, and authentication methods for the whole tenant.
 <img width="1919" height="1079" alt="Screenshot 2026-06-15 171714" src="https://github.com/user-attachments/assets/e6fb7bb3-7e8b-4a8b-8c91-38ca5a02127e" />
 
### Step 5: Authentication & MFA
### Step 6: Conditional Access
### Step 7: Identity Governance
### Step 8: Excessive Permission Simulation
### Step 9: Entitlement Management
### Step 10: Temporary Access Pass
