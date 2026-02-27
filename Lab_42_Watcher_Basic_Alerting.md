# Lab — Using Watcher for Basic Alerting (OSS Basic)

## Objectives
- Learn how to set up a Watch using Kibana's Dev Tools.
- Understand how to configure conditions and actions for alerting.
- Test the Watch by injecting data that meets specific conditions.

## Prerequisites
- Basic understanding of Elasticsearch and Kibana.
- Access to a running instance of Elasticsearch and Kibana.
- Familiarity with JSON and Kibana Dev Tools.

---

## Task 1: Create a Watch in Kibana Dev Tools

### Step 1.1: Access Kibana Dev Tools
- Open Kibana in your web browser.
- Navigate to **Dev Tools** in the sidebar.

### Step 1.2: Define a Search Query for the Watch
In the Console tab, create a sample watch:

```json
PUT _watcher/watch/log_error_watch
{
  "trigger": {
    "schedule": {
      "interval": "10s"
    }
  },
  "input": {
    "search": {
      "request": {
        "indices": ["logs-*"],
        "body": {
          "query": {
            "match": {
              "error": "critical"
            }
          }
        }
      }
    }
  },
  "condition": {
    "compare": {
      "ctx.payload.hits.total": {
        "gt": 0
      }
    }
  }
}

Explanation:

trigger: The schedule for the watch to run (every 10 seconds).

input: The search query for indices starting with logs-*.

condition: Checks if at least one matching document is found.

Task 2: Add an Action (Email or Webhook)
Email Action (if email is configured):
PUT _watcher/watch/log_error_watch
{
  "actions": {
    "email_admin": {
      "email": {
        "to": "admin@example.com",
        "subject": "Critical Error Detected",
        "body": "A critical error has been detected in the logs."
      }
    }
  }
}
Webhook Action (example):
PUT _watcher/watch/log_error_watch
{
  "actions": {
    "notify_webhook": {
      "webhook": {
        "method": "POST",
        "url": "http://example.com/alerts",
        "body": "{{ctx.payload}}"
      }
    }
  }
}

Explanation:

actions: Defines what happens when the watch condition is met.

email: Sends an alert to a specified email.

webhook: Sends a POST request with the payload to a URL.

Task 3: Test by Injecting Data That Meets the Condition
Step 3.1: Inject Sample Data

Use Dev Tools to index a document that triggers the alert:

POST logs/_doc/
{
  "timestamp": "2023-10-15T11:02:00",
  "error": "critical",
  "message": "A critical error occurred at the main server."
}

Explanation:

This simulates a critical error. Once indexed, the watch should trigger the alert.

Conclusion

You have successfully:

Created a basic watch in Kibana for alerting.

Defined conditions and actions for email or webhook notifications.

Tested the watch using sample log data.

This fundamental alerting mechanism provides a foundation for building advanced monitoring and automated responses in Elasticsearch using Watcher.
