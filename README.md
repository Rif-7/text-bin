# TextBin

TextBin is a web application written in Go for sharing and managing text snippets. Users can view public snippets, create new ones after logging in, and set expiration times for their snippets.

## Features

- **View Snippets:** Home page displays the latest 10 snippets.
- **Create Snippets:** Authenticated users can create new snippets.
- **Snippet Expiry:** Set snippet expiration to one day, one week, or one year.
- **User Authentication:** Session-based login system.
- **Update Password:** Users can update their password after logging in.
- **HTTPS Support:** Runs as an HTTPS server using provided certificate and key files.
- **Template Caching:** Caches HTML templates for performance.
- **Embedded Assets:** Uses Go’s `embed` package to bundle static files and templates into the binary.
- **Debug Mode:** Optional debug mode for detailed error messages.
- **Testing:** Includes tests for handlers, middleware, and templates. Database operations are mocked for testing.

## Technologies Used

- Go standard `net/http` library
- Go `embed` package
- Session management
- HTTPS with TLS certificates

## Getting Started

### Prerequisites

- Go 1.24 or newer
- MySQL (for production use)
- TLS certificate and key files

### Running the Application

1. Clone the repository:
    ```sh
    git clone https://github.com/Rif-7/text-bin.git
    cd text-bin
    ```

2. Make sure you have TLS certificate and key files at `./tls/cert.pem` and `./tls/key.pem`.  
   You can generate self-signed certificates for development with:
    ```sh
    mkdir -p tls
    openssl req -x509 -newkey rsa:4096 -keyout tls/key.pem -out tls/cert.pem -days 365 -nodes -subj "/CN=localhost"
    ```

3. Build and run:
    ```sh
    make run
    ```

4. Visit [https://localhost:4000](https://localhost:4000) in your browser.
### Running Tests

```sh
make test
```

## Project Structure

- `cmd/web/` – Main application entry point, handlers, routes, middleware
- `internal/models/` – Database models and mocks for testing
- `internal/assert/` – Test helpers
- `internal/validator/` – Form validation logic
- `ui/` – Embedded static assets and HTML templates
- `tls/` – TLS certificate and key files

## License

MIT License

---

*This project is for educational purposes and demonstrates secure session management, template caching, and Go web development best practices.*