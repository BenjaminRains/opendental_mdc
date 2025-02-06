## DBeaver Data Security Note

DBeaver's handling of exported data:

1. **Temporary Storage**
   - No permanent storage of queried data
   - Creates temporary files only during active operations
   - Location: `C:\Users\[username]\AppData\Local\Temp\dbeaver-temp\`
   - Directory and files are automatically deleted after operations complete

2. **Verification Process**
   ```powershell
   # Check for temporary files during active exports
   Get-ChildItem "$env:TEMP\dbeaver-temp\"
   ```
   - Directory only exists during active file operations
   - Clean filesystem when DBeaver is not performing exports

3. **Security Implications**
   - Data is not cached between sessions
   - Temporary files are properly cleaned up
   - Only exported files remain in user-specified locations 