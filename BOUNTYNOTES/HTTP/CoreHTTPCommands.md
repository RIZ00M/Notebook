# Core HTTP Commands & Request Anatomy

## HTTP Methods (Verbs)

| Method |
|---|
| GET |
| POST |
| PUT |
| DELETE |
| PATCH |
| HEAD |
| OPTIONS |
| CONNECT |
| TRACE |

## Anatomy of a Request/Response

| Component | Description |
|---|---|
| Scheme | Tells us which protocol was used: HTTP or HTTPS. |
| Host | Tells us the name of the host we request resources from. |
| Filename | Indicates which file we requested from the host. In our request, this is `/`, which actually translates to `index.html`. |
| Address | Displays the IP address where the website is hosted. In our example, we are hosting the website on the same device — that's why the address `127.0.0.1` is shown. |
| Status | Indicates whether the request was successful. In our example, we received a `200 OK` status, meaning the request was successful. |
