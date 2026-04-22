## EC2 Setup (Step-by-Step)

### In this step, we are creating a a cloud server and will install a web server (NGINX).

EC2 is just a computer running in the cloud that we can access from anywhere.

---

## Step 1: Launch EC2 Instance

Go to AWS → EC2 → Click **Launch Instance**

### Fill these details:

* **Name:** linux-troubleshooting-server (It can be anything, just that more aligned looks more professional)
* **AMI:** Ubuntu
* **Instance type:** t2.micro (Choose Free Tier instance type, and get yourself an icecream, hehe.)
* **Key Pair:** Create and download `.pem` file (You can also use already 

---

## Step 2: Storage

* Keep default (8 GB is enough)

---

## Step 3: Security Group (VERY IMPORTANT)

Add these inbound rules:

| Type | Port | Purpose           |
| ---- | ---- | ----------------- |
| SSH  | 22   | Connect to server |
| HTTP | 80   | Access website    |

I took help from chatGPT for this table :)

You know why is this important?
* Without SSH → you cannot connect
* Without HTTP → website will not open

---

## Step 4: Connect to EC2

Open terminal (Git Bash or any terminal)

Run:

```
ssh -i your-key.pem ubuntu@your-public-ip
```

---

## First Time Connection

You may see:

Are you sure you want to continue connecting?

Type:
```
yes
```

---

## Step 5: Update the Server

Run:

```
sudo apt update && sudo apt upgrade -y
```

---

## Step 6: Install Basic Tools

```
sudo apt install nginx git curl htop net-tools python3 python3-pip -y
```

---

## Why are we installing these?

* nginx → web server
* git → for GitHub
* curl → test requests
* htop → monitor system
* net-tools → network debugging
* python → run backend app

---

## Step 7: Start Nginx

```
sudo systemctl start nginx
sudo systemctl enable nginx
```

---

## Step 8: Check Status

```
systemctl status nginx
```

You should see:

```
active (running)
```

---

## Step 9: Test in Browser

Open:

```
http://your-public-ip
```

You should see:
**Welcome to nginx page**

---

## What You Learned

* How to create a cloud server (EC2)
* How to connect using SSH
* How to install tools
* How to run a web server

---

## Common Mistakes

SSH not working → Check key permission `chmod 400 your-key.pem`

Website not opening → Check port 80 is allowed in Security Group

---

## Finally! We have Nginx running on our EC2 instance. Next setup is [Flask app](../02-setup/flask-app.md)
