AWS Networking — EIP + Inbound + Outbound Rules
🟦 EIP – Elastic IP

Elastic IP (EIP) is a static Public IPv4 address in AWS that:

✔ Does not change when EC2 stops/starts ✔ Can be attached/detached between instances ✔ Used for public-facing services

Why needed?

Normal Public IP changes every restart → breaks website access & DNS.

Where used?
Use Case	Reason
Web Server	Same IP for customers always
Bastion Host	Admin access for private instances
NAT Instance	Private instances reach the internet
VPN Gateway	Stable IP for secure connection
How to use in AWS?

✔ Go to EC2 Console → Elastic IPs → Allocate ✔ Select EIP → Associate with EC2 instance or ENI ✔ Allow necessary ports in Inbound Rules

📝 Note: EIP is free only when attached and instance is running.

🔐 Security Groups – AWS Firewall for EC2

Security Groups (SG) decide what traffic is allowed:

Inbound  = What CAN come inside instance?
Outbound = What CAN go outside instance?
⬇️ Inbound (IN) Rules — Traffic Entering EC2

Controls: ✔ Port ✔ Protocol ✔ Source IP

Port	Protocol	Source	Meaning
22	SSH	My Public IP	Secure admin login
80	HTTP	0.0.0.0/0	Public website access
443	HTTPS	Anywhere	Encrypted site access
3306	MySQL	Only App Server SG	Protect DB from internet

📌 Default: Block everything, you must allow explicitly.

Example Flow:

Internet → Allow 80 → Web Server (EC2)
Admin   → Allow 22 (My IP) → EC2
App SG  → Allow 3306 → Database EC2
⬆️ Outbound (OUT) Rules — Traffic Leaving EC2

Used for: ✔ Package updates ✔ API calls ✔ Database connection ✔ Internet via NAT

Example Rule	Meaning
Allow all outbound	Normal EC2 usage + internet access
Only allow DB port	EC2 can only reach specific DB

📌 Default AWS rule → Allow All Outbound

🔄 Security Group Flow (Visual)
                ⬇ Inbound Allowed
Internet ------------------> EC2 Instance
                ⬆ Outbound Allowed
🧠 Interview Section
Q1️⃣ Security Group vs NACL
Security Group	NACL
Instance-level	Subnet-level
Stateful	Stateless
Return traffic auto allowed	Must allow return traffic manually
Only ALLOW rules	ALLOW + DENY rules
Q2️⃣ Most common ports
Service	Port
SSH	22
HTTP	80
HTTPS	443
MySQL	3306
PostgreSQL	5432
🎯 Hands-On Example — Deploy Public EC2

✔ Launch EC2 (Ubuntu) ✔ Allocate & Associate EIP ✔ Create SG:

Inbound:

80 (HTTP) → Anywhere

22 (SSH) → My IP only

Outbound:

Allow All (default)

✔ Hit EIP in browser → Website live 🎉



Which option do you want? 😊

ChatGPT can make mistakes. Check important info. See Cookie Preferences.
