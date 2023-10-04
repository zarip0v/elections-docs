---
title: Swagger Smart Elections v0.0.3
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

<h1 id="swagger-smart-elections">Swagger Smart Elections v0.0.3</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Base URLs:

* <a href="https://elections.hse.ru">https://elections.hse.ru</a>

# Authentication

- oAuth2 authentication. 

    - Flow: implicit
    - Authorization URL = [https://elections.hse.ru/auth/elk](https://elections.hse.ru/auth/elk)

|Scope|Scope Description|
|---|---|
|elect|view elections|
|observe|set keys|
|admin|create and manage elections|

<h1 id="swagger-smart-elections-elector">elector</h1>

Инструментарий для пользователя

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
  {
    "name": "Выборы в КпЦ",
    "isRunoff": true,
    "mandates": 0,
    "isForNearForeign": true,
    "isForFarForeign": true,
    "acceptedCampusesIds": [
      1,
      2
    ],
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
    "acceptedCities": [
      "Москва",
      "Пермь"
    ],
    "startTime": "2019-08-24T14:15:22Z",
    "finishTime": "2019-08-24T14:15:22Z",
    "status": "waiting"
  }
]
```

<h3 id="get__elections_all-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Возвращает выборы|Inline|

<h3 id="get__elections_all-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Election](#schemaelection)]|false|none|none|
|» name|string|true|none|none|
|» isRunoff|boolean|true|none|none|
|» mandates|integer(int64)|false|none|none|
|» isForNearForeign|boolean|true|none|none|
|» isForFarForeign|boolean|true|none|none|
|» acceptedCampusesIds|[integer]|false|none|none|
|» acceptedCouncilOrganizationsIds|[integer]|false|none|none|
|» acceptedFacultiesIds|[integer]|false|none|none|
|» acceptedDormitoriesIds|[integer]|false|none|none|
|» acceptedCities|[string]|false|none|none|
|» startTime|string(date-time)|true|none|none|
|» finishTime|string(date-time)|false|none|none|
|» status|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|status|waiting|
|status|started|
|status|finished|
|status|results|

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
|electionId|path|integer(int64)|true|ID|

> Example responses

> 200 Response

```json
{
  "name": "Выборы в КпЦ",
  "isRunoff": true,
  "mandates": 0,
  "isForNearForeign": true,
  "isForFarForeign": true,
  "acceptedCampusesIds": [
    1,
    2
  ],
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
  "acceptedCities": [
    "Москва",
    "Пермь"
  ],
  "startTime": "2019-08-24T14:15:22Z",
  "finishTime": "2019-08-24T14:15:22Z",
  "status": "waiting"
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
|electionId|path|integer(int64)|true|ID|

> Example responses

> 200 Response

```json
[
  {
    "studentId": 1,
    "description": "Программа"
  }
]
```

<h3 id="get__elections_getcandidates_{electionid}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Возвращает выборы|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Невалидный ID|None|

<h3 id="get__elections_getcandidates_{electionid}-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Candidate](#schemacandidate)]|false|none|none|
|» studentId|integer(int64)|true|none|none|
|» description|string|false|none|none|

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
|electionId|path|integer(int64)|true|ID|

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
|electionId|path|integer(int64)|true|ID|
|voice|query|string|false|Зашифрованная публичным ключом строка JSON: в случае runoff [candidateId, candidateId] в порядке предпочтения, иначе - [[candidateId, voicesCount], [candidateId, voicesCount]]|

<h3 id="post__elections_vote_{electionid}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Голос принят|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Неверно|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
elk_auth ( Scopes: elect )
</aside>

## post__elections_publicKey_{electionId}

> Code samples

```shell
# You can also use wget
curl -X POST https://elections.hse.ru/elections/publicKey/{electionId} \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://elections.hse.ru/elections/publicKey/{electionId} HTTP/1.1
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

result = RestClient.post 'https://elections.hse.ru/elections/publicKey/{electionId}',
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

r = requests.post('https://elections.hse.ru/elections/publicKey/{electionId}', headers = headers)

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
    $response = $client->request('POST','https://elections.hse.ru/elections/publicKey/{electionId}', array(
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
    req, err := http.NewRequest("POST", "https://elections.hse.ru/elections/publicKey/{electionId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /elections/publicKey/{electionId}`

*Получить публичный ключ*

<h3 id="post__elections_publickey_{electionid}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|electionId|path|integer(int64)|true|ID|

> Example responses

> 200 Response

```json
"string"
```

<h3 id="post__elections_publickey_{electionid}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Возвращает публичный ключ|string|

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
|electionId|path|integer(int64)|true|none|
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
|electionId|path|integer(int64)|true|none|
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
curl -X POST https://elections.hse.ru/elections/create?election=name,%D0%92%D1%8B%D0%B1%D0%BE%D1%80%D1%8B%20%D0%B2%20%D0%9A%D0%BF%D0%A6,isRunoff,true,mandates,0,isForNearForeign,true,isForFarForeign,true,acceptedCampusesIds,1%2C2,acceptedCouncilOrganizationsIds,1%2C2,acceptedFacultiesIds,1%2C2,acceptedDormitoriesIds,1%2C2,acceptedCities,%D0%9C%D0%BE%D1%81%D0%BA%D0%B2%D0%B0%2C%D0%9F%D0%B5%D1%80%D0%BC%D1%8C,startTime,2019-08-24T14%3A15%3A22Z,finishTime,2019-08-24T14%3A15%3A22Z,status,waiting \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://elections.hse.ru/elections/create?election=name,%D0%92%D1%8B%D0%B1%D0%BE%D1%80%D1%8B%20%D0%B2%20%D0%9A%D0%BF%D0%A6,isRunoff,true,mandates,0,isForNearForeign,true,isForFarForeign,true,acceptedCampusesIds,1%2C2,acceptedCouncilOrganizationsIds,1%2C2,acceptedFacultiesIds,1%2C2,acceptedDormitoriesIds,1%2C2,acceptedCities,%D0%9C%D0%BE%D1%81%D0%BA%D0%B2%D0%B0%2C%D0%9F%D0%B5%D1%80%D0%BC%D1%8C,startTime,2019-08-24T14%3A15%3A22Z,finishTime,2019-08-24T14%3A15%3A22Z,status,waiting HTTP/1.1
Host: elections.hse.ru

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://elections.hse.ru/elections/create?election=name,%D0%92%D1%8B%D0%B1%D0%BE%D1%80%D1%8B%20%D0%B2%20%D0%9A%D0%BF%D0%A6,isRunoff,true,mandates,0,isForNearForeign,true,isForFarForeign,true,acceptedCampusesIds,1%2C2,acceptedCouncilOrganizationsIds,1%2C2,acceptedFacultiesIds,1%2C2,acceptedDormitoriesIds,1%2C2,acceptedCities,%D0%9C%D0%BE%D1%81%D0%BA%D0%B2%D0%B0%2C%D0%9F%D0%B5%D1%80%D0%BC%D1%8C,startTime,2019-08-24T14%3A15%3A22Z,finishTime,2019-08-24T14%3A15%3A22Z,status,waiting',
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

result = RestClient.post 'https://elections.hse.ru/elections/create',
  params: {
  'election' => '[Election](#schemaelection)'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://elections.hse.ru/elections/create', params={
  'election': {
  "name": "Выборы в КпЦ",
  "isRunoff": true,
  "mandates": 0,
  "isForNearForeign": true,
  "isForFarForeign": true,
  "acceptedCampusesIds": [
    1,
    2
  ],
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
  "acceptedCities": [
    "Москва",
    "Пермь"
  ],
  "startTime": "2019-08-24T14:15:22Z",
  "finishTime": "2019-08-24T14:15:22Z",
  "status": "waiting"
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
URL obj = new URL("https://elections.hse.ru/elections/create?election=name,%D0%92%D1%8B%D0%B1%D0%BE%D1%80%D1%8B%20%D0%B2%20%D0%9A%D0%BF%D0%A6,isRunoff,true,mandates,0,isForNearForeign,true,isForFarForeign,true,acceptedCampusesIds,1%2C2,acceptedCouncilOrganizationsIds,1%2C2,acceptedFacultiesIds,1%2C2,acceptedDormitoriesIds,1%2C2,acceptedCities,%D0%9C%D0%BE%D1%81%D0%BA%D0%B2%D0%B0%2C%D0%9F%D0%B5%D1%80%D0%BC%D1%8C,startTime,2019-08-24T14%3A15%3A22Z,finishTime,2019-08-24T14%3A15%3A22Z,status,waiting");
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

<h3 id="post__elections_create-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Успешно|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Невалидно|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
elk_auth ( Scopes: admin )
</aside>

## post__elections_addCandidate_{electionId}

> Code samples

```shell
# You can also use wget
curl -X POST https://elections.hse.ru/elections/addCandidate/{electionId}?candidate=studentId,1,description,%D0%9F%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B0 \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://elections.hse.ru/elections/addCandidate/{electionId}?candidate=studentId,1,description,%D0%9F%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B0 HTTP/1.1
Host: elections.hse.ru

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://elections.hse.ru/elections/addCandidate/{electionId}?candidate=studentId,1,description,%D0%9F%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B0',
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

result = RestClient.post 'https://elections.hse.ru/elections/addCandidate/{electionId}',
  params: {
  'candidate' => '[Candidate](#schemacandidate)'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://elections.hse.ru/elections/addCandidate/{electionId}', params={
  'candidate': {
  "studentId": 1,
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
    $response = $client->request('POST','https://elections.hse.ru/elections/addCandidate/{electionId}', array(
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
URL obj = new URL("https://elections.hse.ru/elections/addCandidate/{electionId}?candidate=studentId,1,description,%D0%9F%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B0");
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
    req, err := http.NewRequest("POST", "https://elections.hse.ru/elections/addCandidate/{electionId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /elections/addCandidate/{electionId}`

*Добавить кандидата в выборы*

Добавить кандидата в выборы

<h3 id="post__elections_addcandidate_{electionid}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|electionId|path|integer(int64)|true|Выборы|
|candidate|query|[Candidate](#schemacandidate)|true|Кандидат|

<h3 id="post__elections_addcandidate_{electionid}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Успешно|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Невалидно|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
elk_auth ( Scopes: admin )
</aside>

<h1 id="swagger-smart-elections-dictionary">dictionary</h1>

Справочники

## get__dictionaries_campus

> Code samples

```shell
# You can also use wget
curl -X GET https://elections.hse.ru/dictionaries/campus \
  -H 'Accept: application/json'

```

```http
GET https://elections.hse.ru/dictionaries/campus HTTP/1.1
Host: elections.hse.ru
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://elections.hse.ru/dictionaries/campus',
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

result = RestClient.get 'https://elections.hse.ru/dictionaries/campus',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://elections.hse.ru/dictionaries/campus', headers = headers)

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
    $response = $client->request('GET','https://elections.hse.ru/dictionaries/campus', array(
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
URL obj = new URL("https://elections.hse.ru/dictionaries/campus");
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
    req, err := http.NewRequest("GET", "https://elections.hse.ru/dictionaries/campus", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /dictionaries/campus`

*Кампусы*

Возвращает кампусы

> Example responses

> 200 Response

```json
[
  {
    "id": 1,
    "name": "Москва"
  }
]
```

<h3 id="get__dictionaries_campus-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Возвращает кампусы|Inline|

<h3 id="get__dictionaries_campus-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Campus](#schemacampus)]|false|none|none|
|» id|integer(int64)|true|none|none|
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
    "name": "Факультет компьютерных наук",
    "campusId": 1
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
|» id|integer(int64)|true|none|none|
|» name|string|true|none|none|
|» campusId|integer(int64)|true|none|none|

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
    "name": "Общежитие №5",
    "campusId": 1
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
|» id|integer(int64)|true|none|none|
|» name|string|true|none|none|
|» campusId|integer(int64)|true|none|none|

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
  "firstname": "Иван",
  "lastname": "Иванов",
  "middlename": "Иванович",
  "email": "iiivanov@edu.hse.ru",
  "campusId": 1,
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
  "isFarForeign": true,
  "city": "Moscow"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer(int64)|true|none|none|
|firstname|string|true|none|none|
|lastname|string|true|none|none|
|middlename|string|false|none|none|
|email|string(email)|true|none|none|
|campusId|integer(int64)|false|none|none|
|isDormitoryStudent|boolean|true|none|none|
|dormitoryId|integer(int64)|false|none|none|
|facultyIds|[integer]|true|none|none|
|isCouncil|boolean|true|none|none|
|councilOrganizationIds|[integer]|false|none|none|
|isPostGraduate|boolean|true|none|none|
|isNearForeign|boolean|true|none|none|
|isFarForeign|boolean|true|none|none|
|city|string|true|none|none|

<h2 id="tocS_Campus">Campus</h2>
<!-- backwards compatibility -->
<a id="schemacampus"></a>
<a id="schema_Campus"></a>
<a id="tocScampus"></a>
<a id="tocscampus"></a>

```json
{
  "id": 1,
  "name": "Москва"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer(int64)|true|none|none|
|name|string|true|none|none|

<h2 id="tocS_Faculty">Faculty</h2>
<!-- backwards compatibility -->
<a id="schemafaculty"></a>
<a id="schema_Faculty"></a>
<a id="tocSfaculty"></a>
<a id="tocsfaculty"></a>

```json
{
  "id": 1,
  "name": "Факультет компьютерных наук",
  "campusId": 1
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer(int64)|true|none|none|
|name|string|true|none|none|
|campusId|integer(int64)|true|none|none|

<h2 id="tocS_Dormitory">Dormitory</h2>
<!-- backwards compatibility -->
<a id="schemadormitory"></a>
<a id="schema_Dormitory"></a>
<a id="tocSdormitory"></a>
<a id="tocsdormitory"></a>

```json
{
  "id": 1,
  "name": "Общежитие №5",
  "campusId": 1
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer(int64)|true|none|none|
|name|string|true|none|none|
|campusId|integer(int64)|true|none|none|

<h2 id="tocS_CouncilOrganization">CouncilOrganization</h2>
<!-- backwards compatibility -->
<a id="schemacouncilorganization"></a>
<a id="schema_CouncilOrganization"></a>
<a id="tocScouncilorganization"></a>
<a id="tocscouncilorganization"></a>

```json
{
  "id": 1,
  "name": "Коммитет по цифровизации",
  "campusId": 1
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer(int64)|true|none|none|
|name|string|true|none|none|
|campusId|integer(int64)|true|none|none|

<h2 id="tocS_Election">Election</h2>
<!-- backwards compatibility -->
<a id="schemaelection"></a>
<a id="schema_Election"></a>
<a id="tocSelection"></a>
<a id="tocselection"></a>

```json
{
  "name": "Выборы в КпЦ",
  "isRunoff": true,
  "mandates": 0,
  "isForNearForeign": true,
  "isForFarForeign": true,
  "acceptedCampusesIds": [
    1,
    2
  ],
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
  "acceptedCities": [
    "Москва",
    "Пермь"
  ],
  "startTime": "2019-08-24T14:15:22Z",
  "finishTime": "2019-08-24T14:15:22Z",
  "status": "waiting"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|true|none|none|
|isRunoff|boolean|true|none|none|
|mandates|integer(int64)|false|none|none|
|isForNearForeign|boolean|true|none|none|
|isForFarForeign|boolean|true|none|none|
|acceptedCampusesIds|[integer]|false|none|none|
|acceptedCouncilOrganizationsIds|[integer]|false|none|none|
|acceptedFacultiesIds|[integer]|false|none|none|
|acceptedDormitoriesIds|[integer]|false|none|none|
|acceptedCities|[string]|false|none|none|
|startTime|string(date-time)|true|none|none|
|finishTime|string(date-time)|false|none|none|
|status|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|status|waiting|
|status|started|
|status|finished|
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
|» candidateId|integer(int64)|false|none|none|
|» voices|integer(int64)|false|none|none|

<h2 id="tocS_Candidate">Candidate</h2>
<!-- backwards compatibility -->
<a id="schemacandidate"></a>
<a id="schema_Candidate"></a>
<a id="tocScandidate"></a>
<a id="tocscandidate"></a>

```json
{
  "studentId": 1,
  "description": "Программа"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|studentId|integer(int64)|true|none|none|
|description|string|false|none|none|

