SKETCHUP + CLAUDE CONNECTOR SETUP
=================================

PART A - SketchUp side
1. Close SketchUp.
2. Copy su_mcp.rb and the su_mcp folder into your SketchUp Plugins folder:
   %APPDATA%\SketchUp\SketchUp 2026\SketchUp\Plugins
   (Or install su_mcp.rbz from SketchUp: Extensions > Extension Manager >
    Install Extension.)
3. Start SketchUp again.
4. Go to Extensions > MCP Server > Start Server.
   (Do this every time you open SketchUp.)

PART B - Claude Desktop side
1. Install Claude Desktop and sign in.
2. Install uv (open Command Prompt and run):
   winget install --id=astral-sh.uv -e
   Then close and reopen Command Prompt and check: uvx --version
3. Open Claude Desktop > Settings > Developer > Edit Config.
4. Put this in claude_desktop_config.json and save:

{
  "mcpServers": {
    "sketchup": {
      "command": "uvx",
      "args": ["--with", "mcp==1.12.2", "sketchup-mcp"]
    }
  }
}

   If the file already has other content, only add the "sketchup" part
   inside "mcpServers" and keep the rest.
   If "uvx" is not found, run: where uvx
   and paste the full path in "command" (use \\ instead of \).
5. Fully close and reopen Claude Desktop (also quit from the system tray).

PART C - Test
1. Make sure SketchUp is open and the server is started.
2. In Claude, type: Create a 1m cube in SketchUp

NOTES
- The server only listens on localhost (port 9876).
- If it fails, check that Start Server was clicked and restart Claude Desktop.
- Do not share API keys or passwords in this repository.