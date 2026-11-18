# MCP details

## Resourses

A resourse should just provide information like manuals or user info. Its goal is to provide information rather than do an action itself.

Tools and Resources has no distiction each other, they just work to label the purpose of a mcp functionality. There is where confusion came on its use. To me they are like REST verbs: they describe the purpose of an endpoint like POST to create a new registry, GET to ask for information, PATCH to update a registry field, etc

## Resource templates

Allows to retreive a resource dinamically via parameters on a resource URI like: "docs://setup-manual/{version}". It is a good practise to add all valid URIs on documentation to help LLM to identify what can accept or not.

```python
@mcp.resource("docs://setup-manual/{version}")
def get_setup_manual(version: str = "latest") -> str:
    pass
```

Could do this resource be a tool? Sure, but a tool do an action rather than a resource which retreive read only data.

## How an LLM invoke a resource?

Internally some LLMs do not know what are resources and prompts, so they are encapsulated and handled as tools. When LLM ask for all tools available in a MCP server resources and prompts are passed as tools, but when a LLM as for a tool-resource client app recognize this as a resource and know what to call.

## Prompts

A MCP Server can return Prompts to target an specific task. Here more info:

[Prompts lecture](https://www.udemy.com/course/curso-completo-de-model-context-protocol-mcp-aplicado-a-ia/learn/lecture/52883379)
