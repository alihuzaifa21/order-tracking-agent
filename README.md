# Order Tracking Agent (n8n + LLM)

An AI agent built in n8n that answers customer questions like "Where is my order?" by looking up the order in a Google Sheet.


Portfolio: https://alihuzaifa21.github.io

## Problem it solves

Online store customers often ask about their order status, and support staff have to check order data by hand every time. This is repetitive and slow. This agent handles those questions automatically.

## What it does

1. A customer sends a message through an n8n chat trigger.
2. The agent asks for the customer's order ID (or the email used for the order).
3. The AI Agent node, powered by a Groq chat model, uses a Google Sheets tool (Read Rows) to search the order records.
4. If the order exists, the agent replies with the order details.
5. If the order ID does not exist in the records, the agent says so clearly instead of guessing.

The agent also uses a Window Buffer Memory node, so it can follow the conversation.

## Tested cases

| Input | Result |
|-------|--------|
| Valid order ID (1007) | Order found, details returned |
| Valid order ID (1008) | Order found, details returned |
| Invalid order ID (2001) | Agent replies that the order ID is not in the records |

## Tech stack

- n8n (workflow automation)
- Groq chat model (LLM)
- Google Sheets (order data, via the Read Rows action)
- System and user prompts written to define the agent's behavior

## How to run it

1. Install or open n8n.
2. Import the workflow file: order tracking agent.json (Workflows, then Import from File).
3. Add your own credentials: a Groq API key and a Google Sheets account.
4. Create a Google Sheet with order data. Columns used: [for example: order_id, customer_name, status, delivery_date].
5. In the Google Sheets node, select your own sheet.
6. Open the chat and ask about an order.

## Note

All order data in this project is dummy test data. No real customer information is used. The workflow has been built and tested locally in n8n.

## Next improvements

- Add error alerts and automatic retries for failed runs
- Move parts of the system to Python for production use
- Connect to a real order database instead of a Google Sheet

## Author

Ali Huzaifa
GitHub: https://github.com/alihuzaifa21
