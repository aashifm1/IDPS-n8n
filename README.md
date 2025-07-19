# Intrusion Detect and Prevention System Integrated with n8n

## n8n Integration
### Nodes usage
1. Webhook (Trigger)
   - Method: POST
2. Http Request
   - It uses Abuseipdb's API V2.
   - Method: POST
   - Header: X-Auth-Token, Accept
3. If
   - If it is True, then directs to Telegram and Google Sheet.
   - If it is False, then directs to Google Sheet only.
4. Google Sheets

   It Stores the following data into Google sheets.
   - Address
   - Score
   - Country Code
   - Domain
5. Telegram
   - Operation: Leave a chat
   - Telegram Bot [(Link)](https://t.me/@XploitNow_Bot)

### Credentials Used
- Abuseipdb API V2 [(Link)](https://abuseipdb.com)
- Telegram Bot API [(Link)](https://t.me/@BotFather)
- Google Sheet (Sign in with Google)
