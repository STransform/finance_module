# OTech-ERP

This system consist of finance modules. Initially, it is launched with the HRMS module. Now we started customizing finance modules.integration will be done at a later stage.

## Technology stack
- Python: Programming language
- JS: Client-side interactions and dynamic functionalities
- owl: Odoo Web library (framework)
- Werkzeug: Web Server
- QWeb: templating engine(generating HTML and XML views)
- Bootstrap: CSS framework
- XML-RPC: API and Integration
## Finance modules consists of the following submodules
- Invoice
- Accounting
- Customer
- Dashboard
- Folow-ups
- Reporting
- Payment
   

### Prerequisites
 ```bash
- Prerequisites or dependencies (Python, PostgreSQL ,XML,JS,OWL,OS)
 ```
### Installation Steps

1. **Update The System:**  
```bash
sudo apt update
```
2. **Add System User:**
```bash
sudo useradd -m -d /stransform/finance -U -r -s /bin/bash finance
```
2. **Install Dependencies:**
```bash
   sudo apt install build-essential wget git python3-pip python3-dev python3-venv python3-wheel libfreetype6-dev libxml2-dev libzip-dev libsasl2-dev python3-setuptools libjpeg-dev zlib1g-dev libpq-dev libxslt1-dev libldap2-dev libtiff5-dev libopenjp2-7-dev
```
3. **Install dependencies:**
```bash
sudo apt install postgresql
```
4. **add a new postgresql use:**
```bash
sudo su - postgres -c "createuser -s finance"
```
3. **Install dependencies:**
 ```bash
 sudo apt install postgresql
```
4. **add a new postgresql use:**
```bash
sudo su - postgres -c "createuser -s finance"
```
5. **Install Wkhtmltopdf:**
```bash
sudo apt install wkhtmltopdf
```
6. **wkhtmltopdf --version:**
```bash
 pip install -r requirements.txt
```
7. **install Odoo under that username:**
 ```bash
 sudo su - otechuser
```
8. **clone the repository:**
```bash
 pgit clone https://github.com/STransform/otes.git
```
9. **clone the repository:**
```bash
pgit clone https://github.com/STransform/otes.git
```
10. **create a new python virtual environment:**
```bash
    python3 -m venv odoo16-venv
```
11. **activate:**
    ```bash
    source odoo16-venv/bin/activate
    ```
12. **install Odoo:**
```bash
    pip3 install wheel
    pip3 install -r requirements.txt
    deactivate
    mkdir /stransform/finance/finance/custom-addons
    exit
```
13. **Create database systemd unit file**
```bash 
sudo nano /etc/finance.conf
```
14. **Copy and save :**
```bash 
   [options]
admin_passwd = .....
db_host = False
db_port = False
db_user = finance
db_password = False
addons_path = /stransform/finance/finance/finance-addons,/stransform/finance/finance/custom-addons
xmlrpc_port = 8181
```
15. **Create Odoo Systemd Unit file:**
```bash
sudo nano /etc/systemd/system/finance.service
```
16. **Copy and save :**
```bash
 [Unit]
Description=Odoo16
Requires=postgresql.service
After=network.target postgresql.service
[Service]
Type=simple
SyslogIdentifier=odoo16
PermissionsStartOnly=true
User=otechuser
Group=otechgroup
ExecStart=/stransform/finance/odoo16-venv/bin/python3 /stransform/finance/finance/odoo-bin -c /etc/finance.conf
StandardOutput=journal+console
[Install]
WantedBy=multi-user.target
```
17. **Reload:**
```bash
sudo systemctl daemon-reload
```
18. **Start service:**
```bash
sudo systemctl start finance
```
    
10. **Check status:**
```bash
sudo systemctl status finance
```
10. **Author:**
```bash
STransform
```

10. **Author:**
```bash
S Transform
```

