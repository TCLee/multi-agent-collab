# Build an Agent with LangGraph

## Overview
By themselves, language models can't take actions - they just output text. A big use case for LangChain is creating agents. Agents are systems that use an LLM as a reasoning engine to determine which actions to take and what the inputs to those actions should be. The results of those actions can then be fed back into the agent and it determines whether more actions are needed, or whether it is okay to finish.

[LangGraph](https://github.com/langchain-ai/langgraph) 
is an extension of LangChain specifically aimed at creating highly controllable and customizable agents.

In the [notebook](agent_langgraph.ipynb) we will build an agent that can interact with a search engine. You will be able to ask this agent questions, watch it call the search tool, and have conversations with it.

The code in the notebook is adapted from the LangGraph tutorial: 
[Introduction to LangGraph](https://langchain-ai.github.io/langgraph/tutorials/introduction/).


## Setup

### Git
Clone this repository to your local computer by running:

```zsh
git clone https://github.com/TCLee/agent-langgraph
```

### Conda
1. You will need conda in order to install the required packages to run the notebook. [Installing conda](https://docs.conda.io/projects/conda/en/stable/user-guide/install/index.html).

2. Make sure the current working directory is this cloned project's directory:

   ```zsh
   cd /path/to/agent-langgraph
   ```
   
3. Create the environment from the 
   [`environment.yml`](environment.yml) file:

    ```zsh
    conda env create -f environment.yml -p ./env
    ```

    This will create a new environment in a subdirectory of the project directory called `env`, (i.e., `agent-langgraph/env`)

4. Activate the environment: 

    ```zsh
    conda activate ./env
    ```

### Environment variables
This project makes use of 
[python-dotenv](https://github.com/theskumar/python-dotenv)
to load in the environment variables from a `.env` file.

Create a `.env` file in the root directory of this cloned repository
(i.e., `agent-langgraph/.env`):

```Dotenv
# Google Gemini API
GOOGLE_API_KEY="your-google-secret-key"

# Tavily Search API
TAVILY_API_KEY="your-tavily-secret-key"

# Optional. Recommended to see what's going on 
# under the hood of LangGraph and LangChain.
LANGSMITH_API_KEY="your-langsmith-secret-key"
LANGCHAIN_TRACING_V2="true"
LANGCHAIN_PROJECT="LangGraph Tutorial"
```

Fill it in with your own API keys.

#### Google Gemini
The LLM that we will use in the notebook is Google's **Gemini 1.5 Flash**, since it offers a free tier for us to play around with.

To use the Gemini API, you'll need an API key. If you do not already have one, create a key in Google AI Studio.

[Get an API key](https://makersuite.google.com/app/apikey)


#### Tavily Search
[Tavily's Search API](https://tavily.com/) is a search engine built specifically for AI agents (LLMs), delivering real-time, accurate, and factual results at speed.


#### (Optional) LangSmith
Many of the applications you build with LangChain will contain multiple steps with multiple invocations of LLM calls. As these applications get more and more complex, it becomes crucial to be able to inspect what exactly is going on inside your chain or agent. The best way to do this is with [LangSmith](https://smith.langchain.com/).


### Jupyter Notebook

The conda environment includes an installation of [Jupyter Lab](https://jupyter.org/). Start Jupyter Lab from your terminal:

```zsh
jupyter lab
```

In Jupyter Lab, open the notebook 
[`agent_langgraph.ipynb`](agent_langgraph.ipynb) 
and follow the instructions there.