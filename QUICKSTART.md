# Word MCP Server - Quick Start

## ✅ Installation Complete

Your Word MCP server is installed and configured at:
- **Location**: `~/word-mcp-server/`
- **Python**: Python 3.12 virtual environment
- **Status**: Ready to use with Kiro CLI

## 🚀 Usage

Restart Kiro CLI to load the new MCP server, then use natural language:

### Read a Document
```
Read the Word document at ~/Documents/report.docx
```

### Create a Document
```
Create a Word document at ~/Documents/memo.docx with:
Title: Meeting Notes
Date: February 6, 2026

Attendees:
- Alice
- Bob

Discussion:
We reviewed the Q1 goals and agreed on next steps.
```

### Append to a Document
```
Add the following to ~/Documents/memo.docx:

Action Items:
- Review budget by Friday
- Schedule follow-up meeting
```

## 🔧 Available Tools

1. **read_word_document** - Extract text from .docx files
2. **create_word_document** - Create new Word documents
3. **append_to_document** - Add content to existing documents

## 📝 Notes

- All file paths should be absolute (e.g., `/Users/swadeg/Documents/file.docx`)
- The server uses python-docx library (cross-platform, no Microsoft Office required)
- Documents are created in standard .docx format compatible with Microsoft Word

## 🧪 Test

A test document was created at `/tmp/test_word_mcp.docx` to verify functionality.

## 🔄 Restart Kiro

To use the new MCP server:
```bash
# Exit current Kiro session and restart
kiro-cli chat
```

The word-mcp tools will now be available!
