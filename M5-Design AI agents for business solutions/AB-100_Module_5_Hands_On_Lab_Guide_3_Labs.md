

# Demo : Build AI agents with portal and VS Code

In this exercise, you'll build a complete AI agent solution using both the Microsoft Foundry portal and the Foundry Toolkit VS Code extension. You'll start by creating a basic agent in the portal with grounding data and built-in tools, then interact with it programmatically using VS Code to use advanced capabilities like code interpreter for data analysis.

This exercise takes approximately **45** minutes.

> **Note**: Some of the technologies used in this exercise are in preview or in active development. You may experience some unexpected behavior, warnings, or errors.

## Prerequisites

Before starting this exercise, ensure you have:

- An [Azure subscription](https://azure.microsoft.com/free/) with sufficient permissions and quota to provision Azure AI resources
- [Visual Studio Code](https://code.visualstudio.com/) installed on your local machine
- [Python 3.13](https://www.python.org/downloads/) installed
- [Git](https://git-scm.com/downloads) installed on your local machine
- Basic familiarity with Azure AI services and Python programming

> \* Python 3.14 isn't supported yet: some dependencies have no 3.14 build. This lab was tested with Python 3.13.12.

## Create a Microsoft Foundry Project

Microsoft Foundry uses projects to organize models, resources, data, and other assets used to develop an AI solution.

1. In a web browser, open the [Foundry portal](https://ai.azure.com) at `https://ai.azure.com` and sign in using your Azure credentials. Close any tips or quick start panes that are opened the first time you sign in, and if necessary use the **Foundry** logo at the top left to navigate to the home page.

    > **Important**: For this lab, you're using the **New** Foundry experience.

1. In the top banner, select **Start building** to try the new Microsoft Foundry Experience.

1. When prompted, create a **new** project, and enter a valid name for your project (e.g., `it-support-agent-project`).

1. Expand **Advanced options** and specify the following settings:
    - **Microsoft Foundry resource**: *A valid name for your Foundry resource*
    - **Region**: *Select one available near you*\*
    - **Subscription**: *Your Azure subscription*
    - **Resource group**: *Select your resource group, or create a new one*

    > \* Some Azure AI resources are constrained by regional model quotas. In the event of a quota limit being exceeded later in the exercise, there's a possibility you may need to create another resource in a different region.

1. Select **Create** and wait for your project to be created.

1. When your project is created, close any welcome dialogs.

1. In the Foundry portal, create a new agent named `it-support-agent`. If prompted, set the **Interaction mode** to **Text**.

    When ready, your agent opens in the agent playground.

1. In the model drop-down list, ensure that a model has been deployed and selected for your agent.

## Configure your agent with instructions and grounding data

Now that you have an agent created, let's configure it with instructions and add grounding data.

1. In the agent playground, set the **Instructions** to:

    ```prompt
   You are an IT Support Agent for Contoso Corporation.
   You help employees with technical issues and IT policy questions.

   Guidelines:
   - Always be professional and helpful
   - Use the IT policy documentation to answer questions accurately
   - If you don't know the answer, admit it and suggest contacting IT support directly
   - When creating tickets, collect all necessary information before proceeding
    ```

1. Download the IT policy document from the lab repository. Open a new browser tab and navigate to:

    ```
   https://raw.githubusercontent.com/MicrosoftLearning/mslearn-ai-agents/main/Labfiles/01-build-agent-portal-and-vscode/IT_Policy.txt
    ```

    Save the file to your local machine.

    > **Note**: This document contains sample IT policies for password resets, software installation requests, and hardware troubleshooting.

1. Return to the agent playground. In the **Tools** section, select **Add**, and then add both **File search** and **</> Code interpreter**.

1. To the right of **Add**, select **Upload files**. Under **Attach files**, browse to and upload the `IT_Policy.txt` file you just downloaded, and then select **Attach**.

1. Wait for the file to be indexed. You'll see a confirmation when it's ready.

1. Now let's add some performance data for the code interpreter to analyze. Download the system performance data file from:

    ```
   https://raw.githubusercontent.com/MicrosoftLearning/mslearn-ai-agents/main/Labfiles/01-build-agent-portal-and-vscode/system_performance.csv
    ```

    Save this file to your local machine.

1. To the right of **</> Code interpreter**, select **+ Files**, and then upload the `system_performance.csv` file you just downloaded.

    > **Note**: This CSV file contains simulated system metrics (CPU, memory, disk usage) over time that the agent can analyze.

1. Save the agent.

## Test your agent

Let's test the agent to see how it responds using the grounding data.

1. In the chat interface on the right side of the playground, enter the following prompt:

    ```
   What's the policy for password resets?
    ```

1. Review the response. The agent should reference the IT policy document and provide accurate information about password reset procedures.

1. Try another prompt:

    ```
   How do I request new software?
    ```

1. Again, review the response and observe how the agent uses the grounding data.

1. Now test the code interpreter with a data analysis request:

    ```
   Can you analyze the system performance data and tell me if there are any concerning trends?
    ```

1. The agent should use the code interpreter to analyze the CSV file and provide insights about system performance.

1. Try asking for a visualization:

    ```
   Create a chart showing CPU usage over time from the performance data
    ```

1. The agent will use code interpreter to generate visualizations and analysis.

Great! You've created an agent with grounding data, file search, and code interpreter capabilities. In the next section, you'll interact with this agent programmatically using VS Code.

## Interact with your agent using VS Code

As a developer, you may spend some time working in the Foundry portal; but you’re also likely to spend a lot of time in Visual Studio Code. The Foundry Toolkit for VS Code extension provides a convenient way to work with Foundry project resources without leaving the development environment.

### Install and configure the VS Code extension

If you already have installed the Foundry Toolkit extension, you can skip this section.

1. Open Visual Studio Code.

2. Select **Extensions** from the left pane (or press **Ctrl+Shift+X**).

3. Search the extensions marketplace for the `Foundry Toolkit for VS Code` extension from Microsoft and select **Install**.

    Installing the Foundry Toolkit Extension will add the Foundry Toolkit extension to VS Code.

    > **Note**: The extension is currently listed as **Foundry Toolkit**, but some VS Code labels, commands, or older screenshots may still refer to **AI Toolkit**. In this lab, treat those names as referring to the same extension experience.

4. After installing the extension, select the Foundry Toolkit icon in the sidebar.

    You should be prompted to sign in to your Azure account if you haven't already.

### Test your agent in VS Code

Before writing any code, you can interact with your agent directly in the extension interface.

1. Under **Microsoft Foundry Resources**, choose **Set Default Project**

    If a default project is already active, the project name will appear in the resources list. You can select a different project by selecting the same **Select project** icon.

2. Expand the project section. Under **Prompt Agents**, you should see the `it-support-agent` you created in the portal. Select the agent name to open the Agent Builder interface.

    The agent playground will appear in the Agent Builder interface, allowing you to interact with the agent and configure its settings without leaving VS Code.

3. In the playground chat pane, type a question such as:

    ```
   What is the policy for reporting a lost or stolen device?
    ```

4. Review the agent's response. It should use the grounding data you uploaded earlier to provide relevant IT policy information.

    > **Tip**: You can use this built-in playground to quickly test your agent's instructions and knowledge without writing any code.
