**The aim:**
- Install an LLM locally
- Use the model for chats
- Use the model for code completion

Compose file sets up Ollama and WebUI containers. From there install whatever model you prefer. The example shows installing Llama3.1 7B. 

```
docker exec -it ollama ollama pull llama3.1
```

For VS Code integration, ***install Continue extension*.**

Modify the extensions config:

```
...

  "allowAnonymousTelemetry": false,
  "models": [
    {
    "apiBase": "http://localhost:11434/",
      "model": "codellama:7b",
      "provider": "ollama",
      "title": "codellama 7B"
    }
  ],
  
  ...
  
  "tabAutocompleteModel": {
    "title": "codellama:7b",
    "provider": "ollama",
    "model": "codellama 7b",
    "apiBase": "http://localhost:11434/"
  }
...
```