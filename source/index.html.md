---
title: Swagger Smart Elections v0.1.2
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - ruby: Ruby
  - python: Python
  - php: PHP
  - java: Java
  - go: Go
toc_footers:
  - <a href="http://swagger.io">Find out more about Swagger</a>
includes: []
search: true
highlight_theme: darkula
headingLevel: 2

---

<!-- Generator: Widdershins v4.0.1 -->

<h1 id="swagger-smart-elections">Swagger Smart Elections v0.1.2</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Base URLs:

* <a href="https://elections.hse.ru">https://elections.hse.ru</a>

# Authentication

- HTTP Authentication, scheme: bearer 

<h1 id="swagger-smart-elections-auth">auth</h1>

Инструментарий для авторизации

## get__auth_elk

> Code samples

```shell
# You can also use wget
curl -X GET https://elections.hse.ru/auth/elk

```

```http
GET https://elections.hse.ru/auth/elk HTTP/1.1
Host: elections.hse.ru

```

```javascript

fetch('https://elections.hse.ru/auth/elk',
{
  method: 'GET'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

result = RestClient.get 'https://elections.hse.ru/auth/elk',
  params: {
  }

p JSON.parse(result)

```

```python
import requests

r = requests.get('https://elections.hse.ru/auth/elk')

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://elections.hse.ru/auth/elk', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://elections.hse.ru/auth/elk");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://elections.hse.ru/auth/elk", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /auth/elk`

*Авторизация*

Редирект на авторизацию

<h3 id="get__auth_elk-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|303|[See Other](https://tools.ietf.org/html/rfc7231#section-6.4.4)|Редирект на ЕЛК|None|

<aside class="success">
This operation does not require authentication
</aside>

## post__auth_redirect

> Code samples

```shell
# You can also use wget
curl -X POST https://elections.hse.ru/auth/redirect?access_token=string

```

```http
POST https://elections.hse.ru/auth/redirect?access_token=string HTTP/1.1
Host: elections.hse.ru

```

```javascript

fetch('https://elections.hse.ru/auth/redirect?access_token=string',
{
  method: 'POST'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

result = RestClient.post 'https://elections.hse.ru/auth/redirect',
  params: {
  'access_token' => 'string'
}

p JSON.parse(result)

```

```python
import requests

r = requests.post('https://elections.hse.ru/auth/redirect', params={
  'access_token': 'string'
})

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://elections.hse.ru/auth/redirect', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://elections.hse.ru/auth/redirect?access_token=string");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://elections.hse.ru/auth/redirect", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /auth/redirect`

*Возврат из ЕЛК*

Возврат из ЕЛК

<h3 id="post__auth_redirect-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|access_token|query|string|true|JWT-токен|

<h3 id="post__auth_redirect-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Токен принят и сохранён|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Ошибка|None|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="swagger-smart-elections-elector">elector</h1>

Инструментарий для пользователя

## post__elections_becomeCandidate_{electionId}

> Code samples

```shell
# You can also use wget
curl -X POST https://elections.hse.ru/elections/becomeCandidate/{electionId}?candidate=name,%D0%98%D0%BC%D1%8F,photoUrl,https%3A%2F%2Fimg.com%2Fimg.png,description,%D0%9F%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B0 \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://elections.hse.ru/elections/becomeCandidate/{electionId}?candidate=name,%D0%98%D0%BC%D1%8F,photoUrl,https%3A%2F%2Fimg.com%2Fimg.png,description,%D0%9F%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B0 HTTP/1.1
Host: elections.hse.ru

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://elections.hse.ru/elections/becomeCandidate/{electionId}?candidate=name,%D0%98%D0%BC%D1%8F,photoUrl,https%3A%2F%2Fimg.com%2Fimg.png,description,%D0%9F%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B0',
{
  method: 'POST',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://elections.hse.ru/elections/becomeCandidate/{electionId}',
  params: {
  'candidate' => '[CandidateRequest](#schemacandidaterequest)'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://elections.hse.ru/elections/becomeCandidate/{electionId}', params={
  'candidate': {
  "name": "Имя",
  "photoUrl": "https://img.com/img.png",
  "description": "Программа"
}
}, headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://elections.hse.ru/elections/becomeCandidate/{electionId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://elections.hse.ru/elections/becomeCandidate/{electionId}?candidate=name,%D0%98%D0%BC%D1%8F,photoUrl,https%3A%2F%2Fimg.com%2Fimg.png,description,%D0%9F%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B0");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://elections.hse.ru/elections/becomeCandidate/{electionId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /elections/becomeCandidate/{electionId}`

