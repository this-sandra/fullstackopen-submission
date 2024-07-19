## 0.6: New note in Single page app diagram

```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    server-->>browser: JSON Data [{content: "Hejsan", date: "2024-07-18T14:42:36.170Z"}] <br> containing both the content of the note (content) and the timestamp (date).
    deactivate server

    Note right of request: The Content-Type header of the request tells the server <br> that the included data is represented in JSON.
    Note right of server: The server responds with status code 201 created <br> and does not ask for a redirect.
    Note right of browser: SPA version of the app uses the Javascript code <br> that is fetched from the server. 
```