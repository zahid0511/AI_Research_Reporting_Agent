
# System Architecture

## Overview

The system uses n8n as the central orchestration layer to coordinate web research, AI report generation, and email delivery.

## Components

### 1. Research Form
Collects the research topic and research focus.

### 2. Tavily Search
Retrieves relevant web pages and source content.

### 3. Prepare Research
Filters results and extracts titles, URLs, relevance scores, and content.

### 4. Build Gemini Prompt
Combines the research topic and retrieved sources into a structured prompt.

### 5. Google Gemini
Generates the research report using the supplied research material.

### 6. Extract Research Report
Extracts the generated text and formats it into HTML.

### 7. Gmail
Sends the generated research report to the recipient.

## Data Flow

User Input → Web Search → Source Processing → Prompt Construction → AI Generation → Report Formatting → Email Delivery

## Security

Credentials are maintained using n8n's credential management system. API secrets are not included in the workflow export.
