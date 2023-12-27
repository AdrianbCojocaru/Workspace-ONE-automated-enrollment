# Synopsys
Enroll Windows devices in Workspace ONE automatically, without any user interaction.

# Description
For companies that do not use Entra ID, the Workspace ONE enrollment process is interactive and therefore users can opt-out.  
This script aims to cover this limitation and provide an automatic enrollment process which does not require user interaction.  
It is designed to run on the device that it is about to be enrolled. It makes an API call against company's private endpoints in order to authenticate the device and then get the Workspace ONE enrollment token.  
This token will be used as a property during the silent installation of the Intelligent Hub  
  
A non-interactive solution will:
 - simplify the enrollment process
 - allow for devices which lost the Workspace ONE connectivity to be easily re-enrolled
 - allow for bulk enrollment

# Application & Systems Data Flow Diagram
![alt text](https://github.com/AdrianbCojocaru/Workspace-ONE-automated-enrollment/raw/main/Diagram.drawio.png "Workspace-ONE-automated-enrollment")

# Data Flow Description
| Step name     | Associated description |
| ------------- | ---------------------- |
| 1. Rest API call to the OAuth Server | REST API call to the OAuth server using the embedded OAuth client_id and client_secret. |
| 2. OAuth token | The previous call will return the OAuth token [string]. |
| 3. Rest API call to the Private API Endpoint| REST API call to the Private API Endpoint using the OAuth token and the Hardware Id of the device that the script is running on. |
| 4. Get device owner and Workspace ONE secret | The previous call will return the email address for the device owner [string] and the Workspace ONE secret [string]. |
| 5. REST API call to Workspace ONE Token Service | REST API call to Workspace ONE Token Service using the Workspace ONE secret. |
| 6. Get the Workspace One UEM OAuth token | The previous call will return the token required for OAuth authentication to Workspace ONE [string]. |
| 7. REST API call to Workspace ONE | REST API call to Workspace ONE UEM using the OAuth token (Step 4) and the user’s email address (Step 2). |
| 8. Get the Workspace ONE enrollment token | The call returns the enrollment token [string]. |
| 9. Enroll the device into Workspace ONE | The enrollment token will be used as part of the Workspace ONE client installation command line. After enrollment, the system will be managed by Workspace ONE and will receives the security controls. |


