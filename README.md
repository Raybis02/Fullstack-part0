# Fullstack-part0

## Exercise 0.4
```mermaid
  sequenceDiagram
    participant browser
    participant server

    Note right of browser: User types a note in the text field and clicks Save

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    Note right of server: Server processes the submitted note 
    Note right of server: (creating new node object and adding it to notes array)
    server-->>browser: 302 Redirect to /notes
    deactivate server

    Note right of browser: Browser follows the redirect
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Updated JSON with the new note [{ "content": "New note", "date": "2024-12-03" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the updated notes
```
## Exercise 0.5
``` mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code to render the app

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: JSON data with notes [{ "content": "New note", "date": "2024-12-03" }, ... ]
    deactivate server

    Note right of browser: The browser uses the JSON data to render the notes dynamically without reloading the page
```

## Exercise 0.6
``` mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: User types a note in the text field and clicks Save

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note right of server: Server processes the submitted note and updates the database
    server-->>browser: 201 Created (success response)
    deactivate server

    Note right of browser: Browser updates the notes list dynamically using the new note without reloading the page
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Updated JSON with the new note [{ "content": "New SPA note", "date": "2024-12-03" }, ... ]
    deactivate server

    Note right of browser: The browser renders the updated list of notes dynamically
```
