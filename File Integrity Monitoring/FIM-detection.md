OBJECTIVE - 

  To demonstrate how Wazuh File Integrity Monitoring (FIM) detects file creation, modification, and deletion events on an endpoint.

SETUP - 

  Wazuh Manager: Server running in VMware
  Agent: Windows 10 host (DESKTOP-GSG0OEO)
  Monitored Path: c:\users\ACER\Desktop

ATTACK / SIMULATION STEPS - 

  File Creation: 

    Created a new folder named wazuh project and inside it created a new file named fim.txt.

  Event Detected:

    Aug 24, 2025 @ 15:19:08.393
    Agent: DESKTOP-GSG0OEO
    File: c:\users\acer\desktop\wazuh project\fim.txt
    Action: added
    Description: File added to the system.
    Rule ID: 554
    Level: 5


  File Modification:

    Modified contents of fim.txt.

  Event Detected:

    Aug 24, 2025 @ 15:19:14.947
    Agent: DESKTOP-GSG0OEO
    File: c:\users\acer\desktop\wazuh project\fim.txt
    Action: modified
    Description: Integrity checksum changed.
    Rule ID: 550
    Level: 7


  File Deletion

    Deleted fim.txt from the monitored folder.

  Event Detected:

    Aug 24, 2025 @ 15:19:28.419
    Agent: DESKTOP-GSG0OEO
    File: c:\users\acer\desktop\wazuh project\fim.txt
    Action: deleted
    Description: File deleted.
    Rule ID: 553
    Level: 7

OBSERVATION - 

  Wazuh successfully detected all three events (added, modified, deleted) with corresponding rule IDs and alert levels.
  This validates that FIM is working as expected on the Windows agent.
  Alerts were forwarded to the Wazuh dashboard for visibility and correlation.

DETECTION USE CASE - 

  MITRE ATT&CK: T1070.004 – Indicator Removal on Host: File Deletion
  Use Case: Detecting unauthorized modifications or deletions of critical files in monitored directories.
  
