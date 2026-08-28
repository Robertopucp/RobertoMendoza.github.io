---
title: "INDECOPI Chatbot: Virtual Assistant Against Banking Fraud"
excerpt: "A Telegram and REST API virtual assistant that guides Peruvian banking consumers on their rights against financial fraud, powered by a RAG pipeline over real INDECOPI resolutions."
collection: portfolio
permalink: /portfolio/project-2
---

{% include base_path %}

## Overview

This project is a virtual assistant that guides users of the Peruvian banking system on their rights as consumers against financial fraud, based on real resolutions from INDECOPI (Instituto Nacional de Defensa de la Competencia y de la Protección de la Propiedad Intelectual, the Peruvian consumer protection authority). It is available as a Telegram bot ([@IndecopiChatbot](https://t.me/IndecopiChatbot)) and as a REST API.

## Problem

Consumers affected by banking fraud in Peru often don't know their rights, which agency to contact, or what past cases show about how similar complaints were resolved. That information exists in INDECOPI's official resolutions, but those documents are long, technical, and hard for the public to search. This project turns that corpus into a conversational assistant that answers in plain language while grounding every answer in the underlying resolutions, and filters out sensitive personal data before it reaches the user.

## RAG Architecture

The chatbot combines three response layers, applied in order of priority:

1. **FAQ layer:** the query is compared against a fixed bank of frequently asked questions about INDECOPI using embedding similarity. If the best match is above the threshold, it answers directly, without touching the resolutions or the LLM.
2. **RAG layer (Retrieval Augmented Generation):** if there is no FAQ match, the system retrieves the most relevant passages from INDECOPI's final resolutions, indexed in a vector database.
3. **LLM layer:** the retrieved context is passed to a language model, which generates the final answer in natural language and cites the source resolution.

A security layer screens both the user's input and the model's output for forbidden words and sensitive content (names, national ID numbers, fine amounts) before any response is returned.

<figure>
  <img src="{{ base_path }}/images/rag_diagram.png" alt="RAG architecture of the INDECOPI chatbot: Telegram and API request flow through the FAQ, RAG, and LLM layers">
  <figcaption>
    Request flow: a message from Telegram or the API first passes an input security check, then the FAQ layer; if there is no FAQ match, it goes through the RAG retrieval and LLM generation layers, an output security check, and finally back to the user.
  </figcaption>
</figure>

## Tech Stack

| Component | Tool |
|---|---|
| LLM | Qwen3.5-9B, served via Hugging Face (OpenAI-compatible endpoint) |
| Embeddings | OpenAI `text-embedding-3-small` |
| Retrieval/integration framework | LangChain |
| Vector database | FAISS |
| Interaction channel | Telegram bot ([@IndecopiChatbot](https://t.me/IndecopiChatbot)) |
| API | FastAPI |

The knowledge base consists of 12 final INDECOPI resolutions on banking fraud complaints filed by individual consumers in Peru.

## Screenshots

<figure>
  <img src="{{ base_path }}/images/Indecopi_web_2.png" alt="INDECOPI chatbot answering a question through the FAQ layer">
  <figcaption>
    A question answered directly by the FAQ layer, without invoking retrieval or the LLM.
  </figcaption>
</figure>

<figure>
  <img src="{{ base_path }}/images/Indecopi_web_4.png" alt="INDECOPI chatbot blocking a response that would have exposed sensitive data">
  <figcaption>
    Example of the security layer blocking a response, since the underlying resolutions contain sensitive data such as claimants' names, national ID numbers, and fine amounts.
  </figcaption>
</figure>

## Project Repository

<a href="https://github.com/Robertopucp/Chatbot-AIGenerative-BankingSystem" class="btn btn--primary" target="_blank" rel="noopener noreferrer">View on GitHub</a>
