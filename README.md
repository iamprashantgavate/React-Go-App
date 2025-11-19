# 🚀 Employee Management System (Full Setup Guide)

This project consists of:
- 🐘 PostgreSQL Database  
- 🧩 Go (Golang) Backend  
- 🖥️ ReactJS Frontend  

Everything below is arranged in the correct order:
1️⃣ **Database Setup** → 2️⃣ **Backend Setup** → 3️⃣ **Frontend Setup**



## ▶️ Run file locally
```bash
source ./run.sh
```

---

# 🐘 1. PostgreSQL Installation & Setup

## ▶️ Install PostgreSQL 15
```bash
sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
wget -qO - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
sudo apt update
sudo apt install postgresql-15 -y
```

---

## ▶️ Create Database & User
```bash
sudo -i -u postgres
psql
```

```sql
CREATE DATABASE employee_db;
CREATE USER admin3 WITH PASSWORD '12345678';
```

---

## ▶️ Grant Privileges
```sql
GRANT ALL PRIVILEGES ON DATABASE employee_db TO admin3;
\c employee_db
GRANT ALL ON SCHEMA public TO admin3;
GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO admin3;
GRANT ALL PRIVILEGES ON ALL SEQUENCES IN SCHEMA public TO admin3;

ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT ALL ON TABLES TO admin3;
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT ALL ON SEQUENCES TO admin3;
```

---

## ▶️ Exit PostgreSQL
```sql
\q
exit
```

---

## ▶️ Export Environment Variables
```bash
export DB_HOST=localhost
export DB_PORT=5432
export DB_NAME=employee_db
export DB_USER=admin3
export DB_PASSWORD=12345678
export ALLOWED_ORIGINS="*"
```

---

# 🧩 2. Backend (Go 1.19)

### **Description**
- Written in **Go 1.19**
- Runs on **port 8080**

---

## ▶️ Install Go 1.19
```bash
wget https://go.dev/dl/go1.19.13.linux-amd64.tar.gz -O /tmp/go1.19.13.linux-amd64.tar.gz && sudo rm -rf /usr/local/go && sudo tar -C /usr/local -xzf /tmp/go1.19.13.linux-amd64.tar.gz && echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc && echo 'export GOPATH=$HOME/go' >> ~/.bashrc && echo 'export PATH=$PATH:$GOPATH/bin' >> ~/.bashrc && source ~/.bashrc && go version
```

---

## ▶️ Install Dependencies
```bash
go get ./backend/
```

---

## ▶️ Run Backend Server
```bash
go run ./backend/main.go
```

---

# 🖥️ 3. Frontend (ReactJS)

### **Description**
- ReactJS (Node 14.17.0)
- Runs on **port 3000**

---

## ▶️ Install NVM
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```

---

## ▶️ Load NVM
```bash
source ~/.bashrc
```

---

## ▶️ Install Node.js 14.17.0
```bash
nvm install 14.17.0
nvm use 14.17.0
nvm alias default 14.17.0
```

---

## ▶️ Verify Versions
```bash
node -v
npm -v
```

---

## ▶️ Install Dependencies
```bash
npm install
```

---

## ▶️ Start Frontend
```bash
npm start
```

---

# ✅ Project Setup Complete

Your system now includes:
- PostgreSQL DB (employee_db)
- Go backend (port 8080)
- React frontend (port 3000)
- Access Application - http://localhost:3000

Everything is ready to use 🎉

