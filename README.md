# FutureIntern_CYS_03
Steps to Perform a Sniffing Attack Using Wireshark
1. Setup Wireshark
1.Download and install Wireshark from the official website.
2.Open Wireshark with administrative privileges to capture network traffic effectively.

2. Start Capturing Network Traffic
1.Identify your network interface: 
1.From the Wireshark interface, select the appropriate network interface (e.g., Ethernet, Wi-Fi).
2.Start the capture: 
1.Click Start Capturing Packets (the blue shark fin icon).
2.Wireshark begins to record all network traffic on the selected interface.

3. Interact with the Target Website
1.Open a browser and go to http://testphp.vulnweb.com/.
2.Navigate to the login page of the website.
3.Enter the credentials: 
1.Username: admin
2.Password: admin
4.Submit the form.

4. Filter HTTP Packets in Wireshark
1.In Wireshark’s filter bar, type: 
http
2.This filters only HTTP traffic, making it easier to locate the login request.
3.Look for HTTP POST Requests: 
1.Locate a packet with the HTTP POST method, as it typically sends form data (e.g., username and password) to the server.

5. Analyze the HTTP Packet
1.Find HTTP Status Code 200 (OK): 
1.Select a packet with the 200 OK status, indicating a successful transaction.
2.Right-click the packet and choose: 
1.Follow > TCP Stream.
3.Inspect the TCP stream for the credentials: 
1.Wireshark displays the HTTP request and response in plain text.
2.Look for the POST data in the request (e.g., username=admin&password=admin).

6. Results
The username (admin) and password (admin) entered in the login form will be visible in plain text within the HTTP request.
Example from the TCP Stream: 
POST /login.php HTTP/1.1
Host: testphp.vulnweb.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 27

username=admin&password=admin


Key Observations
HTTP is insecure: Data sent over HTTP is unencrypted, making it vulnerable to sniffing attacks.
Credentials in plain text: Any sensitive information submitted via HTTP is exposed to anyone capturing the network traffic.
