# GradAtlas Information Access Documentation

## About
GradAtlas is a web-based platform designed to centralize and simplify event discovery for graduate students in Seattle. Its audience includes students seeking social, academic, and professional engagement opportunities relevant to their interests, schedules, and location preferences. Information is gathered from public sources like Meetup and Everout and standardized into a searchable structure. Users can access the data via a responsive web interface or REST API. The system supports portable formats such as JSON and CSV to allow easy export and offline analysis.

## Methodology
- The information structure was created using a sample dataset of events stored in a JSON file (`meetups-list.json`).
- Flask was used to expose a RESTful API with endpoints for GET, POST, and filtered queries.
- An HTML form (`/add`) was provided to allow non-technical users to contribute data.
- New events are manually inputted using the interface (see "Add a New Meetup").
- The events are stored in a JSON file using a standardized JSON schema format.
- This ensures that all events maintain a consistent structure and metadata for reliable access and search functionality.
- The data is maintained by appending new submissions to the JSON file.
- It can be extended by connecting a SQLite database.
- To update the event list, our app uses Flask’s POST operator at `http://127.0.0.1:5002/add`.

## Access
- Users can navigate the GradAtlas website using any web browser on desktop or mobile devices.
- GradAtlas provides a user-friendly search interface using HTML and JavaScript with support for tag, title, location, and detail queries (`http://127.0.0.1:5002/search`).
- Users can search events using keyword searches or apply filters.
- Each event detail page includes venue, timing, cost, RSVP links, and special requirements.
- Search results can be exported to a CSV file.
- REST API Endpoints:
  - All meetups: `http://127.0.0.1:5002/meetups`
  - Filter by tag: `http://127.0.0.1:5002/meetups/tag/<tag>`
  - Search interface: `http://127.0.0.1:5002/search`

## Structure
The GradAtlas data structure includes:
- `name` (string): Event name
- `host` (string): Host or organization
- `details` (string): Description of the event
- `location` (string): City or venue
- `attendees` (integer): Number of expected attendees
- `tags` (array of strings): Keywords like "Social", "Book Club", "machine-learning"

Data is stored in a consistent JSON schema to support structured access and integration.

## Example

### Request
```
GET /meetups/tag/Book%20Club
```

### Response
```json
[
  {
    "name": "Book Club - Abundance",
    "host": "Ryan",
    "details": "Welcome to the Seattle Intellectual Book Club...",
    "location": "Seattle, WA",
    "attendees": 28,
    "tags": ["Book Club", "Hanging Out", "Social"]
  }
]
```
