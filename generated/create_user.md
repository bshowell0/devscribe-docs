---
title: create_user
description: This API endpoint handles the creation of new users in our system. It
  listens for POST requests on the /api/users route, expecting user details like an
  email and password in the JSON body. The function first validates the email format
  before proceeding to create the new user record. Upon success, it returns a JSON
  object with the new user's information; otherwise, it returns an appropriate error
  response for invalid data or if the user already exists.
openapi: POST ['/api/users']
---
# create_user

{% callout type="tip" %}
**Source:** [View on GitHub](https://github.com/bshowell0/numbered-tabs/blob/main/temp_python/api_routes.py#L61-L84)
{% /callout %}

## Summary
This API endpoint handles the creation of new users in our system. It listens for POST requests on the /api/users route, expecting user details like an email and password in the JSON body. The function first validates the email format before proceeding to create the new user record. Upon success, it returns a JSON object with the new user's information; otherwise, it returns an appropriate error response for invalid data or if the user already exists.

## API Info
{% cardGroup cols=2 %}
{% card title="HTTP Methods" icon="server" %}
POST
{% /card %}
{% card title="Route Path" icon="route" %}
`/api/users`
{% /card %}
{% /cardGroup %}

## Usage Examples
{% tabGroup %}
{% tab title="Python" %}
```python
import requests

url = "https://api.example.com/api/users"
new_user_data = {
    "username": "jane_doe",
    "email": "jane.doe@example.com",
    "password": "securepassword123!"
}

response = requests.post(url, json=new_user_data)

print(response.status_code)
print(response.json())
```
{% /tab %}
{% tab title="JavaScript" %}
```javascript
fetch("https://api.example.com/api/users", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    username: "new_user_123",
    email: "new.user@example.com",
    password: "a-very-secure-password!",
  }),
})
  .then((response) => response.json())
  .then((data) => console.log(data));
```
{% /tab %}
{% tab title="Java" %}
```java
HttpClient client = HttpClient.newHttpClient();

String requestBody = "{\"username\": \"newuser\", \"email\": \"newuser@example.com\", \"password\": \"securePassword123\"}";

HttpRequest request = HttpRequest.newBuilder()
        .uri(URI.create("https://api.example.com/api/users"))
        .header("Content-Type", "application/json")
        .POST(HttpRequest.BodyPublishers.ofString(requestBody))
        .build();

HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());

System.out.println(response.statusCode());
System.out.println(response.body());
```
{% /tab %}
{% tab title="PHP" %}
```php
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "https://api.example.com/api/users",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => json_encode([
    "username" => "test_username",
    "email" => "test@example.com",
    "password" => "a_secure_password"
  ]),
  CURLOPT_HTTPHEADER => [
    "Content-Type: application/json"
  ],
]);

$response = curl_exec($curl);

curl_close($curl);

echo $response;
```
{% /tab %}
{% tab title="Go" %}
```go
package main

import (
	"bytes"
	"encoding/json"
	"fmt"
	"io"
	"net/http"
)

func main() {
	url := "https://api.example.com/api/users"
	
	userData := map[string]string{
		"username": "testuser",
		"email":    "testuser@example.com",
		"password": "securepassword123",
	}
	
	jsonValue, _ := json.Marshal(userData)
	
	resp, err := http.Post(url, "application/json", bytes.NewBuffer(jsonValue))
	if err != nil {
		panic(err)
	}
	defer resp.Body.Close()
	
	body, _ := io.ReadAll(resp.Body)
	
	fmt.Println("Response Status:", resp.Status)
	fmt.Println("Response Body:", string(body))
}
```
{% /tab %}
{% tab title="cURL" %}
```bash
curl -X POST "https://api.example.com/api/users" -H "Content-Type: application/json" -d '{"email": "testuser@example.com", "password": "a_secure_password"}'
```
{% /tab %}
{% /tabGroup %}

## Parameters
{% parameterField name="username" type="string" required=true %}
A string representing the unique identifier for the new user.
{% /parameterField %}

{% parameterField name="email" type="string" required=true %}
A string containing the user's email address, which will be validated.
{% /parameterField %}

{% parameterField name="password" type="string" required=true %}
A string for the user's password to create the new user account.
{% /parameterField %}

## Returns
`jsonify`: A Flask helper function that serializes a Python dictionary into a JSON `Response` object.