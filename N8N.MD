It’s an open-source workflow automation tool that: Connect APIs, services, and apps, Automate repetitive tasks, Build data pipelines and logic flows

- functions similarly to Zapier


How is it different: Visual drag-and-drop interface, Self-hostable (can run on your own server), JavaScript & expressions for flexibility, 
400+ integrations (nodes for Google Sheets, Slack, Telegram, Airtable, APIs, etc.), Webhooks and scheduled workflows


In n8n there are mainly three types of nodes:
1. trigger ndoes: start the worklow
2. regular nodes: perfrom actions like http req, google sheet actions, airtable operations
3. logic nodes: add conditional logic like if-else, switch ,set, merge

Each node passes data to the next.

in n8N API and Webhooks are used to process send and reciecve data from and to external services like weather api, DB, google serach 


### Handle Data in N8N
n8n uses JSON as its internal data format. Every node --> Receives items (objects with key-value pairs)-->Processes the items-->Passes them to the next node

# Ttpical N8N work
Triger node --> Processing node-->logic nodes--> end nodes

