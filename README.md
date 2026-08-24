# 🤖 AI E-Commerce Multi-Agent System

An AI-powered multi-agent e-commerce customer support system built with **n8n, OpenAI, and Supabase**.

The system uses a **Supervisor Agent** to understand the customer's request and automatically route it to the appropriate specialized AI agent.

## 🚀 Project Overview

This project demonstrates a multi-agent architecture for handling different e-commerce customer requests.

Instead of using one AI agent for everything, the system uses multiple specialized agents, each responsible for a specific customer-support task.

The Supervisor Agent classifies the customer's current message and routes it to the correct employee agent.

## 🧠 AI Agents

### 👨‍💼 Supervisor Agent

Classifies customer requests into one of five intents:

* Product Inquiry
* Order Tracking
* Refund
* Complaint
* Human Support

It then routes the request to the appropriate specialized agent.

### 🛍️ Product Inquiry Agent

Handles:

* Product recommendations
* Product prices
* Product availability
* Product features
* Product comparisons
* Purchase assistance

The agent uses the product database to provide product-related information.

### 📦 Order Tracking Agent

Handles:

* Order status
* Shipping information
* Tracking numbers
* Estimated delivery dates

Customers can provide an Order ID, which the agent uses to retrieve the relevant order information.

### 💰 Refund Agent

Handles:

* Refund status
* Refund amount
* Refund method
* Refund reason
* Refund requests

The agent checks the refund database before providing information.

### ⚠️ Complaint Agent

Handles:

* Damaged products
* Wrong products
* Defective products
* Complaint details
* Complaint status
* Complaint updates
* Complaint escalation

The agent can also update complaint status when requested.

### 👩‍💻 Human Support Agent

Handles requests for human assistance and support escalation.

It can check existing support requests, create new requests, and update support status.

## 🔄 How It Works

Customer Message
       ↓
Supervisor Agent
       ↓
Intent Classification
       ↓
      Switch
       ↓
 ┌─────┬────────┬────────────┬───────────┐
 ↓     ↓        ↓            ↓           ↓
Product Refund Order      Complaint   Human
Inquiry       Tracking                 Support
 ↓     ↓        ↓            ↓           ↓
          Supabase Database

## 🗄️ Database

The system uses **Supabase** to store and retrieve e-commerce customer and operational data.

The workflow includes database tools for:

* Product information
* Order tracking
* Refund information
* Customer complaints
* Human support requests

## 🛠️ Technologies Used

* **n8n** — Workflow automation and agent orchestration
* **OpenAI** — AI language models
* **Supabase** — Database and data management
* **AI Agents** — Specialized customer-support agents
* **Switch / Routing Logic** — Intent-based agent routing
* **Simple Memory** — Conversation memory for selected agents

## ⭐ Key Features

* Multi-agent AI architecture
* Supervisor-based intent classification
* Specialized customer-support agents
* Product inquiry handling
* Order tracking
* Refund management
* Complaint management
* Human support escalation
* Supabase database integration
* Automated agent routing
* Conversation memory

## 📁 Project Structure

ai-ecommerce-multi-agent/
│
├── E-commerce Project.json
└── README.md

## 📌 Example Requests

The system can handle requests such as:

"I want to buy a laptop"
"Recommend a mobile"
"Track my order ORD001"
"I want a refund"
"My laptop is damaged"
"Mark my complaint as Closed"
"I want to talk to a human"


Each request is automatically routed to the appropriate specialized agent.

## 🎯 Project Goal

The goal of this project is to demonstrate how a **multi-agent AI system** can be used to automate different areas of e-commerce customer support while keeping each AI agent focused on a specific responsibility.

## 👩‍💻 Author

**Maryam Illahi**

AI Automation Specialist | AI Agents Developer | n8n Workflow Developer
