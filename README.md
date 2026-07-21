# MEOWL-Marketing-Engine-Optimization-though-Web-Learning
MEOWL (Marketing Engine &amp; Optimization through Web Learning) is a recommendation engine for small and medium-sized businesses/SME's. It ingests a business’s revenue reports, workforce, and market data, then uses LLM-driven analysis to identify specific, actionable growth opportunities.

<img width="200" height="200" alt="Screenshot 2026-07-21 13 57 48" src="https://github.com/user-attachments/assets/6a0cd102-89a3-415d-8292-1ff183986790" />

####MEOWL
**M**arketing **E**ngine & **O**ptimization through **W**eb **L**earning

## What is this?
MEOWL ingests a small business's revenue data (and eventually workforce, capex, and 
competitor data) and generates specific, actionable growth recommendations, not generic 
marketing advice, but insights grounded in that business's actual numbers and current consumer trends.

## Who is this for?
- Small business owners who can't afford McKinsey-style consulting but want data-driven 
  marketing guidance
- Developers/collaborators/students looking to understand or contribute to the project 

## Why build this?
Small businesses are priced out of real strategic analysis. Generic marketing advice 
("post more on Instagram" or "try email marketing") ignores what's actually happening in their revenue and target market. 

MEOWL closes that gap by grounding every recommendation in the business's own numbers: 
if revenue dips every February, it says so and suggests a seasonal push instead of a 
generic content calendar. If a competitor two miles away is running more reviews and 
lower prices, it flags that specific gap.

## How it works
1. Business owner uploads revenue data (CSV, v1)
2. Data is parsed and stored per-customer (Supabase, with row-level security for isolation)
3. On request, relevant data is pulled and assembled into a prompt
4. Prompt is sent to a frontier LLM via API for analysis
5. Specific recommendations are returned to the user

## Models and Framework

MEOWL uses a Retrieval-Augmented Generation (RAG) architecture: customer data is 
retrieved from Supabase (isolated per customer via Row Level Security) and passed 
as context to Claude (Anthropic) via API for analysis. No model training or 
fine-tuning is performed on the language model, recommendations originate from 
business's actual data through retrieval and prompt design.

Planned: a supplementary PyTorch-trained forecasting model (trained per-customer 
on their historical revenue) to feed predictive signals into the RAG pipeline, 
separate from and complementary to the LLM analysis layer.

## Tech stack
Next.js, Supabase (Postgres + Auth + Row Level Security), Claude API

MEOWL is as much a learning project as a product: built to develop real skill in SQL/database design, applied marketing analysis, and AI integration (RAG, prompt design, knowing where an LLM should and shouldn't be used). The goal is to understand why each piece works, not just ship a working app.
