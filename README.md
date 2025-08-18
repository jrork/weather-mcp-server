# Weather MCP Server

An MCP (Model Context Protocol) server that provides weather information using the National Weather Service API.

This project was created following the [MCP Server Quickstart Tutorial](https://modelcontextprotocol.io/quickstart/server) as a learning exercise.

## Features

This server provides two main tools:

- **get_alerts**: Get active weather alerts for any US state
- **get_forecast**: Get detailed weather forecasts for specific coordinates

## Installation

This project uses [uv](https://docs.astral.sh/uv/) for dependency management.

```bash
# Clone the repository
git clone <repository-url>
cd weather

# Install dependencies
uv sync

# Run the server
uv run python weather.py
```

## Usage

### Running as an MCP Server

The server communicates via stdio and can be integrated with MCP-compatible clients:

```bash
uv run python weather.py
```

### Available Tools

#### get_alerts

Get active weather alerts for a US state.

**Parameters:**
- `state` (string): Two-letter US state code (e.g., "CA", "NY", "TX")

**Example:**
```python
await get_alerts("CA")
```

#### get_forecast

Get a detailed weather forecast for specific coordinates.

**Parameters:**
- `latitude` (float): Latitude of the location
- `longitude` (float): Longitude of the location

**Example:**
```python
await get_forecast(37.7749, -122.4194)  # San Francisco coordinates
```

## Development

### Dependencies

- **httpx**: HTTP client for API requests
- **mcp**: Model Context Protocol framework
- **FastMCP**: Fast MCP server implementation

### API Usage

This server uses the National Weather Service API, which:
- Requires no API key
- Is free to use
- Covers locations within the United States
- Returns data in GeoJSON format

### Error Handling

The server includes robust error handling:
- Network timeouts (30 seconds)
- HTTP error responses
- Malformed API responses
- Missing location data

## License

[Add your license here]

## Contributing

[Add contributing guidelines here]