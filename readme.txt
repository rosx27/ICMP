### Introduction
This program is designed for monitoring network performance and diagnosing connectivity issues related to specific hosts, such as smcs.ph (LIMS). It performs various network tests including ping, traceroute, and speed tests, and provides a user-friendly interface for interaction.

### Issue
The Laboratory Information Management System (LIMS) at smcs.ph often experiences slow connection speeds, causing delays and disruptions in daily operations. This program aims to monitor and log network performance to identify potential causes and patterns of these slowdowns.

### Purpose
The primary purpose of this program is to:
1. Continuously monitor network performance by performing periodic ping, traceroute, and speed tests.
2. Identify and log network issues, particularly focusing on the connectivity of smcs.ph (LIMS).
3. Provide an easy-to-use graphical interface for initiating tests and viewing logs.
4. Automatically send email reports with detailed logs and performance metrics to specified recipients.

### Method
The program follows these methods to achieve its objectives:
1. **Ping Test**: Measures the round-trip time for messages sent from the host to a specific destination (e.g., smcs.ph) to determine the latency.
2. **Traceroute**: Identifies the route taken by packets across an IP network and measures the time taken for each hop.
3. **Speed Test**: Measures the download and upload speeds by downloading and uploading files from a specified server.
4. **Website Response Check**: Measures the response times for specified websites to assess their availability and performance.
5. **Email Reporting**: Compiles the test results into a log file, zips the logs, and sends them via email for large data analysis.

### Instruction for Developers
1. **Setup**: Ensure all dependencies are installed. This includes the required Python libraries such as `icmplib`, `requests`, `pyzipper`, `tkinter`, `ttkbootstrap`, and others.
2. **Configuration**: 
   - Edit the global variables in the script to customize the list of hosts to ping and traceroute (`hosts`), the premises IPs (`premises_ips`), and email settings (`sender_email`, `sender_password`, `receiver_email`, etc.).
   - Place a `config.json` file in the same directory as the script with the following content:
     ```json
     {
         "sent": false
     }
     ```

### Instruction for Users
1. **Running the Tool**:
   1.1. There are three ways to run the ICMP Monitoring Tool to start the graphical interface:
       1.1.1. Run the `ICMP` shortcut on the Desktop.
       1.1.2. Run the `ICMP.exe` located in `C:\Program Files\Ping`.
       1.1.3. Restart the computer. The ICMP.exe has a shortcut in `C:\Users\<current user>\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup` and will execute automatically.
   1.2. Use the button to report LIMS slowdonws. When this button is clicked, this will be recorded in the log files. This qualitative measurement will be used to compare to the quantitative measurements (ping, traceroute, speed tests) to establish a boundary of how slow a slow connection is.
   1.3. The program will automatically perform the tests at specified intervals (routine: 30 minutes; when the button is clicked: immediate, three (3) consecutive readings) and log the results.
   1.4. The program will also take into account the location of the user through the use of IP addresses. The IP address of the user is compared to the list of known IP addresses located in the laboratory; these known IP addresses will be marked as "In-house" while the unknown IP addresses are marked "On-site". This will further help diagnose where the issue is coming from.
2. **Viewing Logs**: The logs can be viewed in the text area of the GUI. They are also saved in a log file located at `C:\Users\<logged in user>\Downloads\Ping\` with the naming convention `<computer_name>_<date>_ICMP-result.txt`.
3. **Email Reporting**: If the `send.txt` control file located in GitHub repository indicates that an email should be sent (`send_status.text` equals "1" or "2"), the program will compile the logs into a zip file and send it to the specified recipient.

### Notes
- Ensure that the `config.json` and `ICMP.exe` files are located in the `C:\Users\<logged in user>\Downloads\Ping\` directory to avoid errors.
- The email functionality relies on correct SMTP settings and valid email credentials.