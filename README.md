# Data-analyst-agent-test-1
This is to create a simple agent that analyzes data and creates charts. The agent can use the built-in Code Interpreter tool of Azure Foundry AI Agent Service SDK to dynamically generate any code required to analyze data.

## Goal and scenario
You create an agent that can analyze a small text data file, compute statistics, and generate simple chart‑style outputs using the built‑in Code Interpreter tool.

### Steps:

#### Step 1:
Set up Azure AI Foundry project
Sign in to ai.azure.com, use Create an agent, and configure a new Foundry project with subscription, resource group, and an AI‑recommended region.

#### Step 2:
Deploy amd confirm a gpt‑4o model and copy the project endpoint from the Overview page for later use in the client app.

#### Step 3:
Prepare the client app in Cloud Shell
In the Azure portal, open Cloud Shell (PowerShell, classic mode), clone this repo, and inspect the provided code and data files.

#### Step 4:
Create a virtual environment, install requirements.txt plus azure-ai-projects and azure-ai-agents, then edit .env to set the project endpoint and model deployment name (gpt‑4o).

#### Step 5:
Implement the agent logic
In agent.py, add imports for DefaultAzureCredential, AgentsClient, and agent model classes, then instantiate AgentsClient with the project endpoint and current Azure credentials in a with agent_client: block.

Within that block, upload the data file, create a CodeInterpreterTool, define an agent with instructions to analyze the uploaded data using Python, create a conversation thread, send user prompts, process runs, handle failures, display the latest agent reply, print the full conversation history, and finally delete the agent when finished.

#### Step 6:
Run, test, and clean up
After signing in with az login, you run python agent.py, inspect the loaded data.txt, and try prompts like “What’s the category with the highest cost?”, “Create a text-based bar chart showing cost by category”, and “What’s the standard deviation of cost?”.

The thread is stateful, so the agent keeps conversation context, and once done, delete the Azure resource group hosting the lab resources to avoid ongoing costs.
