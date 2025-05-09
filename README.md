﻿
# Google Maps AI Agent with Model Content Protocol (MCP)

This project demonstrates the integration of Google Maps APIs with GitHub Copilot using Model Content Protocol (MCP) inside Visual Studio Code. The goal is to enable AI-assisted development that can interact with real-world APIs directly from the editor.

## What is Model Content Protocol (MCP)?

Model Content Protocol (MCP) is an open standard that enables AI models to dynamically interact with external APIs, tools, and services. Instead of only generating text or code from static training data, MCP allows models like GitHub Copilot to:

- Discover and list available tools
- Understand tool capabilities through metadata
- Execute function calls in real time
- Retrieve structured outputs for better responses

MCP turns an AI model into an intelligent agent capable of performing API-based operations, making it far more interactive and useful in development environments.

## Project Features

In this setup, we enable GitHub Copilot to interact with the Google Maps API using MCP, allowing it to call geolocation-related tools directly from the VS Code environment.

The following Google Maps tools are supported:

- `maps_geocode`: Convert addresses into geographic coordinates
- `maps_reverse_geocode`: Convert geographic coordinates into a human-readable address
- `maps_place_details`: Retrieve detailed information about a place
- `maps_distance_matrix`: Calculate distances and durations between multiple origin-destination pairs
- `maps_directions`: Get turn-by-turn directions between two locations
- `maps_search_places`: Search for nearby places using Google Places API
- `maps_elevation`: Retrieve elevation data for specific locations

## MCP Configuration

The `.vscode/mcp.json` file is used to register the Google Maps toolset with the MCP server. This enables Copilot to interact with these tools inside the editor.

### Example `.vscode/mcp.json`:

```json
{
  "inputs": [],
  "servers": {
    "google-maps": {
      "command": "npx",
      "args": [
        "@modelcontextprotocol/server-google-maps"
      ],
      "env": {
        "GOOGLE_MAPS_API_KEY": "YOUR_API_KEY"
      }
    }
  }
}
```

### Configuration Breakdown:

- **`inputs`**: Left empty in this case. It can be used to define shared parameters.
- **`servers`**: Describes tool servers exposed to the model.
- **`google-maps`**: The name identifier for this server.
- **`command`**: The tool is launched using `npx`, a Node.js command runner.
- **`args`**: Specifies the MCP-compatible server package: `@modelcontextprotocol/server-google-maps`.
- **`env`**: Environment variables such as your actual `GOOGLE_MAPS_API_KEY` are passed here.

> Make sure to replace `"YOUR_API_KEY"` with your valid API key from the Google Cloud Console.

## Example 
![image](https://github.com/user-attachments/assets/99e664de-a6fb-48e8-b1eb-a29332e98aac)


## Use Cases

- Automating location-based features in software projects
- Building smart travel apps with natural language prompts
- Generating route information and address data using AI
- Geospatial reasoning and query automation for logistics and maps-based services

## Why MCP is a Game-Changer

- **Real-time Tool Access**: Models are no longer limited to training data; they can interact with real-world APIs during execution.
- **Better Development Experience**: Copilot becomes more than a code suggestion tool—it acts like an AI assistant that can run and test tool integrations.
- **Context Awareness**: MCP allows models to use the developer’s current file, context, and environment for more relevant suggestions.
- **Plug-and-Play Tools**: Developers can register custom tools via MCP and let the AI model use them without retraining or extension-specific logic.

## Getting Started

1. Clone this repository.
2. Install Node.js (if not already installed).
3. Set up your Google Maps API key via Google Cloud Console.
4. Create a `.vscode/mcp.json` file as shown above.
5. Open the project in VS Code.
6. Enable MCP integration via the Copilot Labs extension.
7. Select and activate the Google Maps tools from the Copilot side panel.

## License

This project is released under the MIT License.
