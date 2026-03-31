[![MCP Compatible](https://img.shields.io/badge/MCP-Compatible-green)](https://modelcontextprotocol.io)
[![OAuth 2.1](https://img.shields.io/badge/Auth-OAuth%202.1-blue)](https://oauth.net/2.1/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Streamable HTTP](https://img.shields.io/badge/Transport-Streamable%20HTTP-purple)](https://modelcontextprotocol.io/specification/2025-03-26/basic/transports#streamable-http)

# InFlow MCP Server

Connect your AI assistant to [InFlow](https://app.inflowpay.ai) for managing payments, wallets, and transactions via the [Model Context Protocol](https://modelcontextprotocol.io).

## Quick Start

**Server URL:**

```
https://app.inflowpay.ai/mcp
```

**MCP Configuration:**

```json
{
  "mcpServers": {
    "inflow": {
      "type": "http",
      "url": "https://app.inflowpay.ai/mcp"
    }
  }
}
```

| Feature            | Details                                                                     |
|--------------------|-----------------------------------------------------------------------------|
| **Transport**      | Streamable HTTP                                                             |
| **Authentication** | OAuth 2.1 (PKCE)                                                            |
| **Tools**          | Balances, Transactions, Deposits, Withdrawals, Policies, Approvals, Account |

## What is MCP?

The **Model Context Protocol** (MCP) is an open standard that allows AI assistants — like Claude, ChatGPT, Cursor, and others — to connect directly to external services. Instead of copying and pasting information between your AI assistant and InFlow, MCP lets your assistant interact with InFlow on your behalf: checking balances, approving payments, managing policies, and more — all through natural conversation.

Think of it like giving your AI assistant a secure, authorized connection to your InFlow account.

## What is InFlow?

InFlow is a payment and wallet platform that allows you to review and manage digital transactions. Whether you are a developer integrating payments into your application, a merchant accepting payments, or an individual managing a wallet, InFlow provides the tools to do so. Connecting your AI assistant to InFlow via MCP means you can manage your account conversationally, without needing to navigate the dashboard for every action.

## What Can You Do with the InFlow MCP?

Once connected, your AI assistant can help you with a range of tasks, including:

- **Balances** — Check your current balances across currencies and wallets.
- **Transactions** — View transaction history and check transaction details.
- **Deposit & Withdrawal** — View deposit addresses, create withdrawal addresses, and initiate withdrawals.
- **Policies** — Create, update, and manage transaction policies that govern how your account operates.
- **Approvals** — Review, approve, or decline pending approval requests.
- **Account** — View your account details and profile information.

You interact with these capabilities using natural language. For example, you might ask your assistant:

- *"What is my current balance?"*
- *"Do I have any pending approvals?"*
- *"Show me my transactions from the last week"*
- *"Create a policy that requires approval for transactions over $500"*

## Prerequisites

1. An **InFlow account**. If you do not have one, you can register at [app.inflowpay.ai](https://app.inflowpay.ai/register/).
2. An **AI assistant or MCP client** that supports the Model Context Protocol (such as Claude, Cursor, VS Code, or any MCP-compatible client).

## Setup

There are two ways to connect your AI assistant to InFlow: through your client's built-in marketplace, or by manually adding the connection.

### Option 1: Find InFlow in Your Client's Marketplace

Many MCP clients have a built-in marketplace or connector directory where you can search for available services. To connect this way:

1. Open your AI assistant's settings or connector marketplace.
2. Search for **"InFlow"**.
3. Select InFlow from the results and follow the prompts to authorize your account.
4. You will be redirected to InFlow to log in and grant access. Once authorized, the connection is complete.

### Option 2: Add InFlow Manually

If your client does not list InFlow in its marketplace, or if you prefer to set up the connection manually, you can add it using the MCP server URL:

```
https://app.inflowpay.ai/mcp
```

The general steps are:

1. Open your MCP client's settings for adding a new connector or MCP server.
2. Use **InFlow** as the name or title for the connection.
3. Enter `https://app.inflowpay.ai/mcp` as the MCP server URL (sometimes called the server URL or endpoint).
4. Save the connection. Your client will redirect you to InFlow to log in and authorize access.

Below are step-by-step instructions for popular clients.

#### Claude

1. Open **Settings** → **Connectors** → **Add custom connector**.
2. Enter `https://app.inflowpay.ai/mcp` as the URL.
3. Complete the OAuth authorization when prompted.

#### Cursor

Create or edit your MCP configuration file at `~/.cursor/mcp.json` (global) or `.cursor/mcp.json` (project) and add:

```json
{
  "mcpServers": {
    "inflow": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://app.inflowpay.ai/mcp"]
    }
  }
}
```

Then enable the server in Cursor settings if prompted.

#### Visual Studio Code

Open the Command Palette → **MCP: Add Server** → select **HTTP** and use:

```json
{
  "servers": {
    "inflow": {
      "type": "http",
      "url": "https://app.inflowpay.ai/mcp"
    }
  }
}
```

#### Claude Code (CLI)

Run the following command in your terminal:

```bash
claude mcp add --transport http inflow https://app.inflowpay.ai/mcp
```

#### Other Clients

For any other MCP-compatible client, you can use `npx` to connect:

```bash
npx -y mcp-remote https://app.inflowpay.ai/mcp
```

Or use the server URL directly if your client supports Streamable HTTP transport:

```
https://app.inflowpay.ai/mcp
```

## Authentication

After adding the InFlow connector, your MCP client will redirect you to InFlow to log in and authorize the connection. This uses OAuth 2.1 with PKCE, the same industry-standard protocol used by services like Google and GitHub for secure authorization. You will only need to authorize once; your client will manage the session from there.

The tools available to your assistant depend on your InFlow account role. For example, a developer account may see different capabilities than a merchant account. You will only see tools that your account is authorized to use.

## Troubleshooting

**I cannot find InFlow in my client's marketplace.**
Not all clients have InFlow listed yet. Use the manual setup instructions above to add the connection directly.

**The OAuth authorization is not completing.**
Make sure you are logged in to your InFlow account in your browser. If you are still having trouble, try clearing your browser cookies for `app.inflowpay.ai` and trying again.

**My assistant says it cannot access a certain tool.**
Tool availability is based on your account role. If you believe you should have access to a tool that is not appearing, contact support at [support@inflowpay.ai](mailto:support@inflowpay.ai).

## Support

If you run into any issues or have questions about the InFlow MCP, reach out to us at [support@inflowpay.ai](mailto:support@inflowpay.ai).
