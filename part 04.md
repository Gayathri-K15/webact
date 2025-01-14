sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML, CSS, and JavaScript files
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Existing notes in JSON format
    deactivate server

    browser->>browser: User types a new note in the text field
    browser->>browser: User clicks the "Save" button
    Note right of browser: Browser prepares POST request with new note content

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    Note right of server: Server processes the new note and stores it
    activate server
    server-->>browser: Success response (200 OK)
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Updated JSON data with the new note
    deactivate server

    browser->>browser: Browser re-renders the page with the updated notes
