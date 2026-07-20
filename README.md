# Custom SMTP Mail Server

A lightweight SMTP server implementing email reception, MIME parsing, and persistent mailbox storage using AWS DynamoDB.

---

## Overview

This project demonstrates the core components of an SMTP mail server. It accepts incoming email over the SMTP protocol, validates recipients, parses MIME messages, and persists email metadata and content to DynamoDB for later retrieval.

Rather than relying on traditional relational storage, the server stores mail in a NoSQL database and retrieves messages through indexed mailbox queries.

---

## Highlights

- SMTP server implementation using Node.js
- MIME email parsing
- Recipient validation for custom domains
- Persistent email storage using AWS DynamoDB
- Indexed mailbox retrieval
- Simple mailbox query interface

---

## Architecture

```
SMTP Client
      │
      ▼
 SMTP Server
      │
Recipient Validation
      │
MIME Parser
      │
Email Processing
      │
AWS DynamoDB
      │
Mailbox Retrieval
```

---

## Tech Stack

### Backend

- Node.js

### Protocols

- SMTP

### Email Processing

- smtp-server
- mailparser

### Cloud

- AWS DynamoDB

---

## Features

### SMTP Email Reception

The server accepts incoming SMTP connections and processes standard email transactions.

---

### Recipient Validation

Only recipients belonging to the configured domain are accepted, preventing unauthorized mail delivery.

---

### MIME Parsing

Incoming email messages are parsed into structured fields including:

- Sender
- Recipient
- Subject
- Body

---

### Persistent Storage

Parsed emails are stored in DynamoDB with metadata including:

- Sender
- Receiver
- Subject
- Message Body
- Timestamp

---

### Mailbox Retrieval

Emails can be retrieved by recipient using DynamoDB secondary indexes.

---

## Email Processing Flow

```
SMTP Client
      │
      ▼
Connect
      │
MAIL FROM
      │
RCPT TO
      │
Recipient Validation
      │
DATA
      │
Parse MIME Message
      │
Store in DynamoDB
      │
Mailbox Query
```

---

## Engineering Decisions

### SMTP Protocol

Using SMTP provides a realistic implementation of how mail servers receive email before forwarding it to storage.

---

### MIME Parsing

Rather than processing raw SMTP payloads manually, MIME parsing converts incoming messages into structured email objects.

---

### DynamoDB Storage

DynamoDB provides a simple schema for storing email documents while enabling efficient mailbox lookups through secondary indexes.

---

### Domain Validation

Restricting accepted recipients to a specific domain simulates mail server ownership and prevents accepting mail for unknown domains.

---

## Running Locally

### Prerequisites

- Node.js
- AWS Account
- DynamoDB Table

Install dependencies

```bash
npm install
```

Configure environment variables

```env
AWS_ACCESS_KEY=...
AWS_SECRET_ACCESS_KEY=...
```

Start the SMTP server

```bash
node server.js
```

The server listens on:

```
Port 25
```

---

## Future Improvements

- IMAP server implementation
- SMTP authentication
- TLS support
- Mailbox management
- Email attachments
- Spam filtering
- DKIM and SPF validation
- Multi-domain support

---

## License

This project is intended for learning and demonstration purposes.
