![LangChain Academy](https://cdn.prod.website-files.com/65b8cd72835ceeacd4449a53/66e9eba1020525eea7873f96_LCA-big-green%20(2).svg)

## Introduction

Welcome to LangChain Academy! 
This is a growing set of modules focused on foundational concepts within the LangChain ecosystem. 
Module 0 is basic setup and Modules 1 - 4 focus on LangGraph, progressively adding more advanced themes. 
In each module folder, you'll see a set of notebooks. A LangChain Academy accompanies each notebook 
to guide you through the topic. Each module also has a `studio` subdirectory, with a set of relevant 
graphs that we will explore using the LangGraph API and Studio.

## Setup

### Python version

To get the most out of this course, please ensure you're using Python 3.11 or later. 
This version is required for optimal compatibility with LangGraph. If you're on an older version, 
upgrading will ensure everything runs smoothly.
```
python3 --version
```

### Clone repo
```
git clone https://github.com/langchain-ai/langchain-academy.git
$ cd langchain-academy
```

### Create an environment and install dependencies
#### Mac/Linux/WSL
```
$ python3 -m venv lc-academy-env
$ source lc-academy-env/bin/activate
$ pip install -r requirements.txt
```
#### Windows Powershell
```
PS> python3 -m venv lc-academy-env
PS> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process
PS> lc-academy-env\scripts\activate
PS> pip install -r requirements.txt
```

### Running notebooks
If you don't have Jupyter set up, follow installation instructions [here](https://jupyter.org/install).
```
$ jupyter notebook
```

### Setting up env variables
Briefly going over how to set up environment variables. You can also 
use a `.env` file with `python-dotenv` library.
#### Mac/Linux/WSL
```
$ export API_ENV_VAR="your-api-key-here"
```
#### Windows Powershell
```
PS> $env:API_ENV_VAR = "your-api-key-here"
```

### Set OpenAI API key
* If you don't have an OpenAI API key, you can sign up [here](https://openai.com/index/openai-api/).
*  Set `OPENAI_API_KEY` in your environment 

### Sign up and Set LangSmith API
* Sign up for LangSmith [here](https://smith.langchain.com/), find out more about LangSmith
* and how to use it within your workflow [here](https://www.langchain.com/langsmith), and relevant library [docs](https://docs.smith.langchain.com/)!
*  Set `LANGSMITH_API_KEY`, `LANGSMITH_TRACING_V2=true` `LANGSMITH_PROJECT="langchain-academy"`in your environment 

### Set up Tavily API for web search

* Tavily Search API is a search engine optimized for LLMs and RAG, aimed at efficient, 
quick, and persistent search results. 
* You can sign up for an API key [here](https://tavily.com/). 
It's easy to sign up and offers a very generous free tier. Some lessons (in Module 4) will use Tavily. 

* Set `TAVILY_API_KEY` in your environment.

### Set up LangGraph Studio

* LangGraph Studio is a custom IDE for viewing and testing agents.
* Studio can be run locally and opened in your browser on Mac, Windows, and Linux.
* See documentation [here](https://langchain-ai.github.io/langgraph/concepts/langgraph_studio/#local-development-server) on the local Studio development server and [here](https://langchain-ai.github.io/langgraph/cloud/how-tos/studio/quick_start/#local-development-server). 
* Graphs for LangGraph Studio are in the `module-x/studio/` folders.
* To start the local development server, run the following command in your terminal in the `/studio` directory each module:

```
langgraph dev
```

You should see the following output:
```
- 🚀 API: http://127.0.0.1:2024
- 🎨 Studio UI: https://smith.langchain.com/studio/?baseUrl=http://127.0.0.1:2024
- 📚 API Docs: http://127.0.0.1:2024/docs
```

Open your browser and navigate to the Studio UI: `https://smith.langchain.com/studio/?baseUrl=http://127.0.0.1:2024`.

* To use Studio, you will need to create a .env file with the relevant API keys
* Run this from the command line to create these files for module 1 to 5, as an example:
```
for i in {1..5}; do
  cp module-$i/studio/.env.example module-$i/studio/.env
  echo "OPENAI_API_KEY=\"$OPENAI_API_KEY\"" > module-$i/studio/.env
done
echo "TAVILY_API_KEY=\"$TAVILY_API_KEY\"" >> module-4/studio/.env
```
Module 1
Video 1 Motivation:

> It helps you make systems where AIs can think through steps, make their own decisions, and even adapt when things change. Instead of a straight, one-way process, it gives your AI the power to move, loop back, and explore multiple paths just like humans do.datacouch​LangChain_Academy_-Introduction_to_LangGraph-_Motivation.pdf​

> It strikes a good git balance between structure and freedom , you can still control critical parts of how your AI works, but let it handle dynamic, unpredictable scenarios on its own. This makes your agents smart, efficient, and ready for real world tasks

Video 2 SimpleGraph
>I learnt how a LangGraph is built using connected nodes and edges, where data (the state) moves from one step to the next.

>I saw how to add a conditional edge so the graph can take different paths depending on a rule — like choosing between two nodes.

>Finally, I ran the graph to see how it updates the state at each step, giving different results each time based on the path it takes.

Video 3 Langsmith Studio
>I got a quick intro on how to use langsmith studio. 
> It helps with the visualisation of what i just created

Video 4 Chain
>I learned how the reducer function manages the flow of information by updating and combining different parts of the conversation as the chain progresses.

>I understood how the message state maintains context across multiple exchanges, ensuring the model remembers previous inputs and responses within the chat flow.

>Created a divide tool.

Video 5 Router
>I learnt about the Router concept in LangGraph, where a chat model can decide whether to respond directly in natural language or to call a specific tool based on the user’s input. This taught me how an AI agent can dynamically manage control flow depending on the situation.

>I learnt how to build conditional logic in graphs by using nodes and conditional edges to control the flow routing between a tool-calling node and a response node depending on what the model outputs.

>I learnt how to implement tools in LangChain, such as creating a simple function like multiply(a, b) and binding it to the model using llm.bind_tools(). This showed me how to make a chat model interact intelligently with tools as part of its reasoning process.

Video 6 Agents
>Saw a dynamic router architecture where the chat model decides whether to respond in natural language or call a tool based on user input, enabling flexible control flow in LangGraph.

>Saw the implementation conditional edges and nodes to manage execution flow, routing between assistant and tool nodes, forming a loop that allows the model to call multiple tools sequentially or respond directly.

>Learnt the Integratation multiple simple math tools (add, multiply, divide) with LangChain through llm.bind_tools(), enabling the model to invoke tools in sequence and reason about their outputs using a ReAct-like agent architecture.

Video 7 Agent Memory
>I learnt how to build an AI agent with memory that can remember past interactions and use that memory to improve future responses and decision-making.

>I learnt that an agent works through a continuous cycle of acting, observing, and reasoning — where it calls tools, analyzes results, and decides what to do next — and that adding memory makes this process more intelligent and context-aware.


MODULE 2
VIDEO 1: STATE-SCHEMA

>Explored different ways to define and manage state in LangGraph, and I saw how Pydantic gives stronger, real-time validation compared to TypedDict and dataclasses.

>learned how the graph can branch based on the state (like deciding mood), and I even expanded it by adding a “neutral” path to handle more realistic outcomes.

>I now understand that enforcing valid values in state isn’t just theory—Pydantic actively prevents bad data from slipping through, making the agent more reliable in real-world scenarios.

VIDEO 2: STATE-REDUCERS

>Learned that reducers in LangGraph control how state updates happen — instead of overwriting values, they can merge or append data, which is crucial when multiple nodes update the same key in parallel.

>Understood that I can create custom reducers to handle special cases, like when inputs are None, ensuring smoother and more flexible state updates.

>Discovered that LangGraph’s built-in add_messages reducer makes managing chat histories easier by automatically appending, updating, or removing messages based on their IDs.

VIDEO 3 : MULTIPLE SCHEMA

> Explored how private states enable nodes to exchange internal information while keeping those details hidden from the user in the final output.

> Saw that type hints determine which parts of the state each node reads from or writes to, clearly defining the data flow within the graph.

>Noted that by defining different input and output schemas, we can filter what enters and leaves the graph, ensuring the user only interacts with essential information.


VIDEO 4 TRIM AND FILTER MESSAGES

>Handling long chats smartly: When conversations get long, sending all messages to the LLM can be slow and costly. We need ways to manage which messages are actually sent.

>Keeping only what matters: Using a filter_messages approach, we can drop older messages and keep just the recent ones, so the LLM focuses on the most relevant context.

>Feeding the model selectively: Even if we maintain the full chat history, we can choose to run the model on just the latest message. This keeps memory intact but reduces token usage.

>Trimming by token size: With trim_messages, we can control how much of the conversation is sent to the LLM—either only the latest message or a partial slice of prior messages—to stay within token limits

VIDEO 5 Chatbot w/ Summarizing Messages and Memory

> We can use an LLM to automatically produce a running summary of a conversation, compressing older messages while preserving important information.

> By storing conversation state with a summary key and using a MemorySaver checkpointer, we can maintain conversation history across multiple graph invocations.

> We can delete older messages (keeping, for example, the last two) after summarization, reducing token usage and keeping the conversation manageable.

> Summaries are triggered based on the number of messages (for instance, after six), allowing the assistant to handle long-running multi-turn conversations without losing context.

VIDEO 6 Chatbot w/ Summarizing Messages and External Memory

>You learned how to build a chatbot that can carry on long conversations by remembering past messages and summarizing older ones, which helps keep things efficient.

> An in-memory checkpointer works for a single session, but using databases like SQLite or Postgres lets your chatbot “remember” conversations even if you restart your notebook.

> The chatbot can automatically create summaries after a certain number of messages (like six), so it keeps the important info without getting bogged down by old messages.

> LangGraph Studio makes it easy to manage multiple conversation threads with built-in persistence, letting you pick up right where you left off.
