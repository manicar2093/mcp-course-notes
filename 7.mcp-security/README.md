# MCP Security

## Generate RSA certificates

`fastmcp` library has auth providers as RSA generators that can be used to secure out server.

```python
from fastmcp.server.auth.providers.jwt import JWTVerifier, RSAKeyPair
```

This RSA key pair need to be protected; not stored in a plain text file rather in a database and ciphered.

[Security lecture](https://www.udemy.com/course/curso-completo-de-model-context-protocol-mcp-aplicado-a-ia/learn/lecture/52932151)
