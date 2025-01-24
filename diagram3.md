sequenceDiagram
    participant browser
    participant server

    Note over browser: User types a note in the input field<br>and clicks the "Save" button

    browser->>server: POST /new_note_spa<br>Payload: { "content": "New note", "date": "2025-01-24" }
    activate server
    server-->>browser: HTTP 201 Created<br>{ "message": "Note saved successfully" }
    deactivate server

    Note right of browser: The app updates the list of notes locally<br>without requiring a server fetch
