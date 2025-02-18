# Understanding Carriage Return

## Definition

A carriage return (CR) is a control character (ASCII 13, \r) that moves the cursor to the beginning of the current line.

## Historical Context

The term comes from typewriters, where the "carriage" was the mechanism that held the paper and the "return" moved it back to the start position.

## Different Line Endings

1. **Windows (CRLF)**: Uses both `\r\n`

   - Carriage Return + Line Feed
   - Represented as `\r\n`

2. **Unix/Linux (LF)**: Uses just `\n`

   - Line Feed only
   - Represented as `\n`

3. **Classic Mac (CR)**: Uses just `\r`
   - Carriage Return only
   - Represented as `\r`

## Common Issues

- Git repositories may have mixed line endings
- Text files may display incorrectly when moved between operating systems
- Scripts may fail if they have wrong line endings

## Git Configuration

```bash
# Configure Git to handle line endings automatically
git config --global core.autocrlf true  # For Windows
git config --global core.autocrlf input # For Linux/Mac
```
