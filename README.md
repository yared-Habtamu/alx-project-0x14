## API Overview

The **MoviesDatabase API** provides complete and updated data for over **9 million titles** (movies, series, episodes) with ratings, cast, genres, and more.

* **Recent titles** updated weekly
* **Ratings & episodes** updated daily
* Multiple filtering, sorting, and search options
* Supports querying titles, actors, ratings, seasons, episodes, and upcoming releases

## Version

**v1** (based on provided documentation)

## Available Endpoints

### Titles

* **`GET /titles`** — Returns multiple titles with optional filters and sorting.
* **`GET /x/titles-by-ids`** — Returns titles by a list of IMDb IDs.
* **`GET /titles/{id}`** — Returns detailed info for a specific title.
* **`GET /titles/{id}/ratings`** — Returns rating and votes for a title.
* **`GET /titles/series/{id}`** — Lists all episodes (light data) for a series.
* **`GET /titles/seasons/{id}`** — Returns number of seasons for a series.
* **`GET /titles/series/{id}/{season}`** — Lists all episodes (light data) for a specific season.
* **`GET /titles/episode/{id}`** — Returns details for a specific episode.
* **`GET /titles/x/upcoming`** — Returns upcoming titles.

### Search

* **`GET /titles/search/keyword/{keyword}`** — Search by keyword.
* **`GET /titles/search/title/{title}`** — Search by title (exact or partial).
* **`GET /titles/search/akas/{aka}`** — Search by alternate title (exact match).

### Actors

* **`GET /actors`** — Returns actors with optional pagination.
* **`GET /actors/{id}`** — Returns details for a specific actor.

### Utils

* **`GET /title/utils/titleType`** — Returns list of title types.
* **`GET /title/utils/genres`** — Returns list of genres.
* **`GET /title/utils/lists`** — Returns predefined title lists.

## Request and Response Format

**Request Example:**

```http
GET /titles?limit=5&genre=Action&year=2020
```

**Response Example:**

```json
{
  "results": [
    {
      "id": "tt1234567",
      "titleText": "Sample Movie",
      "primaryImage": {...},
      "titleType": {...},
      "releaseDate": "2020-07-15",
      "genres": {...},
      "ratingsSummary": {...}
    }
  ],
  "page": 1,
  "next": 2,
  "entries": 100
}
```

* **`results`** — Array of title/actor objects
* **Pagination keys**: `page`, `next`, `entries` appear for paged endpoints
* Data models include **title**, **actor**, **rating**, **light episode**

## Authentication

* The documentation does not specify authentication; verify if an **API key** or other method is needed from the provider before use.

## Error Handling

* On failed requests, the API may return HTTP error codes (e.g., 400 for bad request, 404 for not found, 500 for server errors).
* Always check `status` and handle gracefully in your code.

## Usage Limits and Best Practices

* No explicit rate limits in the documentation — check provider policies.
* Use **`limit`** and **`page`** to manage large datasets.
* Use `info` parameter to request only the needed fields to improve performance.
* Avoid hardcoding endpoints — store them in configuration files.


