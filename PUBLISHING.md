# Publishing word-mcp-server to MCP Registry

This guide walks you through publishing your word-mcp-server to the MCP Registry.

## Prerequisites

Before you begin, you need:

1. **PyPI Account**: Create one at https://pypi.org/account/register/
2. **GitHub Account**: For authentication with MCP Registry
3. **GitHub Repository**: Create a repository for your server (e.g., `word-mcp-server`)

## Step 1: Update Your Information

Replace the placeholder information in these files:

### setup.py
- Replace `Your Name` with your actual name
- Replace `your.email@example.com` with your email
- Replace `yourusername` with your GitHub username

### pyproject.toml
- Replace `Your Name` with your actual name
- Replace `your.email@example.com` with your email
- Replace `yourusername` with your GitHub username

### README.md
- Replace `yourusername` in the mcp-name comment with your GitHub username
  - The line should be: `<!-- mcp-name: io.github.YOURUSERNAME/word-mcp -->`

### server.json
- Replace `yourusername` with your GitHub username in:
  - `"name": "io.github.YOURUSERNAME/word-mcp"`
  - `"repository.url": "https://github.com/YOURUSERNAME/word-mcp-server"`

## Step 2: Create GitHub Repository

1. Go to https://github.com/new
2. Create a repository named `word-mcp-server`
3. Don't initialize with README (we already have one)
4. Push your code:

```bash
cd ~/word-mcp-server
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOURUSERNAME/word-mcp-server.git
git push -u origin main
```

## Step 3: Publish to PyPI

### Install build tools
```bash
cd ~/word-mcp-server
pip install build twine
```

### Build the package
```bash
python -m build
```

This creates files in the `dist/` directory.

### Upload to PyPI
```bash
# First time: authenticate
python -m twine upload dist/*
```

You'll be prompted for your PyPI username and password.

### Verify publication
Visit: https://pypi.org/project/word-mcp-server/

## Step 4: Install mcp-publisher

### macOS/Linux
```bash
curl -L "https://github.com/modelcontextprotocol/registry/releases/latest/download/mcp-publisher_$(uname -s | tr '[:upper:]' '[:lower:]')_$(uname -m | sed 's/x86_64/amd64/;s/aarch64/arm64/').tar.gz" | tar xz mcp-publisher && sudo mv mcp-publisher /usr/local/bin/
```

### Verify installation
```bash
mcp-publisher --help
```

## Step 5: Authenticate with MCP Registry

```bash
cd ~/word-mcp-server
mcp-publisher login github
```

Follow the prompts:
1. Visit the GitHub device authorization URL
2. Enter the code shown in your terminal
3. Authorize the application

## Step 6: Publish to MCP Registry

```bash
cd ~/word-mcp-server
mcp-publisher publish
```

You should see:
```
Publishing to https://registry.modelcontextprotocol.io...
✓ Successfully published
✓ Server io.github.YOURUSERNAME/word-mcp version 1.0.0
```

## Step 7: Verify Publication

Search for your server:
```bash
curl "https://registry.modelcontextprotocol.io/v0.1/servers?search=io.github.YOURUSERNAME/word-mcp"
```

## Troubleshooting

### "Registry validation failed for package"
- Ensure the `mcp-name` in README.md matches the `name` in server.json
- The format must be: `<!-- mcp-name: io.github.YOURUSERNAME/word-mcp -->`

### "Invalid or expired Registry JWT token"
- Re-authenticate: `mcp-publisher login github`

### "You do not have permission to publish this server"
- Your server name must start with `io.github.YOURUSERNAME/` when using GitHub auth
- Replace YOURUSERNAME with your actual GitHub username

### PyPI upload fails
- Make sure you're registered at https://pypi.org
- Consider using an API token instead of password (more secure)
- Create token at: https://pypi.org/manage/account/token/

## Updating Your Server

When you make changes:

1. Update version in `setup.py`, `pyproject.toml`, and `server.json`
2. Rebuild and republish to PyPI:
   ```bash
   python -m build
   python -m twine upload dist/*
   ```
3. Update server.json with new version
4. Republish to MCP Registry:
   ```bash
   mcp-publisher publish
   ```

## Files Created

- `setup.py` - Python package setup (legacy format)
- `pyproject.toml` - Modern Python package configuration
- `server.json` - MCP Registry metadata
- `LICENSE` - MIT License
- `.gitignore` - Git ignore patterns
- `PUBLISHING.md` - This guide

## Next Steps

- Add more features to your server
- Write tests
- Add CI/CD with GitHub Actions
- Consider adding more documentation
- Share your server with the community!

## Resources

- MCP Registry Documentation: https://modelcontextprotocol.io/registry/about
- PyPI Publishing Guide: https://packaging.python.org/tutorials/packaging-projects/
- MCP Specification: https://modelcontextprotocol.io/specification/
