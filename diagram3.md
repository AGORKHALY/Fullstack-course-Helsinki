sequenceDiagram
    participant browser
    participant server

    Note over browser: User types a new note in the input field and clicks "Save"

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa<br>Payload: { "content": "New note", "date": "2025-01-24" }
    activate server
    server-->>browser: HTTP 201 Created<br>{ "message": "Note saved successfully" }
    deactivate server

    Note right of browser: The app updates the list of notes<br>by appending the new note locally

    browser->>server: (Optional) GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Updated JSON data (list of notes)
    deactivate server

    Note right of browser: The browser dynamically re-renders the updated list of notes<br>without reloading the page
