# Intrusion Detection and Prevention System (IDPS) – Integrated with n8n

This project is an automated, cloud-based **Intrusion Detection and Prevention System (IDPS)** built using [n8n](https://n8n.io). It checks suspicious IP addresses against **AbuseIPDB**, sends alerts via **Telegram**, and logs threat data to **Google Sheets** — making it easy to monitor and react to abuse in real time.


## 🔁 n8n Workflow Overview

### Node Usage

1. **Webhook** (Trigger)
   - Method: `POST`
   - Receives incoming IP address payloads.

2. **HTTP Request**
   - Makes a `GET` request to **AbuseIPDB API v2** to check the IP's reputation.
   - Headers used:
     - `X-Auth-Token` (API Key)
     - `Accept: application/json`

3. **If**
   - Evaluates the `abuseConfidenceScore` from AbuseIPDB.
     - ✅ If **score > 50** → Proceeds to both **Telegram** + **Google Sheets**
     - ❌ If **score ≤ 50** → Logs only in **Google Sheets**

4. **Google Sheets**
   - Appends threat data into a Google Sheet with the following columns:
     - `Address`
     - `Score`
     - `Country Code`
     - `Domain`

5. **Telegram**
   - Sends an alert using a Telegram bot.
   - Operation: `Leave a chat`
   - [View Bot](https://t.me/XploitNow_Bot)



## Credentials Used

| Service        | Purpose                                | Link                                  |
|----------------|----------------------------------------|---------------------------------------|
| AbuseIPDB      | Check IP reputation                    | [abuseipdb.com](https://abuseipdb.com) |
| Telegram Bot   | Send alerts                            | [@BotFather](https://t.me/BotFather) |
| Google Sheets  | Log IP data                            | Sign in via Google OAuth in n8n       |


## Usage

Trigger this workflow by sending a `POST` request to your webhook URL with a JSON body like:

```json
{
  "ip": "1.2.3.4"
}
