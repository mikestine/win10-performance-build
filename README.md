# win10-performance-build
Configure Windows 10 for process heavy operations like Gaming, Avid Editing, or if you want a really fast machine.  I use this on all my Win10 environments.
1. Create an admin user: admin/notpassword
2. Turn On DHCP
3. Set Time zone/Date/NTP
   - a. Control Panel > Clock and Region > Set the time and date > Internet Time Tab
        - <CHECK> Synchronize with an Internet time server
        - Server: ntp.domain.com
        - <CLICK> [Update now]
4. Install VMWare Tools (Optional: only for VM installs)
   - From VMWare Workstation > VM (Menu) > Install VMWare Tools...  (this should emulate a cd-rom mounting with the software to install)
5. Activate Windows
   - Settings > Update & Security > Activation
6. Update Windows
   - Windows Settings > Update & Security > Windows Update
7. Stop Using Other Computers to get Windows Updates
   - Settings > Update & Security > Windows Update Delivery Optimization > Advanced options ->Delivery Optimization
     - Allow Downloads from other PCs: OFF
8. Disable IPv6
   - Control Panel > Network and Internet > Network Connections
     - Right Click Interface > Properties
     - <UNCHECK> Internet Protocol Version 6
9. Rename Computer
   - Control Panel > System and Security > System > Advanced system settings
     - Computer Name Tab
       - Computer description: WIN10
       - <CLICK> to rename this computer or change its domain or workgroup click change.  [Change...]
10. Turn Off System Restore
    - Control Panel > System and Security > System
      - System Protection Tab
        - <HIGHLIGHT> Local Disk (C:)(System)
        - <CLICK> [Configure...]
        - <SELECT> Disable system protection
11. Turn On Remote Desktop & Remote Assistance
    - Control Panel > System and Security > System
      - Remote Tab
        - <CHECK> Allow Remote Assistance connections to this computer
        - <SELECT> Allow remote connections to this computer
        - <UNCHECK> Allow connections only from computers running Remote Desktop with Network Level Authentication (recommended)
12. Adjust for Best Performance
    - Control Panel > System and Security > System > Advanced Tab >Performance > [Settings...]
    - Visual Effects Tab
      - <SELECT>Adjust for best performance
    - Advanced Tab
      - <SELECT> Adjust for best performance of: Background services
13. High Performance Power Options
    - Control Panel > System and Security > System > Power Options
      - <SELECT> High performance
      - <CLICK> High Performance Change plan settings
        - Turn off the display: Never
        - Put the computer to sleep: Never
        - [CLICK] Change advanced power settings
          - Turn off hard disk after:  0  (This will change to NEVER)
          - Sleep after: Never
        - USB settings > USB selective suspend setting: Disabled
        - PCI Express > Link State Power Management: OFF
        - Processor power management
          - System cooling policy: Active
        - Display > Turn off display after: never
14. Increase NTFS Cache Size to reduce disk access rates.
    - regedit
      - HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\FileSystem
      - NtfsMemoryUsage = 2
15. Stop Windows from Tracking You
    - Windows Settings > Privacy -> General
      - Let Windows track app launches to improve Start and search results: Off
      - Show me suggested content in the Settings app: Off
      - Windows Settings > Privacy -> Activity history
    - <UNCHECK> Let Windows collect my activities from this PC
16. Stop The World from Tracking You
    - Windows Settings > Privacy >
      - Location
        - Location for this device is: OFF
      - Camera
        - Camera access for this device is: OFF
      - Microphone
        - Microphone access for this device is: OFF
      - Notifications
        - Let apps access my notifications: Off
      - Account info
        - Account info access for this device is: OFF
      - Contacts
        - Contacts access for this device is: OFF
      - Calendar
        - Calendar access for this device is: OFF
      - Call history
        - Call history access for this device is: OFF
      - Email
        - Email access for this device is: OFF
      - Tasks
        - Task access for this device is: ON
        - Allow apps to access your tasks: ON
      - Messaging
        - Messaging access for this device is: OFF
      - Radio
      - Let apps control radios: OFF
        b. Other Devices
      - Communicate with unpaired devices: OFF
        c. Background apps
      - Let apps run in the background: ON
      - Turn off all apps running in background
17. Stop Suggestions in the Taskbar
    - Windows Settings > Personalization > Taskbar
      - Combine taskbar buttons: When taskbar is full
        - Start
        - Show suggestions occasionally in Start: On
18. Turn Firewall off
    - Control Panel > System Security > Windows Defender Firewall -> Advanced Settings -> Windows Defender Firewall Properties
      - Domain Profile Tab > Firewall state: Off
      - Private Profile Tab > Firewall state: Off
      - Public Profile Tab > Firewall state: Off
19. Turn Antivirus Off
    - Settings > Update & Security > Windows Security > Virus & thread protection > Virus & threat protection settings
20. Disable Windows Defender Notification Icon
    - Windows Settings > Apps > Startup
      - Windows Defender notification icon: Off
21. Limit Cortana
    - Windows Settings > Cortana >
      - Talk to Cortana
        - Use Cortana even when my device is locked: Off
      - Permissions & History
        - SafeSearch: Off
      - Windows Cloud Search: Off
      - Cortana across my devices
        - Help me pick up where I left of on other devices: Off
22. Developer Mode (Optional: Can be a Security Threat, and only used when machine is for development)
    - Settings > Update & Security > For Developers
      - <SELECT> Developer Mode
23. Show Filename extensions
    - Windows Explorer
      - View Ribbon
      - <CHECK> File name extensions
24. Disable Indexing Drive C
    - Open Windows Explorer -> <SELECT> C:| -> (RIGHT CLICK) Properties
      - <UNCHECK> Allow files on this drive to have contents indexed in addition to file properties
25. Add Telnet Client, TFTP Clients, Printing Services
    - Control Panel > Programs > Turn Window features on or off
      - <CHECK> Telnet Client
      - <CHECK> TFTP Client
      - <CHECK> Print and Document Services > Internet Printing Client
      - <CHECK> Print and Document Services > Windows Fax and Scan
26. Add Software Installers
      - Create folder C:\users\Installers\ and add install files
        - 7zip
        - Adobe Acrobat Reader
        - Chrome
        - Filezilla
        - Firefox
        - HandBrake
        - MediaInfo
        - NMap/ZenMap
        - Notepad++
        - Sysinternals
        - VLC
        - Wireshark
27. Add Portable Apps (that don't require installation)
      - Create folder C:\Portable\  and add files
      - Putty
      - Rufus
      - Microsoft_File_Checksum_Integrity_Verifier
      - RidgecropsFormat32
      - CrystalDiskInfo
28. Remove Unwanted Games & Apps (even though they will come back next windows update)
    - Windows Settings > Apps > Apps & Features
      - Select game
      - <Click> [Uninstall]
```
powershell -c "Get-AppxPackage|Remove-AppxPackage"
```