*Стать кандидатом/редактировать профиль*

Стать кандидатом в выборах/редактировать профиль

<h3 id="post__elections_becomecandidate_{electionid}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|electionId|path|string|true|Выборы|
|candidate|query|[CandidateRequest](#schemacandidaterequest)|true|Кандидат|

<h3 id="post__elections_becomecandidate_{electionid}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Успешно|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Невалидно|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
elk_auth ( Scopes: elector )
</aside>

## get__elections_myCandidateStatus_{electionId}

> Code samples

```shell
# You can also use wget
curl -X GET https://elections.hse.ru/elections/myCandidateStatus/{electionId} \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://elections.hse.ru/elections/myCandidateStatus/{electionId} HTTP/1.1
Host: elections.hse.ru
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://elections.hse.ru/elections/myCandidateStatus/{electionId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://elections.hse.ru/elections/myCandidateStatus/{electionId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://elections.hse.ru/elections/myCandidateStatus/{electionId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://elections.hse.ru/elections/myCandidateStatus/{electionId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://elections.hse.ru/elections/myCandidateStatus/{electionId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://elections.hse.ru/elections/myCandidateStatus/{electionId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /elections/myCandidateStatus/{electionId}`

*Статус по заявке в кандидаты*

Статус по заявке в кандидаты

<h3 id="get__elections_mycandidatestatus_{electionid}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|electionId|path|string|true|Выборы|

> Example responses

> 200 Response

```json
"approved"
```

<h3 id="get__elections_mycandidatestatus_{electionid}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Успешно|string|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Невалидно|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
elk_auth ( Scopes: elector )
</aside>

## get__elections_all

> Code samples

```shell
# You can also use wget
curl -X GET https://elections.hse.ru/elections/all \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://elections.hse.ru/elections/all HTTP/1.1
Host: elections.hse.ru
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://elections.hse.ru/elections/all',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://elections.hse.ru/elections/all',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://elections.hse.ru/elections/all', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://elections.hse.ru/elections/all', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://elections.hse.ru/elections/all");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://elections.hse.ru/elections/all", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /elections/all`

*Получить выборы*

Получить выборы, доступные для текущего пользователя

<h3 id="get__elections_all-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|status|query|string|false|Cтатус выборов|

#### Enumerated Values

|Parameter|Value|
|---|---|
|status|all|
|status|started|
|status|results|

> Example responses

> 200 Response

```json
[
  "string"
]
```

<h3 id="get__elections_all-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Возвращает ID выборов|Inline|

<h3 id="get__elections_all-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
elk_auth ( Scopes: elect )
</aside>

## get__elections_get_{electionId}

> Code samples

```shell
# You can also use wget
curl -X GET https://elections.hse.ru/elections/get/{electionId} \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://elections.hse.ru/elections/get/{electionId} HTTP/1.1
Host: elections.hse.ru
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://elections.hse.ru/elections/get/{electionId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://elections.hse.ru/elections/get/{electionId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://elections.hse.ru/elections/get/{electionId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://elections.hse.ru/elections/get/{electionId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://elections.hse.ru/elections/get/{electionId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://elections.hse.ru/elections/get/{electionId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /elections/get/{electionId}`

*Получить выборы по ID*

Получить выбор по ID, доступный для текущего пользователя

<h3 id="get__elections_get_{electionid}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|electionId|path|string|true|ID|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "name": "Выборы в КпЦ",
  "priority": 0,
  "isRunoff": true,
  "mandates": 0,
  "isForNearForeign": true,
  "isForFarForeign": true,
  "acceptedCouncilOrganizationsIds": [
    1,
    2
  ],
  "acceptedFacultiesIds": [
    1,
    2
  ],
  "acceptedDormitoriesIds": [
    1,
    2
  ],
  "startTime": "2019-08-24T14:15:22Z",
  "finishTime": "2019-08-24T14:15:22Z",
  "status": "draft"
}
```

<h3 id="get__elections_get_{electionid}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Возвращает выборы|[Election](#schemaelection)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Невалидный ID|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
elk_auth ( Scopes: elect )
</aside>

## get__elections_getCandidates_{electionId}

> Code samples

```shell
# You can also use wget
curl -X GET https://elections.hse.ru/elections/getCandidates/{electionId} \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://elections.hse.ru/elections/getCandidates/{electionId} HTTP/1.1
Host: elections.hse.ru
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://elections.hse.ru/elections/getCandidates/{electionId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://elections.hse.ru/elections/getCandidates/{electionId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://elections.hse.ru/elections/getCandidates/{electionId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://elections.hse.ru/elections/getCandidates/{electionId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://elections.hse.ru/elections/getCandidates/{electionId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://elections.hse.ru/elections/getCandidates/{electionId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /elections/getCandidates/{electionId}`

