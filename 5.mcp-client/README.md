# Using our MCP with an LLM

## Share tools with an LLM

All LLMs accept a different format for tools, so you need to check how your model will take this info. In the case of this course where we use gpt-4o-mini the format will be something like this:

```python
{
    "type": "function",
    "function": {
        "name": "a name",
        "description: "a tool description",
        "parameters": "thi input schema"
    }
}
```

You must remind resources now are recognized as tools, so this process of format has to be done with resources and resources templates:


```python
# Resources mapping
{
    "type": "function",
    "function": {
        "name": func_name,
        "description": resource.description or resource.name,
        "parameters": {"type": "object", "properties": {}, "required": []}
    }
}
```

```python
# Resource template mapping
{
    "type": "function",
    "function": {
        "name": func_name,
        "description": template.description or template.name,
        "parameters": {
            "type": "object",
            "properties": properties,
            "requiered": params
        }
    }
}
```

A quick search on google should show how this resources should be formated for each LLM.
