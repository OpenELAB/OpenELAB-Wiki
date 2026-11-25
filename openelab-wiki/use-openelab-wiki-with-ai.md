---
description: >-
  Search product guides, setup instructions, and troubleshooting references from
  your AI tools.
---

# Use OpenELAB Wiki with AI

Connect OpenELAB Wiki to your AI assistant or coding agent with Model Context Protocol (MCP). Your agent can search our public product guides, tutorials, and engineering references, read the matching page, and link you back to the source.

Use it to check hardware compatibility, find wiring and setup steps, or troubleshoot robotics, AIoT, ESP32, and embedded projects from your development tools.

### Connect your AI agent

Copy the setup prompt below and paste it into an MCP-compatible assistant. The public server uses Streamable HTTP. No OpenELAB account, API key, or self-hosting is required.

```
Connect to OpenELAB Wiki MCP

Register the public MCP server below in your client. Use it as a technical reference when helping me with OpenELAB hardware, robotics, AIoT, or embedded development.

Server name: openelab-wiki
URL: https://wiki.openelab.io/~gitbook/mcp
Transport: Streamable HTTP
Authentication: None
Documentation: https://wiki.openelab.io/

After connecting, initialize MCP and list the available tools. Use searchDocumentation to find the ESP32-CAM Camera Module, then use getPage to load the matching OpenELAB Wiki article. Check which camera and USB-to-serial adapter are included, cite the original Wiki page, and confirm whether the connection works.

When I ask relevant technical questions, search the Wiki, retrieve the matching page, and link to the original source. If the Wiki does not answer the question, tell me what is missing. Do not submit feedback through sendFeedback unless I explicitly ask.

If you cannot configure the server, give me the exact manual steps for my client.
```

### Set up manually

In a client that supports remote MCP, add a server named `openelab-wiki` with this endpoint:

```
https://wiki.openelab.io/~gitbook/mcp
```

See the [GitBook setup guide](https://gitbook.com/docs/ai-for-your-readers/mcp-servers-for-published-docs#connect-an-ai-tool) for Claude Code, Cursor, Codex, and other clients. The endpoint is for your MCP client.

### Try it with ESP32-CAM

> Use OpenELAB Wiki MCP to find which camera and USB-to-serial adapter come with the ESP32-CAM Camera Module. Include the original Wiki link.

Check the answer against the [ESP32-CAM Camera Module guide](https://wiki.openelab.io/aiot/openelab/esp32-cam-camera-module), or [explore the OpenELAB Wiki](https://wiki.openelab.io/).