*Получить кандидатов по выборам*

Получить кандидатов по выборам, доступным для текущего пользователя

<h3 id="get__elections_getcandidates_{electionid}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|electionId|path|string|true|ID|

> Example responses

> 200 Response

```json
[
  {
    "id": 1,
    "electionId": 1,
    "name": "Имя",
    "photoUrl": "https://img.com/img.png",
    "description": "Программа",
    "approved": true,
    "waitingForApprove": true
  }
]
```

<h3 id="get__elections_getcandidates_{electionid}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Возвращает кандидатов|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Невалидный ID|None|

<h3 id="get__elections_getcandidates_{electionid}-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Candidate](#schemacandidate)]|false|none|none|
|» id|string|true|none|none|
|» electionId|integer(int64)|true|none|none|
|» name|string|true|none|none|
|» photoUrl|string(url)|true|none|none|
|» description|string|true|none|none|
|» approved|boolean|true|none|none|
|» waitingForApprove|boolean|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
elk_auth ( Scopes: elect )
</aside>

## get__elections_getVoices_{electionId}

> Code samples

```shell
# You can also use wget
curl -X GET https://elections.hse.ru/elections/getVoices/{electionId} \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://elections.hse.ru/elections/getVoices/{electionId} HTTP/1.1
Host: elections.hse.ru
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://elections.hse.ru/elections/getVoices/{electionId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://elections.hse.ru/elections/getVoices/{electionId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://elections.hse.ru/elections/getVoices/{electionId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://elections.hse.ru/elections/getVoices/{electionId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://elections.hse.ru/elections/getVoices/{electionId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://elections.hse.ru/elections/getVoices/{electionId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /elections/getVoices/{electionId}`

*Получить зашифрованные голоса*

Получить зашифрованные по выборам, доступным для текущего пользователя

<h3 id="get__elections_getvoices_{electionid}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|electionId|path|string|true|ID|

> Example responses

> 200 Response

```json
[
  "string"
]
```

<h3 id="get__elections_getvoices_{electionid}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Возвращает голоса|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Невалидный ID|None|

<h3 id="get__elections_getvoices_{electionid}-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
elk_auth ( Scopes: elect )
</aside>

## get__elections_getResults_{electionId}

> Code samples

```shell
# You can also use wget
curl -X GET https://elections.hse.ru/elections/getResults/{electionId} \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://elections.hse.ru/elections/getResults/{electionId} HTTP/1.1
Host: elections.hse.ru
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://elections.hse.ru/elections/getResults/{electionId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://elections.hse.ru/elections/getResults/{electionId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://elections.hse.ru/elections/getResults/{electionId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://elections.hse.ru/elections/getResults/{electionId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://elections.hse.ru/elections/getResults/{electionId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://elections.hse.ru/elections/getResults/{electionId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /elections/getResults/{electionId}`

*Получить результаты выборов по ID*

Получить результаты выборов по ID, доступный для текущего пользователя

<h3 id="get__elections_getresults_{electionid}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|electionId|path|string|true|ID|

> Example responses

> 200 Response

```json
{
  "candidates": {
    "candidateId": 1,
    "voices": 1
  }
}
```

<h3 id="get__elections_getresults_{electionid}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Возвращает выборы|[ElectionResults](#schemaelectionresults)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Невалидный ID|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
elk_auth ( Scopes: elect )
</aside>

## post__elections_vote_{electionId}

> Code samples

