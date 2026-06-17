Azure Cloud Foundation Project Summary Report

1. Project Overview & Resource Deployment
. Selected Azure Region: South Africa North

. Reason for Selection: Geographic proximity to Nigeria, ensuring lowest network latency and high throughput for local applications.

. Core Resources Deployed:
. Resource Group: Oluwasegun_Jacobs_OJ(Location: southafricanorth). Acts as a logical container for related cloud infrastructure.

. Storage Account: foundation1storage/ mystoragedeploytest2026
	. Performance Tier: Standard(Magnetic drives optimized for bulk data access).
	. Replication: Read-access geo-redundant storage(RA-GRS). Automatically copies data across primary( South Africa North) and secondary( South Africa West) regions.
	. Account Kind: StorageV2(General Purpose v2).
. Virtual Machine (IaaS): segun-test-vmn (Size: Standard_D2s_v3, OS: Ubuntu Server 24.04 LTS).

2. Share Responsibility Model Matrix
This matrix defines the clear operational boundaries between Microsoft Azure and the customer for the deployed Storage Account and Virtual Machine assets:

Resource Category
Storage Account (PaaS/IaaS)

Microsoft Azure Responsibilities (Provider)
. Physical data center physical security
. Storage hardware maintenance & replacement
. Underlying network infrastructure protection
. High availability/ SLA commitments

Customer Responsibilities (Oluwasegun)
. Managing IAM access permissions
. Configuring firewalls & network security settings
. Rotating access keys & credentials
. Monitoring data storage usage patterns

Resource Category
Virtual Machine (IaaS)

Microsoft Azure Responsibilities (Provider)
. Physical host hypervisor uptime
. Host hardware & physical networking components
. Facility cooling and backup power

Customer Responsibilities (Oluwasegun)
. Patching the Guest OS(Ubuntu Linux)
. Managing local accounts/SSH keys
. Configuring network security group rules


3. Comprehensive Setup & Account Creation Guide
Phase 1: Identity & Regional Verification
a. Open login.microsoftonline.com, create one! and press Next. Fill out all necessary information
b. Click start and select create one! to configure a new Microsoft account identifier using a personal Gmail address.
c. Fill out my country identifier(Nigeria) and enter a valid local mobile number. 
d. Click Text me and enter the automated SMS verification code to clear the identity check.

Phase 2: Credit Card Verification(Nigerian Banking Solutions)
. Critical Constraint Note: Azure billing engines do not accept local Verve debit cards
. Action Step: Visit a local banking institution to issue a Naira Mastercard
. Process: Input the card number, expiration date, and CVV. Ensure your billing address perfectly matched your bank details. 
. Verification: Azure will make a temporary $1 USD authorization hold to prove the card is valid. This money will be automatically refunded within minutes. 
. Subscription Initialization: Upon card verification, my profile initialized with "Azure subscription 1", carrying credit balance of $200 USD (approximately 300,000 NGN).

4. Azure Portal Navigation Framework
Crucial Interface Locations

. The Global Search Bar(Top Center): The primary navigation tool. Typing any service name(e.g., Subscriptions, Virtual Machines, Resource Groups) bypasses directory hunting.

. The Left Navigation Panel(Portal Menu): Accessed via the three-line hamburger icon. Houses shortcuts to Resource Groups, All Resources, and Microsoft Entra ID.

. The Breadcrumb Trail(Top Left): Tracks your structural location within a resource layout, allowing me to click backward instantly (e.g., Home > Resource Groups > Oluwasegun_Jacobs_OJ).

Directory Synchronization Pathway
To track profile details and directory linkages:
a. Navigate to the top right corner profile icon
b. Select your Default Directory
c. Under the options list, select My Microsoft Account. This redirects my browser to Microsoft.com to manage security, payment methods, and profile telemetry.

5. Custom Azure Dashboard Configuration
To monitor resources continuously, I configured a dedicated visual control center
Steps to Build and Pin Custom Elements
a. Type Dashboard in the top search bar and click it.
b. Click + Create > Blank Dashboard. Name it Cloud-Foundation-Control-Center.
c. To pin resource health, go to Resource Groups > Oluwasegun_Jacobs_OJ. Click the Pin icon (pin to dashboard) in the top right toolbar.
d. To pin cost data, go to Cost Management + Billing > Cost Analysis. Select my desired visualization chart, click the Pin icon, and select my custom dashboard. 
e. I clicked save to lock my dashboard setup.


6. Billing and Cost Management Setup
Understanding the Billing Interface
The Cost Management + Billing workspace aggregates cross-resource billing parameters. It tracks cumulative daily spending and visualizes consumption trends relative to my credit limits.

