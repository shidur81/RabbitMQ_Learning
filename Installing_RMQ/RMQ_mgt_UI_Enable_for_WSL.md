
# Enabling RabbitMQ Management UI for a WSL Instance

## Step 1: Get the IP address of the WSL instance

> **Note**: WSL2 dynamically assigns a new IP address every time it restarts.

**Command:**
```bash
hostname -I
```

**Example Output:**
```
172.25.38.122
```

---

## Step 2: Create a New Admin User (More Secure)

> The default `guest` user is restricted to logging in only from `localhost`.  
Create a new user to log in from your browser.

```bash
sudo rabbitmqctl add_user myadmin mypassword
sudo rabbitmqctl set_user_tags myadmin administrator
sudo rabbitmqctl set_permissions -p / myadmin ".*" ".*" ".*"
```

---

## Step 3: Restart RabbitMQ

```bash
sudo systemctl restart rabbitmq-server
```

---

## Step 4: Access the RabbitMQ Management UI

Open the browser and go to:

```
http://172.25.38.122:15672
```

**Login credentials:**

- **Username:** `myadmin`  
- **Password:** `mypassword`

---

This will connect you to the RabbitMQ instance running inside your WSL environment.
