# Clinic AI Telegram Bot

An intelligent, fully automated Telegram bot designed specifically for medical clinics and healthcare centers. Built using n8n, Google Gemini, and MS SQL Server, this bot acts as a 24/7 virtual medical receptionist.

## Project Overview

This project automates clinic-patient interactions on Telegram. It handles routine inquiries, books appointments directly into a secure database, and seamlessly routes complex medical situations to human staff, ensuring zero lost leads and reduced workload for clinic administration.

## Core Features

- **24/7 Automated Support:** Instant replies to patient inquiries regarding clinic hours, location, consultation fees, and pre-examination instructions.
- **Smart Appointment Booking:** Conversational booking system that extracts patient details (Name, Phone, Preferred Time) and registers them directly into the clinic's MS SQL Server database.
- **RAG Implementation (Knowledge Base):** Utilizes Google Gemini to process PDF documents and clinic data, providing accurate answers based solely on the clinic's provided context.
- **Human Escalation:** Automatically detects urgent cases or complex requests, shifts the chat status, and alerts the human receptionist or doctor to take over the Telegram chat.
- **Context Memory:** Maintains chat history context to provide a natural, human-like conversation flow.

## Tech Stack & Architecture

- **Workflow Automation:** n8n
- **Messaging Integration:** Telegram Bot API
- **Artificial Intelligence:** Google Gemini (LLM & Embeddings)
- **Database:** MS SQL Server
- **Vector Storage (RAG):** Supabase (or internal n8n memory/vector store)

## How It Works

1. **Message Reception:** A patient sends a message to the clinic's Telegram Bot. The Telegram API sends the payload to an n8n webhook (or via n8n Telegram Trigger).
2. **Intent Parsing:** The AI evaluates if the user is asking a general question, trying to book an appointment, or requesting to speak with a human.
3. **Database Operations:** For bookings, n8n queries SQL Server to check availability and inserts the new appointment record.
4. **Response Generation:** Gemini formulates a polite, professional Arabic response based on the system prompt and clinic data.
5. **Delivery:** The response is sent back to the patient via the Telegram Bot instantly.

## Installation & Setup

1. Message `@BotFather` on Telegram to create a new bot and get your API Token.
2. Import the provided `n8n-workflow.json` file into your n8n instance.
3. Add your Telegram Bot Token to the Telegram credentials in n8n.
4. Set up the MS SQL Server database and execute the provided `schema.sql` to create the required tables.
5. Add your Google Gemini API key to the n8n AI node credentials.
6. Update the system prompt with your specific clinic details.

## Use Cases

- Dental Clinics
- Specialized Medical Centers
- Physical Therapy Clinics
- General Practitioners
