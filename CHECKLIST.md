# MCP Registry Publishing Checklist

## Pre-Publishing Setup

- [ ] Create PyPI account at https://pypi.org/account/register/
- [ ] Create GitHub account (if you don't have one)
- [ ] Create GitHub repository named `word-mcp-server`

## Update Configuration Files

- [ ] Update `setup.py`:
  - [ ] Replace "Your Name" with your actual name
  - [ ] Replace "your.email@example.com" with your email
  - [ ] Replace "yourusername" with your GitHub username

- [ ] Update `pyproject.toml`:
  - [ ] Replace "Your Name" with your actual name
  - [ ] Replace "your.email@example.com" with your email
  - [ ] Replace "yourusername" with your GitHub username

- [ ] Update `README.md`:
  - [ ] Replace "yourusername" in the mcp-name comment

- [ ] Update `server.json`:
  - [ ] Replace "yourusername" in the name field
  - [ ] Replace "yourusername" in the repository URL

- [ ] Update `LICENSE`:
  - [ ] Replace "[Your Name]" with your actual name

## Publish to GitHub

- [ ] Initialize git repository
- [ ] Add all files to git
- [ ] Commit changes
- [ ] Add GitHub remote
- [ ] Push to GitHub

## Publish to PyPI

- [ ] Install build tools: `pip install build twine`
- [ ] Build package: `python -m build`
- [ ] Upload to PyPI: `python -m twine upload dist/*`
- [ ] Verify at https://pypi.org/project/word-mcp-server/

## Publish to MCP Registry

- [ ] Install mcp-publisher CLI tool
- [ ] Verify installation: `mcp-publisher --help`
- [ ] Authenticate: `mcp-publisher login github`
- [ ] Publish: `mcp-publisher publish`
- [ ] Verify publication with curl command

## Post-Publishing

- [ ] Test installation: `pip install word-mcp-server`
- [ ] Test the server works correctly
- [ ] Share your server with the community
- [ ] Consider adding to your GitHub profile README

## Notes

Write any issues or observations here:
