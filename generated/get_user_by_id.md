---
title: get_user_by_id
description: This API endpoint handles GET requests to retrieve a specific user by
  their unique integer ID, which is provided in the URL path. Upon a successful lookup,
  the function returns the user's complete details serialized as a JSON object. If
  a user with the specified ID cannot be found, the endpoint correctly responds with
  a 404 Not Found error.
openapi: GET ['/api/users/<int:user_id>']
---
# get_user_by_id

{% callout type="tip" %}
**Source:** [View on GitHub](https://github.com/bshowell0/numbered-tabs/blob/main/temp_python/api_routes.py#L87-L102)
{% /callout %}

## Summary
This API endpoint handles GET requests to retrieve a specific user by their unique integer ID, which is provided in the URL path. Upon a successful lookup, the function returns the user's complete details serialized as a JSON object. If a user with the specified ID cannot be found, the endpoint correctly responds with a 404 Not Found error.

## API Info
{% cardGroup cols=2 %}
{% card title="HTTP Methods" icon="server" %}
GET
{% /card %}
{% card title="Route Path" icon="route" %}
`/api/users/<int:user_id>`
{% /card %}
{% /cardGroup %}

## Usage Examples
{% codeGroup %}
```python {% title="Python" %}
import requests

user_id = 123
response = requests.get(f"https://api.example.com/api/users/{user_id}")

print(response.json())
```

```javascript {% title="JavaScript" %}
fetch("https://api.example.com/api/users/123")
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error("Error:", error));
```

```java {% title="Java" %}
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.net.HttpURLConnection;
import java.net.URL;

public class GetUserExample {
    public static void main(String[] args) {
        try {
            URL url = new URL("https://api.example.com/api/users/123");
            HttpURLConnection con = (HttpURLConnection) url.openConnection();
            con.setRequestMethod("GET");

            BufferedReader in = new BufferedReader(new InputStreamReader(con.getInputStream()));
            String inputLine;
            StringBuilder content = new StringBuilder();
            while ((inputLine = in.readLine()) != null) {
                content.append(inputLine);
            }
            in.close();
            con.disconnect();

            System.out.println(content.toString());
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

```php {% title="PHP" %}
<?php
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, "https://api.example.com/api/users/123");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
$response = curl_exec($ch);
curl_close($ch);
$user = json_decode($response);
var_dump($user);
?>
```

```go {% title="Go" %}
package main

import (
	"fmt"
	"io/ioutil"
	"net/http"
)

func main() {
	client := &http.Client{}
	req, err := http.NewRequest("GET", "https://api.example.com/api/users/123", nil)
	if err != nil {
		fmt.Println(err)
		return
	}

	resp, err := client.Do(req)
	if err != nil {
		fmt.Println(err)
		return
	}
	defer resp.Body.Close()

	body, err := ioutil.ReadAll(resp.Body)
	if err != nil {
		fmt.Println(err)
		return
	}

	fmt.Println(string(body))
}
```

```bash {% title="cURL" %}
curl -X GET "https://api.example.com/api/users/123"
```
{% /codeGroup %}

## Parameters
{% parameterField name="user_id" type="integer" required=true %}
The unique identifier for the user to be retrieved.
{% /parameterField %}

## Returns
`jsonify`: A Flask function that serializes a Python dictionary into a JSON-formatted Response object.