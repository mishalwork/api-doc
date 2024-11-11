## Create a step workflow session

**Curl**
```bash

curl --request POST \
  --url http://<baseUrl>/apis/request/workflow/step/create \
  --header 'Content-Type: application/json' \
  --header 'api-key: '<api-key>' \
  --data '{ "browserMode": "<mode>" }'

```
**Python**
```python
import requests

url = "http://<baseUrl>/apis/request/workflow/step/create"
headers = {
    "Content-Type": "application/json",
    "api-key": "<api-key>"
}
payload = {
    "browserMode": "<mode>"
}

response = requests.post(url, headers=headers, json=payload)
print(response.json())
```

**Javascript**
```javascript
const url = 'http://<baseUrl>/apis/request/workflow/step/create';
const headers = {
    'Content-Type': 'application/json',
    'api-key': '<api-key>'
};
const payload = {
    browserMode: '<mode>'
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
$url = "http://<baseUrl>/apis/request/workflow/step/create";
$headers = array(
    "Content-Type: application/json",
    "api-key: <api-key>"
);
$payload = array(
    "browserMode" => "<mode>"
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


**Go**
```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io"
)

func main() {

	url := "http://<baseUrl>/apis/request/workflow/step/create"

	payload := strings.NewReader("{ \"browserMode\": \"<mode>\" }")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("Content-Type", "application/json")
	req.Header.Add("api-key", "<api-key>")
	req.Header.Add("content-type", "application/json")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := io.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

**Java**
```java
import java.io.OutputStream;
import java.net.HttpURLConnection;
import java.net.URL;
import java.nio.charset.StandardCharsets;

public class WorkflowStepCreate {
    public static void main(String[] args) {
        try {
            URL url = new URL("http://<baseUrl>/apis/request/workflow/step/create");
            HttpURLConnection conn = (HttpURLConnection) url.openConnection();
            conn.setRequestMethod("POST");
            conn.setRequestProperty("Content-Type", "application/json");
            conn.setRequestProperty("api-key", "<api-key>");
            conn.setDoOutput(true);

            String jsonInput = "{\"browserMode\":\"<mode>\"}";

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

## Execute an individual step

```bash
curl --request POST \
  --url http://<baseUrl>/apis/request/workflow/step/run/<id> \
  --header 'Content-Type: application/json' \
  --header 'api-key: <api-key>' \
  --data '{
    "step": "<step>",
    "type": "<stepType>",
    "currentDom": "<optionalCurrentDom>",
    "currentPageURL": "<optionalCurrentPageURL>",
    "schema": {
	<openapi-schema>
    }
  }'
```

**Python**
```python
import requests

url = "http://<baseUrl>/apis/request/workflow/step/run/<id>"
headers = {
    "Content-Type": "application/json",
    "api-key": "<api-key>"
}
payload = {
    "step": "<step>",
    "type": "<stepType>",
    "currentDom": "<optionalCurrentDom>",
    "currentPageURL": "<optionalCurrentPageURL>",
    "schema": {
        # Add your OpenAPI schema here
        # "<openapi-schema>"
    }
}

response = requests.post(url, headers=headers, json=payload)
print(response.json())
```

**Javascript**

```Javascript
const url = 'http://<baseUrl>/apis/request/workflow/step/run/<id>';
const headers = {
    'Content-Type': 'application/json',
    'api-key': '<api-key>'
};
const payload = {
    step: '<step>',
    type: '<stepType>',
    currentDom: '<optionalCurrentDom>',
    currentPageURL: '<optionalCurrentPageURL>',
    schema: {
        // "<openapi-schema>"
    }
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
$url = "http://<baseUrl>/apis/request/workflow/step/run/<id>";
$headers = array(
    "Content-Type: application/json",
    "api-key: <api-key>"
);
$payload = array(
    "step" => "<step>",
    "type" => "<stepType>",
    "currentDom" => "<optionalCurrentDom>",
    "currentPageURL" => "<optionalCurrentPageURL>",
    "schema" => array(
        // Add your OpenAPI schema here
        // "<openapi-schema>"
    )
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
    url := "http://<baseUrl>/apis/request/workflow/step/run/<id>"
    
    payload := map[string]interface{}{
        "step": "<step>",
        "type": "<stepType>",
        "currentDom": "<optionalCurrentDom>",
        "currentPageURL": "<optionalCurrentPageURL>",
        "schema": map[string]interface{}{
            // Add your OpenAPI schema here
            // "<openapi-schema>"
        },
    }

    jsonPayload, _ := json.Marshal(payload)
    
    req, _ := http.NewRequest("POST", url, bytes.NewBuffer(jsonPayload))
    req.Header.Set("Content-Type", "application/json")
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
import java.io.OutputStream;
import java.net.HttpURLConnection;
import java.net.URL;
import java.nio.charset.StandardCharsets;

public class WorkflowStepRun {
    public static void main(String[] args) {
        try {
            URL url = new URL("http://<baseUrl>/apis/request/workflow/step/run/<id>");
            HttpURLConnection conn = (HttpURLConnection) url.openConnection();
            conn.setRequestMethod("POST");
            conn.setRequestProperty("Content-Type", "application/json");
            conn.setRequestProperty("api-key", "<api-key>");
            conn.setDoOutput(true);

            String jsonInput = String.format("""
                {
                    "step": "%s",
                    "type": "%s",
                    "currentDom": "%s",
                    "currentPageURL": "%s",
                    "schema": {
                        %s
                    }
                }
                """, 
                "<step>", 
                "<stepType>", 
                "<optionalCurrentDom>", 
                "<optionalCurrentPageURL>",
                "<openapi-schema>"
            );

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

## Get completion status of individual step

**Curl**
```bash
curl --request GET \
  --url http://<baseUrl>/apis/request/workflow/step/status/<stepId> \
  --header 'api-key: <api-key>'
```

**Python**
```python
import requests

url = "http://<baseUrl>/apis/request/workflow/step/status/<stepId>"
headers = {
    "api-key": "<api-key>"
}

response = requests.get(url, headers=headers)
print(response.json())
```

**JavaScript**
```javascript
const url = 'http://<baseUrl>/apis/request/workflow/step/status/<stepId>';
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
$url = "http://<baseUrl>/apis/request/workflow/step/status/<stepId>";
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
    url := "http://<baseUrl>/apis/request/workflow/step/status/<stepId>"
    
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

public class WorkflowStepStatus {
    public static void main(String[] args) {
        try {
            URL url = new URL("http://<baseUrl>/apis/request/workflow/step/status/<stepId>");
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
