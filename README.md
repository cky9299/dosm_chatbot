# Project Overview 
A chatbot that answers FAQ about Monthly Unemployment, based on the Department of Statistics Malaysia dataset. Created with no-code open-source workflow tool, Dify.

To focus on a narrow slice of the dataset, only data from the last 24 months is included in its knowledge base.

## Visual flow
![Visual flow](res\images\flow.png)

## Actions
- Export data to CSV
- Summarize unemployment trend

## Responsible AI
The LLM will refuse to entertain queries that are off-topic or unsafe.
missing data is handled via system prompt that instructs the LLM not to make any assumptions and acknowledges it doesn't know to prevent LLM from hallucinating


## Included Nice-to-Haves (Bonus) Features
- Retry node (in LLM node) that handles exceptions and retries LLM inference on failure, such as temporary network issues
> _Properties:_
>- Max retries: 3
>- Retry interval: 1 s

- Guardrail node (chat feature) that equip LLM with OpenAI Moderation, filtering harmful or illegal input and output content.

- An action that returns a CSV from the retrieved data.

- MCP wrapper exposing actions like export_csv
[MCP Server](https://api.dify.ai/mcp/server/4xC5sXnN3MaAzRl8/mcp)

- LLM provides streaming responses.



# Quickstart
## Use Hosted App
 Start chatting at [uDify](https://udify.app/chat/q6QQYb8EhgMFJMXM)
 

## Manually Import App
<ol>
<li>Create an app at <a href='https://cloud.Dify.Ai/apps'>[Dify]</a></li>
<li>Click Create from Blank</li>
<li>Set App Type as chatflow</li>
<li>Create app</li>
<li>Import DSL file from this repo</li>
<li>Add dataset to knowledge base</li>
<li>Add knowledge to LLM node</li>
<li>Click preview to start chatting</li>
</ol>



# Tool Choice
 Dify

## Model/Provider
 Text-embedding-3-large
 OpenAI


# Dataset Data Card
```
{
  "dataset_name": "Monthly Unemployment by Duration",
  "source_urls": [
    "https://storage.Dosm.Gov.My/labour/lfs_month_duration.csv",
  ],
  "refresh_cadence": "monthly",
  "license": "CC-BY 4.0",
  "last_updated_date": "2025-09-10"
}
```

# RAG Design
- Delimiter
  - \n\n

- Maximum chunk length
  - 1024 Characters

- Chunk length
  - 201 characters

- Chunk overlap
  - 50 Characters

- Top K
  - 3

- Model
  - Text-embedding-3-large



# Citation Format
 File name with section showing row number and content



# Evaluation Methodology 
## Metrics Measurement

After receiving a response to each question, the citation is referred to verify the right row within the cited file is retrieved, confirming the response is a hit. The response is verified to be accurate and contains no hallucination. Hence, the response is a pass.
By clicking on the chat logs icon, the latency could be seen.
The latency value, hit and hallucination status are recorded. 


## Results Computation

The median latency is computed from the recorded latencies.


The rates are computed using the formula:

$$
\begin{align*}

\text{Retrieval hit-rate} = \frac{\text{Number of hits}}{\text{total chatbot queries}}
\\
\\
\text{Hallucination rate} = \frac{\text{Number of hallucinations}}{\text{total chatbot queries}}

\end{align*}
$$



# Results

| median/p50 latency (s) | p95 latency (s) | retrieval hit-rate  | hallucination rate |
|----------|----------|----------|----------|
| 1.258  | 1.618 | 1  | 0  |


## logging
![Conversation Log](res\images\Conversation_Log.png)

![latencies_in_steps](res\images\latencies_in_steps.png)



# Known Limitations & Future Work

- Only basic metrics are reported.
  - More detailed metrics like f1, precision, recall over words may be reported.

- Metrics computation is manual
  - Code script to automatically log and compute metrics

- Chatbot only supports natural-language user queries
  - Add feature via Dify to enable user to upload file as input




# Demo Video 
[Google Drive](https://drive.google.com/drive/folders/1dyjsgjR8J_8HPtJveKj0BUkCq0z-M_n8?usp=sharing)




