# FraudShield-AI
Real-Time Financial Fraud Intelligence System using explainable risk scoring and fraud-ring analysis.

# 🛡️ FraudShield AI

### Real-Time Financial Fraud Intelligence

FraudShield AI is an interactive financial fraud intelligence prototype developed for **HNX26PSI04 – Real-Time Financial Fraud Intelligence**.

The system combines **explainable risk scoring, transaction monitoring, relationship analysis, and fraud-ring visualization** to help identify suspicious financial activity and investigate potentially coordinated fraud.

---

## 🚨 Problem Statement

Financial fraud is becoming increasingly complex because fraudulent activity is often not limited to a single transaction or account.

A transaction may appear normal when viewed independently, but relationships between:

- Accounts
- Devices
- IP addresses
- Destinations
- Merchants
- Transaction timing
- Behaviour patterns

can reveal coordinated fraudulent activity.

Traditional transaction-level monitoring may therefore miss the larger network behind suspicious transactions.

---

## 💡 Our Solution

FraudShield AI provides an interactive intelligence dashboard that moves beyond simply classifying a transaction as "fraud" or "not fraud."

The system follows this workflow:

Transaction
↓
Risk Analysis
↓
Explainable Risk Score
↓
Suspicious Indicators
↓
Relationship Analysis
↓
Potential Fraud Ring
↓
Recommended Action

Each suspicious transaction is given a risk score and an explanation of the factors contributing to that score.

---

## ✨ Key Features

### 1. Real-Time Transaction Monitoring

The dashboard continuously simulates incoming financial transactions and displays:

- Transaction ID
- Account ID
- Transaction amount
- Risk score
- Risk level
- Recommended action

Transactions can be searched, filtered and sorted by risk or transaction amount.

---

### 2. Explainable Risk Scoring

Instead of simply showing a fraud prediction, FraudShield AI explains **why** a transaction is considered suspicious.

Example indicators include:

- Shared suspicious device
- Common destination account
- High transaction velocity
- Shared network identity
- New device
- New destination
- Unusual location
- Behaviour anomaly
- Graph correlation

Risk scores range from **0–100**.

Risk levels:

| Score | Risk Level |
|---|---|
| 0–39 | LOW |
| 40–69 | MEDIUM |
| 70–84 | HIGH |
| 85–100 | CRITICAL |

---

### 3. Fraud Ring Detection

Fraud is often coordinated across multiple accounts.

FraudShield AI represents relationships between accounts and shared infrastructure through an interactive connection graph.

Example:

Account → Shared Device → Account
   ↓
Shared IP
   ↓
Destination Account

This allows investigators to look beyond an individual transaction and inspect connected entities.

---

### 4. Account Risk Intelligence

The system provides account-level information such as:

- Account risk score
- Fraud-ring membership
- Connected infrastructure
- Behaviour indicators
- Suggested action

This helps analysts investigate suspicious accounts as part of a larger network.

---

### 5. Fraud Ring Visualization

The prototype currently demonstrates multiple fraud-ring scenarios:

- **FR-003 – Coordinated Transfer Ring**
- **FR-002 – Merchant Collusion Pattern**
- **FR-001 – Device Sharing Cluster**

Each ring contains connected accounts and shared infrastructure.

---

### 6. Interactive Transaction Testing

Users can manually test a transaction by providing:

- Account ID
- Transaction amount
- Device type
- Destination type
- Transaction velocity
- Location

The system calculates a risk score and adds the resulting transaction to the live monitoring dashboard.

---

### 7. Suspicious Event Simulation

The dashboard includes an **"Inject Suspicious Event"** feature.

This simulates a high-risk transaction involving characteristics such as:

- Shared device
- Common destination
- High transaction velocity
- Graph correlation

This allows the system to demonstrate how a suspicious event can enter the monitoring workflow.

---

## 🧠 Risk Scoring Logic

The current prototype uses an **explainable rule-based scoring engine**.

Example signals include:

| Indicator | Score Contribution |
|---|---:|
| Transaction amount above threshold | +12 |
| New device | +13 |
| Shared suspicious device | +35 |
| New destination | +10 |
| Known fraud-ring destination | +30 |
| High transaction velocity | +18 |
| Unusual location | +12 |
| Device + fraud destination correlation | +10 |

The final score is capped at 99 in the interactive transaction simulator.

The purpose of this approach is to make the reasoning behind each alert transparent and understandable.

---

## 🏗️ Current Architecture

The current hackathon prototype is implemented as a self-contained web application.

```text
                  ┌─────────────────────┐
                  │ Simulated Transaction│
                  │       Stream         │
                  └──────────┬──────────┘
                             ↓
                  ┌─────────────────────┐
                  │  Risk Scoring Engine │
                  │  Rule-Based Analysis │
                  └──────────┬──────────┘
                             ↓
                  ┌─────────────────────┐
                  │ Explainable Risk     │
                  │ Score + Evidence     │
                  └──────────┬──────────┘
                             ↓
              ┌──────────────┴──────────────┐
              ↓                             ↓
      ┌───────────────┐             ┌───────────────┐
      │ Account Risk  │             │ Relationship  │
      │ Intelligence  │             │ Graph         │
      └───────┬───────┘             └───────┬───────┘
              │                             │
              └──────────────┬──────────────┘
                             ↓
                    ┌──────────────────┐
                    │ Fraud Ring /     │
                    │ Investigation    │
                    └────────┬─────────┘
                             ↓
                    Recommended Action
