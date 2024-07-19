## 0.4: New note diagram

```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>browser: HTML/Redirect - (submitting the form input)
    deactivate server

    Note right of server: The server asks the browser to perform a new HTTP GET request <br> to the address defined in the header's Location - the address notes

    Note right of browser: The Browser reloads the Notes page.

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    Note right of browser: The reload causes six more HTTP requests.

    browser->>server: GET https://studies.cs.helsinki.fi/319deed6-0e9f-4865-932c-7f052b20c0d9
    activate server
    server-->>browser: Some javascript
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/stats/0ab54153eeeca0ce03978cc463b257f7.woff2
    activate server
    server-->>browser: Font file
    deactivate server

    browser->>server: GET https://fonts.gstatic.com/s/lato/v24/S6uyw4BMUTPHjx4wXiWtFCc.woff2
    activate server
    server-->>browser: Font file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: Javascript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Json Data -  [{content: "Testing from COL", date: "2024-07-18T00:08:16.664Z"}, ...]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes
```