# 🤖 AI Multi-Agent E-Commerce Support System

A supervisor-based multi-agent AI system built in **n8n** that automates end-to-end e-commerce customer support — product inquiries, order tracking, refunds, complaints, and human escalation — using a team of specialized AI agents that work together like a real support team.

---

## 📌 Project Overview

Instead of a single chatbot trying to handle every type of request, this system uses a **Supervisor Agent** that reads each customer message, classifies its intent, and routes it to the correct **specialized employee agent** — just like a real shop supervisor assigning tasks to the right department.

Each specialized agent has its own role, its own instructions, and its own connection to a **Supabase** database table, so it only ever works within its area of responsibility.

---

## 🧠 Multi-Agent Architecture
User Message
│
▼
Supervisor Agent ──► classifies intent
│
▼
Switch (router)
│
├──► Product Inquiry Agent → Supabase: Product Inquiry
├──► Order Tracking Agent → Supabase: Order Tracking Agent
├──► Refund Agent → Supabase: Refund Agent
├──► Complaint Agent → Supabase: Customer Complaint Agent
└──► Human Support Agent → Supabase: Human Support Agent

### 🧭 Supervisor Agent
Reads the current user message and classifies it into exactly one intent — `product_inquiry`, `order_tracking`, `refund`, `complaint`, or `human_support` — without answering the customer itself. When a message matches multiple intents, it resolves the conflict using a fixed priority order: **complaint → refund → order_tracking → human_support → product_inquiry**.

### 🛍️ Product Inquiry Agent
Acts as a customer dealing employee — recommends products, and answers questions about price, availability, features, and comparisons. Never touches orders, refunds, or complaints.

### 📦 Order Tracking Agent
Acts as an operations employee — automatically extracts the Order ID from the customer's message and returns product name, order status, tracking number, and estimated delivery date.

### 💳 Refund Agent
Acts as a cashier employee — checks refund status, amount, method, and reason for a given order, and offers to create a new refund request if none exists. Never invents refund information.

### ⚠️ Complaint Agent
Acts as a complaint handling employee. It first checks whether a complaint already exists for the given Order ID. If none exists, it collects the details and creates a new complaint record. If a complaint already exists, it intelligently distinguishes between the customer following up on the *same* issue versus reporting a *new* issue on the same order — updating the existing record's type, description, priority, and status accordingly.

### 🧑‍💼 Human Support Agent
Acts as a support employee — connects customers with human support when automated agents can't resolve an issue, creates new support tickets, and escalates existing ones.

---

## 🛠️ Tech Stack

- 🔄 **n8n** — workflow orchestration and agent automation
- 🤖 **OpenAI (GPT-3.5-Turbo & GPT-5-mini)** — language models powering the agents
- 🗃️ **Supabase** — database backend for products, orders, refunds, complaints, and support tickets
- 🧠 **n8n Memory Buffer** — per-agent conversation memory for context-aware responses
- 🔀 **Switch Node** — intent-based routing between agents

---

## 🌐 Live Demo

### 🎥 Demo Video

https://github.com/user-attachments/assets/3c35e9d2-8261-46c9-ac10-7c348ce8dcb5

---

## 🚀 How It Works

1. A customer sends a message through the chat trigger.
2. The **Supervisor Agent** reads the message and classifies it into a single intent.
3. A **Switch node** routes the request to the matching specialized agent.
4. The specialized agent queries (or updates) its dedicated Supabase table using its own tool.
5. Each agent maintains its own short-term memory for context within the conversation.
6. The agent's response is returned to the customer directly in the chat.

---

## ✨ Features

- 🧭 Intent-based routing via a dedicated Supervisor Agent
- 🛍️ Product recommendations and inquiry handling
- 📦 Automatic Order ID extraction and tracking
- 💳 Refund status lookup and refund request creation
- ⚠️ Smart complaint handling — creates new complaints or updates existing ones based on context
- 🧑‍💼 Human support escalation with ticket creation
- 🧠 Independent conversation memory per agent
- 🗃️ Supabase-backed data for every agent

---

## ⚙️ Setup / Import Instructions

1. Import `E-commerce_Project.json` into your n8n instance (**Workflows → Import from File**).
2. Set up your own credentials:
   - **OpenAI API** credential for the chat models
   - **Supabase API** credential for all database tool nodes
3. Create the following tables in your Supabase project (or adjust the table names in each tool node to match your own schema):
   - `Product Inquiry`
   - `Order Tracking Agent`
   - `Refund Agent`
   - `Customer Complaint Agent`
   - `Human Support Agent`
4. Activate the workflow and test it using the Chat Trigger.

> ⚠️ **Note:** This repository does not include any API keys or credentials. You must connect your own OpenAI and Supabase accounts after importing the workflow.

---

## 🖥️ Workflow Screenshot

![Multi-Agent Workflow](workflow-screenshot.png)

---

## 👩‍💻 Developed By

**Maryam Illahi**

AI Automation Developer | n8n Developer | AI Agents | Multi-Agent Systems | Workflow Automation

⭐ If you like this project, feel free to give it a **Star**.
