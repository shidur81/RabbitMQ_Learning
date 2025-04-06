
# Installing RabbitMQ in WSL (Windows Subsystem for Linux)

## Step 1: Install Erlang (Dependency)

RabbitMQ requires Erlang, so install it first.

### For Ubuntu (or Debian-based distros)

**Update package list and install required dependencies:**

```bash
sudo apt update && sudo apt install -y curl gnupg apt-transport-https
```

**Add Erlang repository and install Erlang:**

```bash
curl -fsSL https://packages.erlang-solutions.com/ubuntu/erlang_solutions.asc | sudo tee /usr/share/keyrings/erlang.gpg > /dev/null

echo "deb [signed-by=/usr/share/keyrings/erlang.gpg] https://packages.erlang-solutions.com/ubuntu $(lsb_release -cs) contrib" | sudo tee /etc/apt/sources.list.d/erlang.list

sudo apt update
sudo apt install -y erlang
```

**Verify Erlang installation:**

```bash
erl
```

If you see the Erlang shell (`1>`) running, it's installed correctly. Exit with:

```erlang
q().
```

---

## Step 2: Install RabbitMQ

**Add RabbitMQ repository:**

```bash
curl -fsSL https://packagecloud.io/rabbitmq/rabbitmq-server/gpgkey | sudo tee /usr/share/keyrings/rabbitmq.gpg > /dev/null

echo "deb [signed-by=/usr/share/keyrings/rabbitmq.gpg] https://packagecloud.io/rabbitmq/rabbitmq-server/ubuntu/ $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/rabbitmq.list
```

**Update packages and install RabbitMQ:**

```bash
sudo apt update
sudo apt install -y rabbitmq-server
```

**Enable RabbitMQ service:**

```bash
sudo systemctl enable rabbitmq-server
```

**Start RabbitMQ:**

```bash
sudo systemctl start rabbitmq-server
```

**Verify RabbitMQ status:**

```bash
sudo systemctl status rabbitmq-server
```

If it's running, you should see output similar to:

```
Active: active (running)
```
```