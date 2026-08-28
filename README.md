# 🤖 AI Multi-Agent E-Commerce Support System

A supervisor-based multi-agent AI system built in **n8n** that automates end-to-end e-commerce customer support — product inquiries, order tracking, refunds, complaints, and human escalation — using a team of specialized AI agents that work together like a real support team.

---

## 📌 Project Overview

Instead of a single chatbot trying to handle every type of request, this system uses a **Supervisor Agent** that reads each customer message, classifies its intent, and routes it to the correct **specialized employee agent** — just like a real shop supervisor assigning tasks to the right department.

Each specialized agent has its own role, its own instructions, and its own connection to a **Supabase** database table, so it only ever works within its area of responsibility.

---

## 🧠 Multi-Agent Architecture
