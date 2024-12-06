# envbuilder

**envbuilder** is a tool to securely and automatically generate `.env` files from an `envinfo.json` file, allowing you to share the .env by keeping certain information private to you only, and making other information public, at your discretion. With integrity verification, it ensures the accuracy and safety of your environment variables by preventing unauthorized modifications.

## Use

To use the tools, use the following commands:


### To build a `.env` from a `envinfo.json`
```bash
  npx envbuilder build
```

### To build a `envinfo.json` from a `.env`
```bash
  npx envbuilder create
```

### To check the integrity of the `.env` file against the data in `envfile.json`
```bash
  npx envbuilder integrity
```
## Structure of `envinfo.json`

The `envinfo.json` file contains the following information to generate an `.env` file:

- `name`: The name of the env attribute.
- `description`: The description of the env attribute.
- `defaultValue`: The default value that the attribute must share (e.g. a token that all developers in a project must have).
## Examples

Suppose you want to share a template of your `.env`, but without sharing the values ​​of certain env attributes. You could make an `envinfo.json` structure like this:

### To check the integrity of the `.env` file against the data in `envfile.json`
```json
  {
    "dataenv": [
        {
            "name": "TOKEN",
            "description": "Your token 1",
            "defaultValue": "hello"
        },
        {
            "name": "TOKEN2",
            "description": "Your token 2",
            "defaultValue": ""
        },
        {
            "name": "TOKEN3",
            "description": "Your token 3",
            "defaultValue": ""
        }
    ]
}
```

After running the command to build it, you would have a .env like this:
```env
# Your bot token
TOKEN=hello

# Your bot token
TOKEN2=

# Your bot token
TOKEN3=
```

**The key point of the system is to share the .env file in projects.**
## Authors

- [@MrTigerST](https://www.github.com/MrTigerST)