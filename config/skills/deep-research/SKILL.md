---
name: deep-research
description: |
  Use when asked to research any technical topic, investigate how something works, find documentation, explore APIs, or gather information from the web.
  Triggers on: "research", "investigate", "find out", "how does", "what is", "deep dive", "look into", "explore", "study", "analyze", "figure out", "learn about", "compare", "survey", "gather information"
---

# Deep Research — Parallel Agent Investigation

## Overview
Dispatch multiple parallel research agents to investigate different angles of a technical topic simultaneously. Each agent focuses on one independent dimension of the question, returning comprehensive findings. You then synthesize results.

## When to Use
- User asks to research a technical topic: APIs, libraries, protocols, architectures
- Investigating how a system works internally
- Comparing multiple approaches/technologies
- Gathering documentation, open-source projects, and real-world implementations
- Exploring undocumented or reverse-engineered features
- ANY research question with 2+ independent angles

## The Pattern

### 1. Identify Independent Research Dimensions
Break the topic into 3-5 orthogonal angles. Each agent investigates a different slice:

**Example (TradingView indicator data extraction):**
- Agent 1: Pine Script engine internals & data access
- Agent 2: Charting Library API & embedded widget
- Agent 3: Reverse-engineering & scraping approaches
- Agent 4: Alert/webhook bridge methods

### 2. Craft Agent Prompts
Each agent gets:
- A focused, narrow scope (one dimension only)
- Specific search queries to try
- Clear output requirements
- Instruction to use websearch + webfetch (not local codebase)

### 3. Dispatch in Parallel
Use the `task` tool with `subagent_type: "general"` for all agents simultaneously.

### 4. Synthesize Results
When agents return, compile findings into structured sections organized by approach.

### 5. Save as Skill (if discovery is novel)
If the research uncovered a novel or complex workflow, offer to save it as a skill.

## Agent Prompt Template
```
You are doing DEEP WEB RESEARCH on a technical topic. Do NOT search the local codebase.
Use websearch and webfetch extensively.

## Topic: [focus area]

Research [specific dimension] covering:
1. [question 1]
2. [question 2]
3. [question 3]

Search for:
- "[search query 1]"
- "[search query 2]"

Return: Comprehensive research report covering all questions with source URLs.
```

## Verification
- Each agent should return source URLs for claims
- Cross-reference findings between agents for consistency
- Flag any conflicting information for user clarification

## Common Pitfalls
- Agents going too broad — keep each scope narrow
- Agents repeating the same searches — ensure each has unique queries
- Agents not using web tools — explicitly tell them to search the web
- Including too many agents (5+ is usually excessive)
