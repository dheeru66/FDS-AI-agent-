📦 Food Delivery System – n8n Workflow

This project is an AI-powered Food Delivery Automation Workflow built with n8n.
It integrates Google Sheets with LangChain AI (Google Gemini) to manage orders, FAQs, and inventory checks seamlessly.

🚀 Features

AI-Powered Chat – Uses Google Gemini (via LangChain) to understand and respond to customer queries.

Inventory Validation – Only accepts orders available in the Google Sheets "Inventory" tab.

FAQ Automation – Retrieves FAQs from the Google Sheets "FAQ" tab and answers customer questions.

Order Logging – Automatically stores new customer orders into the "Orders" tab with a timestamp.

Conversation Memory – Maintains context for better responses using a simple memory buffer.

🛠️ Workflow Overview
1. Trigger

Node: When chat message received

Starts the workflow whenever a customer sends a chat message.

2. AI Agent

Node: AI Agent (LangChain Agent)

Uses a system message:

"Only take those orders that are available in the excel sheet"

Acts as the decision-maker by checking inventory, answering FAQs, or placing an order.

3. Google Gemini Chat Model

Node: Google Gemini Chat Model

Powered by Google PaLM API.

Handles natural language understanding and AI responses.

4. Memory

Node: Simple Memory

Keeps recent chat context (window length: 50 messages).

5. Google Sheets Tools

Get Inventory → Reads food items and availability from the Inventory sheet.

Get FAQ → Fetches FAQs from the FAQ sheet.

Post Orders → Appends customer orders into the Orders sheet with:

Customer Name

Food Item

Quantity Ordered

Status

Ordered Date (auto-generated)

📊 Google Sheets Setup

The system relies on a Google Sheets document structured as follows:

Inventory (gid=0)
Contains available food items and stock levels.

FAQ (gid=1410238715)
Stores common customer questions and answers.

Orders (gid=1678067262)
Logs placed orders with fields:

Customer Name

Food Item

Quantity Ordered

Status

Ordered Date

🔑 Credentials Required

Google Sheets OAuth2 API (to read/write sheets).

Google Gemini (PaLM) API Key (for AI chat responses).

⚙️ How It Works

Customer sends a message → Workflow triggered.

AI Agent checks:

If it’s an order → Validates against Inventory sheet.

If it’s a query → Searches FAQ sheet.

If valid order → Post Orders logs it into Orders sheet with timestamp.

AI responds back to the customer with confirmation or relevant answer.

📌 Example Flow

User: "I want 2 Burgers"

✅ AI checks Inventory sheet → Burgers available.

📝 AI writes to Orders sheet → Customer Name, Item, Quantity, Status=Pending, Ordered Date=Timestamp.

🤖 AI replies: "Your order for 2 Burgers has been placed successfully!"

📝 Notes

Orders are only processed if the item exists in the Inventory sheet.

Workflow must be activated in n8n for real-time usage.

Ensure proper API credentials are configured in your n8n instance.

📂 Project Metadata

Workflow ID: 3YGdBSkD0Q8F3R8H

Version ID: d0247170-fdbc-49de-9707-afef7c7295f3
