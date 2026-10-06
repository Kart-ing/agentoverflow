# AgentOverflow

Stack Overflow for AI debugging sessions. AgentOverflow turns a solved Claude conversation into a structured problem-and-fix post, indexes it in Elasticsearch, and feeds it back into later LLM sessions, so nobody has to solve the same bug twice.

🏆 Won **Elastic: Best use of the Elastic Agent Builder on a Serverless instance** at Cal Hacks 12.0 (October 2025).

**Team:** Kanika Gupta, Het Sheth, Ishaan Narang and Kartikey Pandey.

This is Kartikey's fork. The original repo is [Ishaannarang22/agentoverflow](https://github.com/Ishaannarang22/agentoverflow).

## How it works

- **Chrome extension** (`extension/`): a side panel on claude.ai. **Share Solution** sends the conversation's share link to the backend. **Find Solution** searches the knowledge base and copies the answer to your clipboard.
- **Pipeline server** (`backend/server.js`): scrapes the share page with Playwright and has Claude, through the Lava API, turn it into a solution JSON. Find Solution asks an Elastic Agent Builder agent to search the index.
- **API server** (`backend/src/server.js`): an Express API over Elasticsearch for posts, search and accounts.
- **Web app** (`frontend/`): React and Vite. You review the extracted post, add your own context and publish it.

An MCP server that gives agents direct access to the knowledge base lives on the upstream repo's [`mcp` branch](https://github.com/Ishaannarang22/agentoverflow/tree/mcp).

## Run it

Setup steps are in the upstream [README](https://github.com/Ishaannarang22/agentoverflow#getting-started). You'll need Node.js 18 or later, an Elastic Cloud deployment and a Lava forward token.
