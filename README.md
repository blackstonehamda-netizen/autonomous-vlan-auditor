# Autonomous AI Agent for Network Segmentation and VLAN Isolation Auditing

> ⚠️ **Work in Progress** — this is an early prototype demonstrating the AI agent architecture (autonomous script generation + self-correction loop). VLAN/network setup and deeper validation logic are still in progress.

This project implements an autonomous security auditor built with a custom, zero-dependency Agentic Framework. The architecture utilizes the Gemini 3.6-flash API as its core cognitive reasoning engine to automate inter-VLAN boundary enforcement checks.

## Architecture and Workflow

Instead of executing static or hardcoded security scripts, this system utilizes a closed-loop autonomous AI agent cycle:

1. Goal Acquisition: The agent ingests high-level natural language instructions defining the target audit parameters (e.g., verifying isolation boundaries between an untrusted Guest VLAN 10 and a secured Internal VLAN 20).
2. Dynamic Code Synthesis: The core reasoning engine dynamically synthesizes specific Python verification code tailored to local environmental constraints.
3. Localized Tool Execution: The runtime engine pipes the generated script directly into an isolated local memory scope for live network probing.
4. Self-Correction Pipeline: If a runtime exception or script error occurs, the system captures the execution stack trace and automatically feeds it back to the language model for immediate refinement and automated re-execution.
5. Executive Synthesis: Upon successful execution, the agent parses raw network responses to compile a structured compliance remediation report directly to the console.

## Technical Specifications

* Language and Runtime: Python 3.14+
* Core Reasoning Engine: Google Gemini 3.6-flash API
* System Dependencies: Native Python subprocess, io, and contextlib modules (completely free of external binary dependencies like jiter to comply with strict Windows Application Control and endpoint protection policies)

## Local Configuration and Deployment

To run this autonomous auditor locally without hardcoding sensitive API keys:

1. Clone or download this repository.
2. Initialize your Google AI Studio access token within your temporary terminal environment variables:
   
   set GEMINI_API_KEY=your_secret_key_here

3. Execute the autonomous auditor application:
   
   python vlan_agent.py
