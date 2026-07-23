# adfspectramicros
Application Development Framework using Oracle14c jdeveloper studio, oracle 19c database for 3 days. Developing microservices using spectra (Rancher desktop) for installing single note using kubernetes.

Trainer machine config:
o deploy a shared central database training model, your ASUS Windows Laptop will serve as both the Shared Database Host and the trainer machine. The Student Mac Machines (16GB RAM / 512GB SSD) will act as light development clients that connect to your laptop over the local network (LAN).

 software installation and network routing setup blueprint
 =========================================================

Part 1: Trainer Machine Setup (ASUS Windows Laptop)
****************************************************

Your laptop will run the actual Oracle Database instance alongside your own instance of JDeveloper.
 
+------------------------------------------------------+

|             ASUS Windows Laptop (Trainer)            |
|  +--------------------+      +--------------------+  |
|  |   JDeveloper 14c   |      |  Oracle DB (PDB)   |  |
|  +--------------------+      +--------------------+  |
+------------------------------------------------------+
           |                              ^
           v (Local JDBC Connect)         | (Remote JDBC Connect via LAN)
     [ localhost:1521 ]             [ 192.168.1.XX:1521 ]
                                          ^
                                          |
                        +-----------------+-----------------+

                        |                                   |
           +-------------------------+         +-------------------------+
           |   Student Mac 01 (M-series)|         |   Student Mac 02 (M-series)|
           +-------------------------+         +-------------------------+

1. Pre-requisite: Java Development Kit (JDK)Download: Get Oracle JDK 17 (Windows x64 Installer).
Install: Run the .exe file. It installs to C:\Program Files\Java\jdk-17.
Environment Variable: Set JAVA_HOME in Windows System Properties pointing to your JDK 17 folder. Add %JAVA_HOME%\bin to your system PATH

2. Download: Download Oracle Database 23ai Free or 21c Express Edition (XE) for Windows.Install: Run the setup file. Set a master database password you will remember (e.g., Welcome_ADF14c).Database Structure: The installation automatically creates a Container Database (CDB) and a default Pluggable Database (PDB) named FREEPDB1 or XEPDB1.Initialize Student Schemas: Open SQL Developer or SQL*Plus, connect as SYS AS SYSDBA, and execute the admin script provided earlier to provision accounts STU01, STU02, etc., directly inside the PDB

3. JDeveloper 14c SetupDownload: Grab the Oracle JDeveloper Studio 14c (14.1.2.0) generic installer archive.Install: Open Command Prompt as Administrator and target the .jar installer via JDK 17:cmd"C:\Program Files\Java\jdk-17\bin\java.exe" -jar V1045138-01.jar

OR Wizard: Follow the visual prompts to configure your installation directory (e.g., C:\Oracle\Middleware\Oracle_Home)

4. Crucial Trainer Actions: Network & Firewall AccessTo allow student Macs to talk to your laptop database, execute these steps:Find Your IP: Open Command Prompt, type ipconfig. Locate your Active LAN IPv4 Address (e.g., 192.168.1.50). Write this down.Open Database Listener Port: Open Windows Defender Firewall with Advanced Security. Click Inbound Rules -> New Rule. Select Port, choose TCP, enter Specific Local Ports: 1521. Choose Allow the connection, check all profiles, and name it Oracle_DB_Listener.Configure Listener Network Scope: Open your database home directory path (e.g., ...\dbhome_1\network\admin\listener.ora). Ensure the HOST value is either set to your active laptop machine name or 0.0.0.0 rather than strictly restricted to localhost. Restart the Windows Service OracleOraDB23Home1TNSListener.

Part 2: Student Machine Setup (Mac 16GB / 512GB)Since the student Macs run on Apple Silicon or modern macOS ecosystems, they will avoid native database virtualization friction entirely. They only need a lightweight local Java execution environment.

1. Native macOS Java 17 InstallationDownload: Download the Oracle JDK 17 macOS Arm64 DMG Installer (or x64 if utilizing older Intel Macs).Install: Mount the .dmg file and follow the standard macOS package installation wizard.Verification: Open Terminal and type java -version. It should output java version "17.x.x".2. JDeveloper 14c Setup on macOSDownload: Download the same Oracle JDeveloper Studio 14c Generic Installer JAR file.Install: Open Terminal, navigate to your Downloads folder, and trigger the generic installation jar using your native Mac Java path:bash/usr/libexec/java_home -v 17 --exec java -jar V1045138-01.jar
Use code with caution.Workspace Mapping: Complete the Oracle Universal Installer. Choose a clean directory path inside their home workspace directory (e.g., /Users/username/Oracle/Middleware/Oracle_Home).3. Network Binding to Trainer DatabaseOn Day 1, have students open JDeveloper 14c on their Mac.Choose View -> Resources -> IDE Connections -> Database -> New Database Connection.Configure the exact properties pointing to your ASUS trainer laptop:+-------------------+--------------------------------------------+

| Connection Property | Student Input Value                        |
+-------------------+--------------------------------------------+

| Connection Name   | HrConn                                     |
| Connection Type   | Oracle (JDBC)                              |
| Username          | STU01 (Incremented per student seat)       |
| Password          | Welcome_ADF14c                             |
| Host Name         | 192.168.1.50 (Your ASUS Laptop LAN IP)      |
| Port              | 1521                                       |
| Service Name      | FREEPDB1 (Or XEPDB1 depending on version)  |
+-------------------+--------------------------------------------+

           


           