```shell
# You can also use wget
curl -X POST https://elections.hse.ru/elections/vote/{electionId} \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://elections.hse.ru/elections/vote/{electionId} HTTP/1.1
Host: elections.hse.ru

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://elections.hse.ru/elections/vote/{electionId}',
{
  method: 'POST',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://elections.hse.ru/elections/vote/{electionId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://elections.hse.ru/elections/vote/{electionId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://elections.hse.ru/elections/vote/{electionId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://elections.hse.ru/elections/vote/{electionId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://elections.hse.ru/elections/vote/{electionId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /elections/vote/{electionId}`

*Проголосовать в выборах*

<h3 id="post__elections_vote_{electionid}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|electionId|path|string|true|ID|
|voice|query|string|false|Зашифрованная публичным ключом строка JSON: в случае runoff {random: '293029302', voice: [candidateId, candidateId]} в порядке предпочтения, иначе - {random: '293029302', voice: [[candidateId, voicesCount], [candidateId, voicesCount]]}|

<h3 id="post__elections_vote_{electionid}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Голос принят|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Голосование не началось/уже закончилось|None|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Голос уже был принят|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
elk_auth ( Scopes: elect )
</aside>

## get__elections_publicKey_{electionId}

> Code samples

```shell
# You can also use wget
curl -X GET https://elections.hse.ru/elections/publicKey/{electionId} \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://elections.hse.ru/elections/publicKey/{electionId} HTTP/1.1
Host: elections.hse.ru
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://elections.hse.ru/elections/publicKey/{electionId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://elections.hse.ru/elections/publicKey/{electionId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://elections.hse.ru/elections/publicKey/{electionId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://elections.hse.ru/elections/publicKey/{electionId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://elections.hse.ru/elections/publicKey/{electionId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://elections.hse.ru/elections/publicKey/{electionId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /elections/publicKey/{electionId}`

*Получить публичный ключ*

<h3 id="get__elections_publickey_{electionid}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|electionId|path|string|true|ID|

> Example responses

> 200 Response

```json
"string"
```

<h3 id="get__elections_publickey_{electionid}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Возвращает публичный ключ|string|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Ключ ещё не загружен|string|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
elk_auth ( Scopes: elect )
</aside>

<h1 id="swagger-smart-elections-observer">observer</h1>

Инструментарий для наблюдателя

## post__elections_setPrivateKey_{electionId}

> Code samples

```shell
# You can also use wget
curl -X POST https://elections.hse.ru/elections/setPrivateKey/{electionId}?key=string \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://elections.hse.ru/elections/setPrivateKey/{electionId}?key=string HTTP/1.1
Host: elections.hse.ru

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://elections.hse.ru/elections/setPrivateKey/{electionId}?key=string',
{
  method: 'POST',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://elections.hse.ru/elections/setPrivateKey/{electionId}',
  params: {
  'key' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://elections.hse.ru/elections/setPrivateKey/{electionId}', params={
  'key': 'string'
}, headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://elections.hse.ru/elections/setPrivateKey/{electionId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://elections.hse.ru/elections/setPrivateKey/{electionId}?key=string");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://elections.hse.ru/elections/setPrivateKey/{electionId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /elections/setPrivateKey/{electionId}`

*Установить часть приватного ключа для выборов*

Создает выборы, для администратора

<h3 id="post__elections_setprivatekey_{electionid}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|electionId|path|string|true|none|
|key|query|string|true|none|

<h3 id="post__elections_setprivatekey_{electionid}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Успешно|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
elk_auth ( Scopes: observer )
</aside>

<h1 id="swagger-smart-elections-admin">admin</h1>

Инструментарий для администратора

## post__elections_setPublicKey_{electionId}

> Code samples

```shell
# You can also use wget
curl -X POST https://elections.hse.ru/elections/setPublicKey/{electionId}?key=string \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://elections.hse.ru/elections/setPublicKey/{electionId}?key=string HTTP/1.1
Host: elections.hse.ru

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://elections.hse.ru/elections/setPublicKey/{electionId}?key=string',
{
  method: 'POST',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://elections.hse.ru/elections/setPublicKey/{electionId}',
  params: {
  'key' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://elections.hse.ru/elections/setPublicKey/{electionId}', params={
  'key': 'string'
}, headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://elections.hse.ru/elections/setPublicKey/{electionId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://elections.hse.ru/elections/setPublicKey/{electionId}?key=string");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://elections.hse.ru/elections/setPublicKey/{electionId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /elections/setPublicKey/{electionId}`

*Установить публичный ключ для выборов*

<h3 id="post__elections_setpublickey_{electionid}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|electionId|path|string|true|none|
|key|query|string|true|none|

