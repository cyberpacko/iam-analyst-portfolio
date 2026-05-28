# Project 1: Microsoft Entra ID, IAM provisioning, technical documentation


## 3\. Solution Architecture

The following end-to-end architecture eliminates manual touchpoints by connecting the HRIS directly to Entra ID Governance, automating provisioning decisions, and centralising all identity events in Microsoft Sentinel for audit evidence.

WORKDAY (HRIS)  
| SCIM 2.0 / Graph API  
v  
ENTRA ID PROVISIONING (Inbound SCIM)  
|  
v  
LIFECYCLE WORKFLOWS  
+-----------+-----------+  
| | |  
JOINER MOVER LEAVER  
| | |  
+-----+-----+-----------+  
|  
+-----+-----+------------------+  
| | |  
ACCESS ENTITLEMENT PIM  
PACKAGES MANAGEMENT (JIT)  
(dept) (Access Reviews) (Privileged)  


