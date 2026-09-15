# Cracking the multi-day transcript Q&A agent

If you have multiple days worth of transcripts, querying them directly is a nightmare. The context window gets bloated, the latency goes through the roof, and the LLM starts hallucinating or losing the thread. Getting an answer takes forever, and the quality is usually compromised.

I needed a way to create a dedicated Q&A agent that could read all of it, understand the context, and return any answer quickly with great quality. No lag. No dropped context.

I had only an in-house Copilot subscription at hand. By structuring the ingestion and optimizing how the agent retrieves and synthesizes the data, it now handles days of raw transcripts and instantly fires back highly accurate answers.

You're welcome.
