# mcp-demo-products-api

Simple Node.js/Express Products API with in-memory storage.

## Setup

### Prerequisites
- Node.js 18+ (or current LTS)
- npm

### Install dependencies
```bash
npm install
```

## Run Commands

### Start (production mode)
```bash
npm start
```

### Start (development with auto-reload)
```bash
npm run dev
```

By default, the API runs at:
- `http://localhost:3000`

Quick health check:

PowerShell:
```powershell
Invoke-WebRequest -Uri http://localhost:3000/health
```

or:
```powershell
curl.exe -s http://localhost:3000/health
```

## Endpoints

Base URL: `http://localhost:3000`

### Health
- `GET /health`
- Response: `200 { "status": "ok" }`

### Products

#### List products
- `GET /products`
- Optional query parameter: `?limit=2` to limit the number of results.

#### Get product by id
- `GET /products/:id`
- `404` if not found

#### Create product
- `POST /products`
- Body (JSON):
```json
{
	"name": "Mouse",
	"price": 19.99
}
```
- Validation rules:
	- `name` must be a string with at least 2 characters
	- `price` must be a number greater than 0
- `400` on validation failure

#### Update product
- `PUT /products/:id`
- Body (JSON): same shape/validation as create
- `404` if not found
- `400` on validation failure

#### Delete product
- `DELETE /products/:id`
- Returns `204` on success
- `404` if not found

## Testing

Run all tests:
```bash
npm test
```

Test suites included:
- Unit tests: product validation model (`tests/unit`)
- Integration tests: API CRUD flow and validation (`tests/integration`)
