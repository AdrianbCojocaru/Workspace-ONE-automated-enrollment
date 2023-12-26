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