<h3 id="post__elections_setpublickey_{electionid}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Успешно|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Невалидно|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
elk_auth ( Scopes: admin )
</aside>

## post__elections_create

> Code samples

```shell
# You can also use wget
curl -X POST https://elections.hse.ru/elections/create?election=id,string,name,%D0%92%D1%8B%D0%B1%D0%BE%D1%80%D1%8B%20%D0%B2%20%D0%9A%D0%BF%D0%A6,priority,0,isRunoff,true,mandates,0,isForNearForeign,true,isForFarForeign,true,acceptedCouncilOrganizationsIds,1%2C2,acceptedFacultiesIds,1%2C2,acceptedDormitoriesIds,1%2C2,startTime,2019-08-24T14%3A15%3A22Z,finishTime,2019-08-24T14%3A15%3A22Z,status,draft \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://elections.hse.ru/elections/create?election=id,string,name,%D0%92%D1%8B%D0%B1%D0%BE%D1%80%D1%8B%20%D0%B2%20%D0%9A%D0%BF%D0%A6,priority,0,isRunoff,true,mandates,0,isForNearForeign,true,isForFarForeign,true,acceptedCouncilOrganizationsIds,1%2C2,acceptedFacultiesIds,1%2C2,acceptedDormitoriesIds,1%2C2,startTime,2019-08-24T14%3A15%3A22Z,finishTime,2019-08-24T14%3A15%3A22Z,status,draft HTTP/1.1
Host: elections.hse.ru
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://elections.hse.ru/elections/create?election=id,string,name,%D0%92%D1%8B%D0%B1%D0%BE%D1%80%D1%8B%20%D0%B2%20%D0%9A%D0%BF%D0%A6,priority,0,isRunoff,true,mandates,0,isForNearForeign,true,isForFarForeign,true,acceptedCouncilOrganizationsIds,1%2C2,acceptedFacultiesIds,1%2C2,acceptedDormitoriesIds,1%2C2,startTime,2019-08-24T14%3A15%3A22Z,finishTime,2019-08-24T14%3A15%3A22Z,status,draft',
{
  method: 'POST',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://elections.hse.ru/elections/create',
  params: {
  'election' => '[Election](#schemaelection)'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://elections.hse.ru/elections/create', params={
  'election': {
  "id": "string",
  "name": "Выборы в КпЦ",
  "priority": 0,
  "isRunoff": true,
  "mandates": 0,
  "isForNearForeign": true,
  "isForFarForeign": true,
  "acceptedCouncilOrganizationsIds": [
    1,
    2
  ],
  "acceptedFacultiesIds": [
    1,
    2
  ],
  "acceptedDormitoriesIds": [
    1,
    2
  ],
  "startTime": "2019-08-24T14:15:22Z",
  "finishTime": "2019-08-24T14:15:22Z",
  "status": "draft"
}
}, headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://elections.hse.ru/elections/create', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://elections.hse.ru/elections/create?election=id,string,name,%D0%92%D1%8B%D0%B1%D0%BE%D1%80%D1%8B%20%D0%B2%20%D0%9A%D0%BF%D0%A6,priority,0,isRunoff,true,mandates,0,isForNearForeign,true,isForFarForeign,true,acceptedCouncilOrganizationsIds,1%2C2,acceptedFacultiesIds,1%2C2,acceptedDormitoriesIds,1%2C2,startTime,2019-08-24T14%3A15%3A22Z,finishTime,2019-08-24T14%3A15%3A22Z,status,draft");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://elections.hse.ru/elections/create", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /elections/create`

*Создать выборы*

Создает выборы, для администратора

