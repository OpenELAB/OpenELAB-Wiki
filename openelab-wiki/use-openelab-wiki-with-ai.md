---
description: >-
  Give your AI agent access to OpenELAB product guides, wiring instructions, and
  troubleshooting steps with MCP.
---

# Use OpenELAB Wiki with AI

<figure><img src=".gitbook/assets/openelab-mcp-clients.svg" alt="Supported MCP clients: Codex, Claude Code, and Cursor"><figcaption></figcaption></figure>

### Quick setup

Choose your client below. No OpenELAB account or API key is required.

{% tabs %}
{% tab title="Codex CLI" %}
Run this in your terminal.

```
codex mcp add openelab-wiki --url https://wiki.openelab.io/~gitbook/mcp
```

Start a new Codex session before testing. If Codex suggests logging in, try the test first. This public server requires no MCP login.
{% endtab %}

{% tab title="Claude Code" %}


Run this in your terminal, then test in Claude Code.

```
claude mcp add --transport http openelab-wiki https://wiki.openelab.io/~gitbook/mcp
```
{% endtab %}

{% tab title="Cursor" %}


Add this entry in Cursor MCP settings or in your `.cursor/mcp.json` file. If the file already has an `mcpServers` object, add the entry inside it.

```
{
  "mcpServers": {
    "openelab-wiki": {
      "url": "https://wiki.openelab.io/~gitbook/mcp"
    }
  }
}
```
{% endtab %}
{% endtabs %}

### Test your connection

```
Use OpenELAB Wiki MCP to find which camera and USB-to-serial adapter come with the ESP32-CAM Camera Module. Include the original Wiki link.
```

A successful answer should name the OV2640 camera and the ESP32-CAM-MB USB-to-serial adapter and link to the [ESP32-CAM Camera Module guide](https://wiki.openelab.io/aiot/openelab/esp32-cam-camera-module).

### Using another AI client?

Copy this prompt into your agent. If it cannot configure MCP from chat, use your client’s MCP settings or setup command.

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

### Public MCP endpoint

Use Streamable HTTP, server name `openelab-wiki`, and no authentication.

```
https://wiki.openelab.io/~gitbook/mcp
```

The MCP server searches and reads published OpenELAB Wiki documentation. Use it to check hardware compatibility, find wiring and setup steps, or troubleshoot a project. [GitBook setup guide](https://gitbook.com/docs/ai-for-your-readers/mcp-servers-for-published-docs#connect-an-ai-tool) · [Explore the OpenELAB Wiki](https://wiki.openelab.io/)
