# Details

## Installs

`uv pip install "mcp[cli]"` to interact with MCP servers via CLI with `mcp`

and

`uv pip install fastmcp` which is the SDK to create a new MCP server

## For testing
First enter to directory `3.first-mcp-server``

For a local MCP server run `fastmcp dev inspector mcp_server.py`

For other MCP server use `npx @modelcontextprotocol/inspector`. Example: `npx @modelcontextprotocol/inspector uvx --with "mcp<2" mcp-server-sqlite --db-path ./videojuegos.db`.

Consider putting double quotes to mcp<2 in UI to prevent errors on connection

When using HTTP transport you can just run `npx @modelcontextprotocol/inspector` and fill form using Transport Type as Streamable HTTP and a URL like `http://127.0.0.1:8000/mcp`

**Quite important**: you need to change transport on run method call `mcp.run(transport="http")"`

## How to integarte with MCP client? (Claude desktop)

Create a pyproject.toml like this as example:

```toml
[project]
name = "mcp-server-videogames-store"
version = "0.1.0"
dependencies = [
    "fastmcp",
]

[project.scripts]
mcp-server = "mcp_server.py:main"
```

And add it to MCP Client configuration (claude desktop for this example):

```json
{
    "mcpServers": {
        "database-videogames-store": {
            "command": "uv",
            "args": [
            "--directory",
            "/Users/manuelcarbajal/Developer/courses/mcp-udemy-course/3.first-mcp-server",
            "run",
            "mcp_server.py"
            ]
        }
    }
}
```

`--directory` argument tells where our pyproject.tml is to be able to run the mcp server
