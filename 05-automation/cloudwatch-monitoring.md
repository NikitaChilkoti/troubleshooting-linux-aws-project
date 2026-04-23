# CloudWatch Monitoring

## What are we doing?

In this section, we set up monitoring using AWS CloudWatch.

Because why wait for the system to fail, when we can:

* track system performance
* detect unusual behavior
* get alerts

---

## What is CloudWatch?

CloudWatch is an AWS service used to monitor:

* CPU usage
* network activity
* system performance

---

## What will we monitor?

For this project, we monitor CPU Utilization - this is the most important for sure.

---

## Step 1: Open CloudWatch

* Go to AWS Console
* Search for **CloudWatch**
* Click **Metrics**

---

## Step 2: Select EC2 Metrics

* Click **EC2**
* Click **Per-Instance Metrics**
* Select your EC2 instance

---

## Step 3: View CPU Usage

You will see a graph for:

CPU Utilization

This shows how much CPU your server is using.

---

## Step 4: Create an Alarm

Click **Create Alarm**

---

## Step 5: Configure Alarm

* Metric: CPUUtilization
* Threshold: Greater than 70%
* Period: 5 minutes

---

## Step 6: Getting notification over email

To receive alerts, we have to connect the alarm to SNS.

* Create a new SNS topic (for example: ec2-alerts)
* Add your email as a subscription
* Confirm the email from your inbox
* Select this SNS topic while creating the alarm

Now, when the threshold is crossed, you will receive an email alert.

---

## What does this alarm do?

If CPU usage goes above 70%:

* CloudWatch triggers an alert

This helps detect:

* high load
* stuck processes
* system stress

---

## Why monitoring is important?

Without monitoring you only know after failure

With monitoring you detect issues early. The most critical difference to get back right quicker and firmer.

---

## Example Use-Case

If CPU suddenly spikes:

* check running processes
* identify high usage
* fix the issue

---

## Key Learning

* Monitoring helps prevent failures
* CloudWatch gives visibility into system behavior

---

## So, monitoring helps in detecting the issue early, thus early rectification can be done. How about we automate the deployment as well? Through GitHub Actions.
