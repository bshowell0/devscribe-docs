---
title: borrow
description: This POST API endpoint at `/api/borrow` handles requests for users to
  borrow products. It requires a `user_id` and `product_id` in the request payload,
  validates that both the user and product exist, and then creates a new order record
  to track the transaction. The endpoint returns a JSON response confirming the successful
  creation of the borrow order.
openapi: POST ['/api/borrow']
---
# borrow

{% callout type="tip" %}
**Source:** [View on GitHub](https://github.com/bshowell0/numbered-tabs/blob/main/temp_python/api_routes.py#L54-L58)
{% /callout %}

## Summary
This POST API endpoint at `/api/borrow` handles requests for users to borrow products. It requires a `user_id` and `product_id` in the request payload, validates that both the user and product exist, and then creates a new order record to track the transaction. The endpoint returns a JSON response confirming the successful creation of the borrow order.

## API Info
{% cardGroup cols=2 %}
{% card title="HTTP Methods" icon="server" %}
POST
{% /card %}
{% card title="Route Path" icon="route" %}
`/api/borrow`
{% /card %}
{% /cardGroup %}

## Usage Examples
{% codeGroup %}
```python {% title="Python" %}
import requests
import json

url = "https://api.example.com/api/borrow"
payload = {
    "user_id": "user_12345",
    "book_id": "book_67890",
    "borrow_date": "2024-07-29"
}
headers = {
    "Content-Type": "application/json"
}

response = requests.post(url, data=json.dumps(payload), headers=headers)

print(f"Status Code: {response.status_code}")
print(f"Response: {response.json()}")
```

```javascript {% title="JavaScript" %}
fetch("https://api.example.com/api/borrow", {
  method: "POST",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify({
    userId: "user-789",
    bookId: "book-123",
    dueDate: "2024-08-15"
  })
})
.then(response => response.json())
.then(data => console.log("Success:", data))
.catch(error => console.error("Error:", error));
```

```java {% title="Java" %}
import java.io.IOException;
import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;

public class Example {
    public static void main(String[] args) throws IOException, InterruptedException {
        HttpClient client = HttpClient.newHttpClient();
        String requestBody = "{\"userId\": \"user_a5b1c2\", \"bookId\": \"book_x4y5z6\"}";

        HttpRequest request = HttpRequest.newBuilder()
                .uri(URI.create("https://api.example.com/api/borrow"))
                .header("Content-Type", "application/json")
                .POST(HttpRequest.BodyPublishers.ofString(requestBody))
                .build();

        HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());

        System.out.println("Status Code: " + response.statusCode());
        System.out.println("Response Body: " + response.body());
    }
}
```

```php {% title="PHP" %}
<?php

$url = "https://api.example.com/api/borrow";
$data = [
    "user_id" => "user_a7b1c9d8",
    "item_id" => "item_f3e2d1c0"
];

$options = [
    "http" => [
        "header"  => "Content-type: application/json\r\n",
        "method"  => "POST",
        "content" => json_encode($data),
    ],
];

$context  = stream_context_create($options);
$result = file_get_contents($url, false, $context);

if ($result === FALSE) {
    /* Handle error */
}

var_dump($result);

?>
```

```go {% title="GO" %}
package main

import (
	"bytes"
	"encoding/json"
	"fmt"
	"io"
	"net/http"
)

func main() {
	url := "https://api.example.com/api/borrow"
	requestBody, _ := json.Marshal(map[string]string{
		"user_id": "user_789",
		"book_id": "book_123",
	})

	response, err := http.Post(url, "application/json", bytes.NewBuffer(requestBody))
	if err != nil {
		fmt.Printf("Request failed with error %s\n", err)
		return
	}
	defer response.Body.Close()
	body, _ := io.ReadAll(response.Body)
	fmt.Println("Response Status:", response.Status)
	fmt.Println("Response Body:", string(body))
}
```

```bash {% title="cURL" %}
curl -X POST "https://api.example.com/api/borrow" -H "Content-Type: application/json" -d '{"user_id": "user_123", "book_id": "book_456"}'
```
{% /codeGroup %}

## Parameters
- `parameters` <span style="color: #8B5CF6; background-color: #F5F3FF; padding: 2px 6px; border-radius: 4px; font-size: 0.9em; font-weight: 500;">required</span>
  A required list of parameter lists, where each inner list contains strings with details about a single function parameter.

## Returns
`jsonify`: Creates a Flask `Response` object with the JSON representation of the given arguments.