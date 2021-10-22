# Amazon-SNS-to-Microsoft-Teams-Slack


## Code snippet for Microsoft Teams

```python
#!/usr/bin/python3.6
import urllib3 
import json
http = urllib3.PoolManager() 
def lambda_handler(event, context): 
    url = "https://outlook.office.com/webhook/xxxxxxx"    
    msg = {
        "text": event['Records'][0]['Sns']['Message']
    }
    encoded_msg = json.dumps(msg).encode('utf-8')
    resp = http.request('POST',url, body=encoded_msg)
    print({
        "message": event['Records'][0]['Sns']['Message'], 
        "status_code": resp.status, 
        "response": resp.data
    })
    
 ```

## Code snippet for Slack
```python
#!/usr/bin/python3.6
import urllib3
import json
http = urllib3.PoolManager()
def lambda_handler(event, context):
    url = "https://hooks.slack.com/services/xxxxxxx"
    msg = {
        "channel": "#YOUR_CHANNEL_NAME",
        "username": "WEBHOOK_USERNAME",
        "text": event['Records'][0]['Sns']['Message'],
        "icon_emoji": ""
    }
    
    encoded_msg = json.dumps(msg).encode('utf-8')
    resp = http.request('POST',url, body=encoded_msg)
    print({
        "message": event['Records'][0]['Sns']['Message'], 
        "status_code": resp.status, 
        "response": resp.data
    })
```
