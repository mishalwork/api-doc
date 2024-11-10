## Workflow API's

### Run a workflow using workflow id

**curl**

```bash
curl --request POST \
  --url http://<baseUrl>/apis/request/run/workflows \
  --header 'api-key: <api-key>' \
  --header 'content-type: application/json' \
  --data '{
       "workflowId": "<workflowId>"
}'
```

**Python**
```python
import requests

url = "http://<baseUrl>/apis/request/run/workflows"
headers = {
    "api-key": "<api-key>",
    "content-type": "application/json"
}
payload = {
    "workflowId": "<workflowId>"
}

response = requests.post(url, headers=headers, json=payload)
print(response.json())
```

**Javascript**
```javascript
const url = 'http://<baseUrl>/apis/request/run/workflows';
const headers = {
    'api-key': '<api-key>',
    'content-type': 'application/json'
};
const payload = {
    workflowId: '<workflowId>'
};

fetch(url, {
    method: 'POST',
    headers: headers,
    body: JSON.stringify(payload)
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
```
**PHP**
```php
<?php
// PHP (using cURL)
$url = "http://<baseUrl>/apis/request/run/workflows";
$headers = array(
    "api-key: <api-key>",
    "content-type: application/json"
);
$payload = array(
    "workflowId" => "<workflowId>"
);

$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);
curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($payload));
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

$response = curl_exec($ch);
curl_close($ch);

echo $response;
?>
```
**GO**
```go
package main

import (
    "bytes"
    "encoding/json"
    "fmt"
    "net/http"
)

func main() {
    url := "http://<baseUrl>/apis/request/run/workflows"
    payload := map[string]string{
        "workflowId": "<workflowId>",
    }

    jsonPayload, _ := json.Marshal(payload)
    
    req, _ := http.NewRequest("POST", url, bytes.NewBuffer(jsonPayload))
    req.Header.Set("api-key", "<api-key>")
    req.Header.Set("content-type", "application/json")

    client := &http.Client{}
    resp, err := client.Do(req)
    if err != nil {
        panic(err)
    }
    defer resp.Body.Close()

    var result map[string]interface{}
    json.NewDecoder(resp.Body).Decode(&result)
    fmt.Println(result)
}
```
**Java**
```java
import java.io.OutputStream;
import java.net.HttpURLConnection;
import java.net.URL;
import java.nio.charset.StandardCharsets;

public class WorkflowRequest {
    public static void main(String[] args) {
        try {
            URL url = new URL("http://<baseUrl>/apis/request/run/workflows");
            HttpURLConnection conn = (HttpURLConnection) url.openConnection();
            conn.setRequestMethod("POST");
            conn.setRequestProperty("api-key", "<api-key>");
            conn.setRequestProperty("content-type", "application/json");
            conn.setDoOutput(true);

            String jsonInput = "{\"workflowId\":\"<workflowId>\"}";

            try(OutputStream os = conn.getOutputStream()) {
                byte[] input = jsonInput.getBytes(StandardCharsets.UTF_8);
                os.write(input, 0, input.length);
            }

            int responseCode = conn.getResponseCode();
            System.out.println("Response Code: " + responseCode);

            conn.disconnect();
        } catch(Exception e) {
            e.printStackTrace();
        }
    }
}
```

### Get Workflow Session Status

**curl**
```bash
curl --request GET \
  --url http://<baseUrl>/apis/request/workflow/status/<id> \
  --header 'api-key: <api-key>' 
```
**Python**
```python
import requests

url = "http://<baseUrl>/apis/request/workflow/status/<id>"
headers = {
    "api-key": "<api-key>"
}

response = requests.get(url, headers=headers)
print(response.json())
```

**Javascript**
```javascript
const url = 'http://<baseUrl>/apis/request/workflow/status/<id>';
const headers = {
    'api-key': '<api-key>'
};

fetch(url, {
    method: 'GET',
    headers: headers
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
```

**PHP**
```php
<?php
$url = "http://<baseUrl>/apis/request/workflow/status/<id>";
$headers = array(
    "api-key: <api-key>"
);

$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_HTTPGET, true);
curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

$response = curl_exec($ch);
curl_close($ch);

echo $response;
?>
```
**GO**
```go
package main

import (
    "encoding/json"
    "fmt"
    "net/http"
)

func main() {
    url := "http://<baseUrl>/apis/request/workflow/status/<id>"
    
    req, _ := http.NewRequest("GET", url, nil)
    req.Header.Set("api-key", "<api-key>")

    client := &http.Client{}
    resp, err := client.Do(req)
    if err != nil {
        panic(err)
    }
    defer resp.Body.Close()

    var result map[string]interface{}
    json.NewDecoder(resp.Body).Decode(&result)
    fmt.Println(result)
}
```
**Java**
```java
import java.net.HttpURLConnection;
import java.net.URL;
import java.io.BufferedReader;
import java.io.InputStreamReader;

public class WorkflowStatus {
    public static void main(String[] args) {
        try {
            URL url = new URL("http://<baseUrl>/apis/request/workflow/status/<id>");
            HttpURLConnection conn = (HttpURLConnection) url.openConnection();
            conn.setRequestMethod("GET");
            conn.setRequestProperty("api-key", "<api-key>");

            BufferedReader in = new BufferedReader(
                new InputStreamReader(conn.getInputStream()));
            String inputLine;
            StringBuffer response = new StringBuffer();

            while ((inputLine = in.readLine()) != null) {
                response.append(inputLine);
            }
            in.close();

            System.out.println(response.toString());
            conn.disconnect();
        } catch(Exception e) {
            e.printStackTrace();
        }
    }
}
```
