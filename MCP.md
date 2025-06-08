
Topic MCP Model Context Protocol
So MCP in this the full form this is Model Context Protocol. The model means basically the LLM we are using. Context is some external information we are feeding to the LLM and protocol are the general rules to be followed. So this idea is presented by the Anthropix which is the parent company of Clod. MCP follows HTTP, TCP protocol and so now let's just mention what why we use this. So context for LLM is important to work. Training is highly costly and computational required and training frequency is too high for LLMs. So content and LLMs also have a smaller context window, limited context window. Then the challenge is how to efficiently and structurally give context of the updated content and information to the LLM. So we use MCP and MCP is like the USB C port if we give the analogy for it. So it is like the USB C port for AI. MCP provides standard ways to connect to different data sources and tools for LLM. So it is like we have a host client with MCP client. So we have basically the user is with the MCP client. It is paired with many MCP server. Each MCP server connects to an external service maybe like a Google search or YouTube feed or some database local storage. So link between external and world and AI is MCP is the main idea of MCP to feed the context. MCP uses the standard input output. So it is like how we talk in the terminal using the echo command. So what happens is there is the cycle is like AI, MCP and API. MCP is bridge between AI and real-time data in the external world. Same MCP server can be used in the cross models or cross IDE. So initially MCP was built with the standard input output STDIO.


Client-Side (MCP Pad):
→ Could be IDEs or tools like Claude, ChatGPT, etc.
→ Handles I/O, manages flows, and connects AI to context.

Server-Side (MCP Server):
→ Lightweight and shell-based (SH server).
→ Runs task-specific programs for AI to access.
→ Pulls data from:
 → Local Databases.
 → Remote APIs (e.g., Google Drive, external APIs).

→ MCP Can:
 → Generate prompts, route API responses, manage AI resources.
 → Build reusable prompt templates and workflows.

The standard input-output won't work when we deploy the MCPU on the cloud. Hence, we use SSE transport, the server-sent event transport protocol, to work with MCPU on the cloud.