Step-by-Step Budget Alert Execution
To ensure zero accidental card billing, a strict multi-tier notification model is established:

a. I selected my active subscription and click Budgets > Add
b. Set the amount to $1.00 USD on a Monthly reset cycle.
c. Advance to the Alerts pane. Configure an alert type of Actual Cost at a value of 50%(Triggering an alert when consumption hits $0.50).
d. Why 50% over 75%?: A 50% threshold provides a much earlier warning for low-budget free profiles, allowing me to clean up resources before they exceed the trial balance.
e. I entered my personal email address and phone number under Alert recipients and click Create.

7. Azure Free Tier Limits Matrix
The following list tracks structural service quotas and ceilings provided within the introductory 12-month free usage envelope:

Azure Core Service
Linux Compute(VM)

Free Tier Allotment Quota
750 Hours

Unit/Frequency
Per Month(B1s Size Only)

Post-Limit Charging Type
Standard Pay-As-You-Go hourly rate


Azure Core Service
Windows Compute(VM)

Free Tier Allotment Quota
750 Hours

Unit/Frequency
Per Month(B1s Size Only)

Post-Limit Charging Type
Standard Pay-As-You-Go hourly rate

Azure Core Service
Blob Storage

Free Tier Allotment Quota
5GB

Unit/Frequency
Flat Storage Limit

Post-Limit Charging Type
Per-GB standard monthly tier charge

Azure Core Service
File Storage

Free Tier Allotment Quota
5GB

Unit/Frequency
Flat Storage Limit

Post-Limit Charging Type
Per-GB standard monthly tier charge

Azure Core Service
Azure SQL Database

Free Tier Allotment Quota
250GB

Unit/Frequency
Flat Database Allocation

Post-Limit Charging Type
Standard database
compute hour rate

8. Security Considerations & Policy Mapping
. Microsoft Entra ID Role Mapping: Implemented explicit Role-Based Access Control(RBAC). Standard principal assignments are isolated strictly to Owner (Full delegation privileges), Contributor (Resource modification without access assignment rights), and Reader (Read-only observation).

. Multi-Factor Authentication (MFA): Configured via Entra ID properties. Every administrative identity must authorize changes using the Microsoft Authenticator app or mobile SMS confirmation tokens.

. Azure Enterprise Password Requirements: Mandates a minimum password length of 12 characters, requiring at least three of the following properties: uppercase letters, lowercase letters, numbers, and special characters(@, #, $, etc.).

9. Comprehensive Troubleshooting Section
Scenario A: Entry-Level VM Sizes (B1s/B2s) Are Completely Invisible
. Root Cause: The newer Ubuntu OS images default to Generation 2 and Trusted Launch security protocols. The cheapest B-Series virtual instances run exclusively on older Generation 1(x64) architectures.

. Step-by-Step Fix:
a. Go back to the Basics tab of the VM creation wizard
b. Change the Security type from Trusted launch to Standard.
c. Ensure the VM Generation toggle is flipped to Gen1/
d. Click See all sized; the B1s and B2s families will now appear/

Scenario B: SSH Connections to Your Public IP Fail with "Connection Timed Out"
. Root Cause: The Network Security Group (NSG) firewall rules are blocking incoming connections on port 22, or your local ISP is dropping outbound SSH requests.

. Step-by-step Fix:
a. Navigate to my VM page, open the Networking blade, and click Add inbound port rule.
b. Set the Destination port range to 22, Protocol to TCP, and Action to Allow. Name it Allow-SSH-22 and save.
c. If local network issues persist, use the browser-based Serial Console tool under the Help menu section to log straight into your VM without using an external terminal program.

Scenario C: Deployed Webpage Fails with ERR_CONNECTION_TIMED_OUT
. Root Cause: The firewall is blocking port 80(HTTP), or Nginx is not running inside the Linux instance.

. Step-by-Step Fix:
	a. Add an inbound security group rule mapping destination port 80 to Allow.
	b. Connect to your VM command prompt and run sudo apt update && sudo apt install nginx -y to turn on the background web service


10. External Support Resources & Links
a. Official Azure Free Tier Documentation Portal - azure.microsoft.com/en-us/pricing/purchase-options/azure-account?icid=azurefreeaccount
b. Microsoft Learn: Manage Azure Costs & Budgets -learn.microsoft.com/en-us/azure/cost-management-billing/
c. Azure Architecture Documentation: Shared Responsibility Guidance - learn.microsoft.com/en-us/azure/security/fundamentals/shared-responsibility