<h3 id="post__elections_create-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|election|query|[Election](#schemaelection)|true|election|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "name": "Выборы в КпЦ",
  "priority": 0,
  "isRunoff": true,
  "mandates": 0,
  "isForNearForeign": true,
  "isForFarForeign": true,
  "acceptedCouncilOrganizationsIds": [
    1,
    2
  ],
  "acceptedFacultiesIds": [
    1,
    2
  ],
  "acceptedDormitoriesIds": [
    1,
    2
  ],
  "startTime": "2019-08-24T14:15:22Z",
  "finishTime": "2019-08-24T14:15:22Z",
  "status": "draft"
}
```

<h3 id="post__elections_create-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Успешно|[Election](#schemaelection)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Невалидно|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
elk_auth ( Scopes: admin )
</aside>

## post__elections_approveCandidate_{electionId}_{candidateId}

> Code samples

```shell
# You can also use wget
curl -X POST https://elections.hse.ru/elections/approveCandidate/{electionId}/{candidateId}?approve=true \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://elections.hse.ru/elections/approveCandidate/{electionId}/{candidateId}?approve=true HTTP/1.1
Host: elections.hse.ru

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://elections.hse.ru/elections/approveCandidate/{electionId}/{candidateId}?approve=true',
{
  method: 'POST',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://elections.hse.ru/elections/approveCandidate/{electionId}/{candidateId}',
  params: {
  'approve' => 'boolean'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://elections.hse.ru/elections/approveCandidate/{electionId}/{candidateId}', params={
  'approve': 'true'
}, headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://elections.hse.ru/elections/approveCandidate/{electionId}/{candidateId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://elections.hse.ru/elections/approveCandidate/{electionId}/{candidateId}?approve=true");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://elections.hse.ru/elections/approveCandidate/{electionId}/{candidateId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /elections/approveCandidate/{electionId}/{candidateId}`

*Одобрить/отклонить кандидата*

Одобрить/отклонить кандидата

<h3 id="post__elections_approvecandidate_{electionid}_{candidateid}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|electionId|path|string|true|ID выборов|
|candidateId|path|string|true|Кандидат в выборы|
|approve|query|boolean|true|Одобрить/отклонить заявку|

<h3 id="post__elections_approvecandidate_{electionid}_{candidateid}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Успешно|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Невалидно|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
elk_auth ( Scopes: admin )
</aside>

## post__elections_next_{electionId}

> Code samples

```shell
# You can also use wget
curl -X POST https://elections.hse.ru/elections/next/{electionId} \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://elections.hse.ru/elections/next/{electionId} HTTP/1.1
Host: elections.hse.ru

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://elections.hse.ru/elections/next/{electionId}',
{
  method: 'POST',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://elections.hse.ru/elections/next/{electionId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://elections.hse.ru/elections/next/{electionId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://elections.hse.ru/elections/next/{electionId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://elections.hse.ru/elections/next/{electionId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://elections.hse.ru/elections/next/{electionId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /elections/next/{electionId}`

*Перенести выборы на следующий этап*

Перенести выборы на следующий этап

<h3 id="post__elections_next_{electionid}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|electionId|path|string|true|ID|

<h3 id="post__elections_next_{electionid}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Выполнено|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Невалидный ID|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
elk_auth ( Scopes: admin )
</aside>

## get__elections_getAllCandidates

> Code samples

```shell
# You can also use wget
curl -X GET https://elections.hse.ru/elections/getAllCandidates \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://elections.hse.ru/elections/getAllCandidates HTTP/1.1
Host: elections.hse.ru
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://elections.hse.ru/elections/getAllCandidates',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://elections.hse.ru/elections/getAllCandidates',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://elections.hse.ru/elections/getAllCandidates', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://elections.hse.ru/elections/getAllCandidates', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://elections.hse.ru/elections/getAllCandidates");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://elections.hse.ru/elections/getAllCandidates", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /elections/getAllCandidates`

*Получить всех кандидатов*

Получить всех кандидатов

> Example responses

> 200 Response

```json
[
  {
    "id": 1,
    "electionId": 1,
    "name": "Имя",
    "photoUrl": "https://img.com/img.png",
    "description": "Программа",
    "approved": true,
    "waitingForApprove": true
  }
]
```

<h3 id="get__elections_getallcandidates-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Возвращает кандидатов|Inline|

<h3 id="get__elections_getallcandidates-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Candidate](#schemacandidate)]|false|none|none|
|» id|string|true|none|none|
|» electionId|integer(int64)|true|none|none|
|» name|string|true|none|none|
|» photoUrl|string(url)|true|none|none|
|» description|string|true|none|none|
|» approved|boolean|true|none|none|
|» waitingForApprove|boolean|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
elk_auth ( Scopes: admin )
</aside>

<h1 id="swagger-smart-elections-dictionary">dictionary</h1>

Справочники

## get__dictionaries_councilOrganizations

> Code samples

```shell
# You can also use wget
curl -X GET https://elections.hse.ru/dictionaries/councilOrganizations \
  -H 'Accept: application/json'

```

```http
GET https://elections.hse.ru/dictionaries/councilOrganizations HTTP/1.1
Host: elections.hse.ru
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://elections.hse.ru/dictionaries/councilOrganizations',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://elections.hse.ru/dictionaries/councilOrganizations',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://elections.hse.ru/dictionaries/councilOrganizations', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://elections.hse.ru/dictionaries/councilOrganizations', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://elections.hse.ru/dictionaries/councilOrganizations");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://elections.hse.ru/dictionaries/councilOrganizations", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /dictionaries/councilOrganizations`

*Студенческие организации*

Возвращает студенческие организации

> Example responses

> 200 Response

```json
[
  {
    "id": 1,
    "name": "Коммитет по цифровизации"
  }
]
```

<h3 id="get__dictionaries_councilorganizations-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Возвращает студенческие организации|Inline|

<h3 id="get__dictionaries_councilorganizations-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[CouncilOrganization](#schemacouncilorganization)]|false|none|none|
|» id|string|true|none|none|
|» name|string|true|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## get__dictionaries_faculty

> Code samples

```shell
# You can also use wget
curl -X GET https://elections.hse.ru/dictionaries/faculty \
  -H 'Accept: application/json'

```

```http
GET https://elections.hse.ru/dictionaries/faculty HTTP/1.1
Host: elections.hse.ru
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://elections.hse.ru/dictionaries/faculty',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://elections.hse.ru/dictionaries/faculty',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://elections.hse.ru/dictionaries/faculty', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://elections.hse.ru/dictionaries/faculty', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://elections.hse.ru/dictionaries/faculty");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://elections.hse.ru/dictionaries/faculty", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /dictionaries/faculty`

*Факультеты*

Возвращает факультеты

> Example responses

> 200 Response

```json
[
  {
    "id": 1,
    "name": "Факультет компьютерных наук"
  }
]
```

<h3 id="get__dictionaries_faculty-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Возвращает факультеты|Inline|

<h3 id="get__dictionaries_faculty-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Faculty](#schemafaculty)]|false|none|none|
|» id|string|true|none|none|
|» name|string|true|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## get__dictionaries_dormitory

> Code samples

```shell
# You can also use wget
curl -X GET https://elections.hse.ru/dictionaries/dormitory \
  -H 'Accept: application/json'

```

```http
GET https://elections.hse.ru/dictionaries/dormitory HTTP/1.1
Host: elections.hse.ru
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://elections.hse.ru/dictionaries/dormitory',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://elections.hse.ru/dictionaries/dormitory',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://elections.hse.ru/dictionaries/dormitory', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://elections.hse.ru/dictionaries/dormitory', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://elections.hse.ru/dictionaries/dormitory");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://elections.hse.ru/dictionaries/dormitory", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /dictionaries/dormitory`

*Общежития*

Возвращает общежития

> Example responses

> 200 Response

```json
[
  {
    "id": 1,
    "name": "Общежитие №5"
  }
]
```

<h3 id="get__dictionaries_dormitory-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Возвращает общежития|Inline|

<h3 id="get__dictionaries_dormitory-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Dormitory](#schemadormitory)]|false|none|none|
|» id|string|true|none|none|
|» name|string|true|none|none|

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

<h2 id="tocS_Elector">Elector</h2>
<!-- backwards compatibility -->
<a id="schemaelector"></a>
<a id="schema_Elector"></a>
<a id="tocSelector"></a>
<a id="tocselector"></a>

```json
{
  "id": 1,
  "fullname": "Иванов Иван Иванович",
  "email": "iiivanov@edu.hse.ru",
  "isDormitoryStudent": true,
  "dormitoryId": 1,
  "facultyIds": [
    1,
    2
  ],
  "isCouncil": true,
  "councilOrganizationIds": [
    1,
    2
  ],
  "isPostGraduate": true,
  "isNearForeign": true,
  "isFarForeign": true
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|fullname|string|false|none|none|
|email|string(email)|true|none|none|
|isDormitoryStudent|boolean|true|none|none|
|dormitoryId|string|false|none|none|
|facultyIds|[string]|true|none|none|
|isCouncil|boolean|true|none|none|
|councilOrganizationIds|[integer]|false|none|none|
|isPostGraduate|boolean|true|none|none|
|isNearForeign|boolean|true|none|none|
|isFarForeign|boolean|true|none|none|

<h2 id="tocS_Faculty">Faculty</h2>
<!-- backwards compatibility -->
<a id="schemafaculty"></a>
<a id="schema_Faculty"></a>
<a id="tocSfaculty"></a>
<a id="tocsfaculty"></a>

```json
{
  "id": 1,
  "name": "Факультет компьютерных наук"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|name|string|true|none|none|

<h2 id="tocS_Dormitory">Dormitory</h2>
<!-- backwards compatibility -->
<a id="schemadormitory"></a>
<a id="schema_Dormitory"></a>
<a id="tocSdormitory"></a>
<a id="tocsdormitory"></a>

```json
{
  "id": 1,
  "name": "Общежитие №5"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|name|string|true|none|none|

<h2 id="tocS_CouncilOrganization">CouncilOrganization</h2>
<!-- backwards compatibility -->
<a id="schemacouncilorganization"></a>
<a id="schema_CouncilOrganization"></a>
<a id="tocScouncilorganization"></a>
<a id="tocscouncilorganization"></a>

```json
{
  "id": 1,
  "name": "Коммитет по цифровизации"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|name|string|true|none|none|

<h2 id="tocS_Election">Election</h2>
<!-- backwards compatibility -->
<a id="schemaelection"></a>
<a id="schema_Election"></a>
<a id="tocSelection"></a>
<a id="tocselection"></a>

```json
{
  "id": "string",
  "name": "Выборы в КпЦ",
  "priority": 0,
  "isRunoff": true,
  "mandates": 0,
  "isForNearForeign": true,
  "isForFarForeign": true,
  "acceptedCouncilOrganizationsIds": [
    1,
    2
  ],
  "acceptedFacultiesIds": [
    1,
    2
  ],
  "acceptedDormitoriesIds": [
    1,
    2
  ],
  "startTime": "2019-08-24T14:15:22Z",
  "finishTime": "2019-08-24T14:15:22Z",
  "status": "draft"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|name|string|true|none|none|
|priority|integer(int64)|true|none|none|
|isRunoff|boolean|true|none|none|
|mandates|integer(int64)|false|none|none|
|isForNearForeign|boolean|true|none|none|
|isForFarForeign|boolean|true|none|none|
|acceptedCouncilOrganizationsIds|[string]|false|none|none|
|acceptedFacultiesIds|[string]|false|none|none|
|acceptedDormitoriesIds|[string]|false|none|none|
|startTime|string(date-time)|true|none|none|
|finishTime|string(date-time)|false|none|none|
|status|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|status|draft|
|status|created|
|status|waiting|
|status|started|
|status|finished|
|status|decrypted|
|status|results|

<h2 id="tocS_ElectionResults">ElectionResults</h2>
<!-- backwards compatibility -->
<a id="schemaelectionresults"></a>
<a id="schema_ElectionResults"></a>
<a id="tocSelectionresults"></a>
<a id="tocselectionresults"></a>

```json
{
  "candidates": {
    "candidateId": 1,
    "voices": 1
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|candidates|object|false|none|none|
|» candidateId|string|false|none|none|
|» voices|integer(int64)|false|none|none|

<h2 id="tocS_Candidate">Candidate</h2>
<!-- backwards compatibility -->
<a id="schemacandidate"></a>
<a id="schema_Candidate"></a>
<a id="tocScandidate"></a>
<a id="tocscandidate"></a>

```json
{
  "id": 1,
  "electionId": 1,
  "name": "Имя",
  "photoUrl": "https://img.com/img.png",
  "description": "Программа",
  "approved": true,
  "waitingForApprove": true
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|electionId|integer(int64)|true|none|none|
|name|string|true|none|none|
|photoUrl|string(url)|true|none|none|
|description|string|true|none|none|
|approved|boolean|true|none|none|
|waitingForApprove|boolean|false|none|none|

<h2 id="tocS_CandidateRequest">CandidateRequest</h2>
<!-- backwards compatibility -->
<a id="schemacandidaterequest"></a>
<a id="schema_CandidateRequest"></a>
<a id="tocScandidaterequest"></a>
<a id="tocscandidaterequest"></a>

```json
{
  "name": "Имя",
  "photoUrl": "https://img.com/img.png",
  "description": "Программа"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|true|none|none|
|photoUrl|string(url)|true|none|none|
|description|string|true|none|none|

