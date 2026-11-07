# BDF Lab 3 – Book Management REST API

## Student Details

- **Student Name:** Jahnavi
- **Roll Number:** 252U1R5056
- **Course:** Backend Development Fundamentals (BDF)
- **Lab:** Lab 3
- **Faculty:** Sai Shiva Teja Sir

## Aim

To develop a REST API using Node.js, Express.js, and SQLite. The API supports book management operations (CRUD), searching, sorting, pagination, price filtering, input validation, suitable HTTP status codes, and error handling.

## Technologies Used

- Node.js and Express.js
- SQLite and sqlite3
- JavaScript
- npm and Nodemon
- Postman for API testing
- Git and GitHub for version control

## Project Structure

```text
252U1R5056_Jahnavi_BDF_Lab_3/
├── screenshots/
│   └── README.md
├── .gitignore
├── POSTMAN_TEST_CASES.md
├── README.md
├── books.db
├── database.js
├── package.json
├── package-lock.json
└── server.js
```

## Setup and Execution

1. Install Node.js (Node.js 22 or a compatible supported version) and npm.
2. Open this project folder in VS Code.
3. Install dependencies:

   ```bash
   npm install
   ```

4. Start the server:

   ```bash
   npm start
   ```

5. For development with automatic restart, use:

   ```bash
   npm run dev
   ```

The server runs at **http://localhost:3001** by default. You can change the port using the `PORT` environment variable.

## Database Design

- **Database file:** `books.db`
- **Table:** `books`

| Column | Data type | Constraint / purpose |
|---|---|---|
| id | INTEGER | Primary key, auto-increment |
| title | TEXT | Required book title |
| author | TEXT | Required author name |
| price | REAL | Required non-negative price |

The database and table are initialized automatically when the application starts. Ten sample book records are inserted if they do not already exist.

## API Endpoints

| Method | Endpoint | Purpose | Success status |
|---|---|---|---|
| GET | `/` | Check whether the API is running | 200 |
| GET | `/books` | List books with search, sorting, filters, and pagination | 200 |
| GET | `/books/:id` | Get one book by ID | 200 |
| POST | `/books` | Add a new book | 201 |
| PUT | `/books/:id` | Update an existing book | 200 |
| DELETE | `/books/:id` | Delete a book | 200 |

Unknown endpoints and missing book IDs return 404. Invalid input returns 400.

## Query Parameters for GET /books

- `search_q` – search for part of a book title.
- `order_by` – sort by `id`, `title`, `author`, or `price`.
- `order` – sorting direction: `ASC` or `DESC`.
- `limit` – number of records to return (1–100).
- `offset` – number of records to skip.
- `min_price` – minimum book price.
- `max_price` – maximum book price.

Example:

```text
http://localhost:3001/books?search_q=Atomic&order_by=price&order=DESC&limit=5&offset=0
```

## Example POST Request Body

Choose **Body → raw → JSON** in Postman and use:

```json
{
  "title": "Database Management Systems",
  "author": "Jahnavi",
  "price": 599
}
```

## SQL Operations Used

- `SELECT` retrieves book records.
- `INSERT` adds a book.
- `UPDATE` changes a book.
- `DELETE` removes a book.
- `WHERE` and `LIKE` support filtering and searching.
- `ORDER BY` sorts results.
- `LIMIT` and `OFFSET` support pagination.

Parameterized SQL queries (`?` placeholders) are used for user-provided values. Sorting columns are restricted to an allowed list.

## Validation and HTTP Status Codes

- **200 OK:** Request completed successfully.
- **201 Created:** A book was added successfully.
- **400 Bad Request:** Required fields are missing or values are invalid.
- **404 Not Found:** The requested book or API endpoint does not exist.
- **500 Internal Server Error:** An unexpected server error occurred.

The title and author must be non-empty strings. Price must be a valid, non-negative number.

## Testing

Use the test cases in `POSTMAN_TEST_CASES.md` to verify GET, POST, PUT, DELETE, validation, and error responses. Capture fresh screenshots of your own test runs and save them in the `screenshots/` folder. The starter screenshots from the previous student's project have intentionally not been included.

## Result

A Book Management REST API was implemented using Node.js, Express.js, and SQLite. It supports CRUD operations, search, sorting, pagination, price filtering, input validation, and appropriate HTTP status codes.

## Conclusion

Through this lab, I learned how to create REST API routes using Express.js, connect an application to an SQLite database, perform SQL CRUD operations, handle query parameters, validate user input, and test API responses using Postman.

---

**Developed by Jahnavi | Roll Number: 252U1R5056**
