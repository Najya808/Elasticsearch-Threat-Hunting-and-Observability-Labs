# Lab 26: Alerting & Actions in Kibana

## Objectives
- Understand how to create alerts in Kibana.
- Learn to configure actions for alerts.
- Set up an email connector for notifications.
- Validate the alerting setup by receiving a notification.

## Prerequisites
- Basic knowledge of Kibana and Elastic Stack.
- Access to a Kibana instance.
- An available SMTP email server for sending alerts.

---

## Task 1: Accessing Alerts and Actions
- Navigate to Stack Management in Kibana.
- Under Alerts and Insights, click on Alerts and Actions.
- Verify that you can view existing alert rules and actions.

---

## Task 2: Setting Up an Email Connector
- Go to the Connectors tab and click Create connector.
- Select Email as the connector type.
- Provide SMTP server details:
  - Host, Port, Secure option, Username, Password
- Test the connector using the "Send test email" feature.

```json
{
  "host": "smtp.example.com",
  "port": 587,
  "secure": false,
  "username": "your-username",
  "password": "your-password"
}
Task 3: Configuring Alerts

Create a new alert rule under Alerts.

Define index, query, and trigger conditions (e.g., errors >= 10 in 5 minutes).

Assign an action using the created SMTP Email Connector.

Configure email content and recipients.

{
  "actionTypeId": ".email",
  "config": {
    "to": ["recipient@example.com"],
    "subject": "Kibana Alert Triggered",
    "message": "An alert has been triggered based on the defined conditions."
  }
}
Task 4: Verification

Simulate triggering the alert with test data.

Verify that the configured email is received.

Check the accuracy and content of the notification.

Conclusion

What I have learned: created alerts in Kibana, configured actions using an SMTP email connector, defined trigger conditions, and successfully verified notifications to monitor critical events.
