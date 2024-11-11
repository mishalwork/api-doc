## Create a step workflow session

**Curl**
```bash

curl --request POST \
  --url http://<baseUrl>/request/workflow/step/create \
  --header 'Content-Type: application/json' \
  --header 'api-key: '<api-key>' \
  --data '{ "browserMode": "<mode>" }'

```
**Python**
```python
import requests

url = "http://<baseUrl>/request/workflow/step/create"
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
const url = 'http://<baseUrl>/request/workflow/step/create';
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
$url = "http://<baseUrl>/request/workflow/step/create";
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

	url := "http://<baseUrl>/request/workflow/step/create"

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
            URL url = new URL("http://<baseUrl>/request/workflow/step/create");
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
