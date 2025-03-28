# -EC2-CPU-Monitoring-and-Auto-Alert-System-using-AWS-CloudWatch
# EC2 CPU Monitoring and Auto-Alert System using AWS CloudWatch

## 📌 Project Overview
This project demonstrates how to set up **real-time EC2 CPU monitoring** using AWS CloudWatch. It includes configuring **CloudWatch Alarms** to trigger email alerts when CPU utilization exceeds a threshold. A **Python-based CPU spike simulator** is also provided to test the alert system.

## 🚀 Features
- **Automated CPU Utilization Alerts** – CloudWatch alarms notify users when CPU usage is high.
- **Python-based CPU Load Testing** – Simulates high CPU usage for alert testing.
- **Proactive Monitoring** – Helps identify performance issues before they impact users.
- **Email Notifications via SNS** – Sends real-time alerts on CPU spikes.
- **AWS CloudWatch Metrics Integration** – Monitors EC2 instance performance effectively.

## 🏗️ Tech Stack
- **Amazon Web Services (AWS)**
  - CloudWatch
  - EC2
  - Simple Notification Service (SNS)
- **Python** (for CPU load simulation)

---

## 🛠️ Setup Instructions

### Step 1: Create an EC2 Instance
- Launch a new EC2 instance from the AWS Console.

### Step 2: Enable Detailed Monitoring
- Go to the **Monitoring** tab in your EC2 instance.
- Click on **Manage detailed monitoring** and enable it.

### Step 3: Simulate a CPU Spike
SSH into the EC2 instance and run the following:

```bash
nano cpu_spike.py
```
Paste the following Python script into the file:

```python
import time

def simulate_cpu_spike(duration=30, cpu_percent=80):
    print(f"Simulating CPU spike at {cpu_percent}%...")
    start_time = time.time()
    target_percent = cpu_percent / 100
    total_iterations = int(target_percent * 5_000_000)
    
    for _ in range(total_iterations):
        result = 0
        for i in range(1, 1001):
            result += i
    
    elapsed_time = time.time() - start_time
    remaining_time = max(0, duration - elapsed_time)
    time.sleep(remaining_time)
    print("CPU spike simulation completed.")

if __name__ == '__main__':
    simulate_cpu_spike(duration=30, cpu_percent=80)
```
Run the script to generate a CPU spike:
```bash
python3 cpu_spike.py
```

### Step 4: Set Up CloudWatch Monitoring
- Open **AWS CloudWatch** in the AWS Console.
- Click on **Metrics** > **EC2** > **Per-Instance Metrics**.
- Select your EC2 instance and monitor **CPU Utilization**.

### Step 5: Create an Alarm
- In CloudWatch, go to **Alarms** > **Create Alarm**.
- Select **CPUUtilization** as the metric.
- Set the condition (e.g., CPU utilization > 50%).

### Step 6: Configure Email Notifications (SNS)
- Create an **SNS topic** and subscribe with your email.
- Confirm the email subscription from your inbox.
- Attach the SNS topic to the CloudWatch Alarm.

### Step 7: Receive Alerts
- Once the CPU spike is triggered, an email alert will be sent.

---

## 📷 Expected Output
✅ CloudWatch metrics showing CPU spikes.  
✅ Email notifications on high CPU usage.

## 🎯 Use Cases
- **Proactive System Monitoring** – Prevents performance degradation.
- **Incident Response Automation** – Alerts teams on high CPU usage.
- **Scalability Testing** – Ensures infrastructure handles variable loads.

## 📜 License
This project is open-source and available under the MIT License.

---

## 📩 Contact
For any queries or suggestions, feel free to reach out!
