# MCP Demo Project

This project demonstrates the implementation of Model Context Protocol (MCP) servers using two different approaches:
1. Standard I/O (stdio) based server in `/weather-mcp`
2. Server-Sent Events (SSE) REST API based server in `/weather-mcp-sse`

Both implementations provide weather-related tools that can be integrated with Cursor IDE.

## Features

- Get weather alerts for a specific US state
- Get weather forecasts for any US location using latitude/longitude coordinates

## Project Structure

```
mcp-demo/
├── weather-mcp/        # stdio-based MCP server
│   └── src/
│       └── index.ts    # Main server implementation
└── weather-mcp-sse/    # SSE-based MCP server
    └── src/
        └── index.ts    # Main server implementation
```

## Setup Instructions

### 1. Install Dependencies

For each implementation (`weather-mcp` and `weather-mcp-sse`), run:

```bash
cd weather-mcp    # or cd weather-mcp-sse
npm install
```

### 2. Build and Run

For development, run TypeScript in watch mode:
```bash
npm run tsc -- -w
```

In a separate terminal, start the server:
```bash
node dist/index.js
```

## Configuring MCP in Cursor

To use these MCPs in Cursor:

1. Open Cursor IDE
2. Navigate to File > Preferences > Cursor Settings
3. Scroll to the MCPs section
4. Click "Add MCP"
5. Configure based on your chosen implementation:

### For stdio-based MCP:
- Name: Weather MCP
- Transport: stdio
- Command: `node /path/to/mcp-demo/weather-mcp/dist/index.js`

### For SSE-based MCP:
- Name: Weather MCP SSE
- Transport: sse
- URL: `http://localhost:3000`

## Usage Examples

Once configured, you can simply ask the Cursor Agents about weather in a particular area and it will invoke the MCP calls.

## MCP Endpoint Details

### get-alerts
- Parameter: `state` (two-letter state code, e.g., "CA", "NY")
- Returns: Active weather alerts for the specified state

### get-forecast
- Parameters: 
  - `latitude` (between -90 and 90)
  - `longitude` (between -180 and 180)
- Returns: Detailed weather forecast for the specified location

## Notes

- The weather data is sourced from the National Weather Service (NWS) API
- Only US locations are supported for forecasts
- The SSE implementation requires the server to be running locally on port 3000

## Contributing

This is a proof of concept and is not intended for production use. This repository is for educational purposes and will not be maintained. Please feel free to fork and maintain your own version!

## License

MIT License - feel free to use this code for your own projects!