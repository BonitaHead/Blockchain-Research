# Bitcoin Transaction Analysis — Case Study 01

## Objective

This case study demonstrates a structured methodology for examining a publicly observable Bitcoin transaction.

The objective is to move beyond describing Bitcoin's transaction model and demonstrate how an analyst can:

- Identify transaction components
- Examine inputs and outputs
- Calculate transaction value and fees
- Examine UTXO relationships
- Determine confirmation status
- Document observable patterns
- Distinguish blockchain evidence from analytical inference
- Identify limitations of on-chain analysis

No private keys, seed phrases, or personally identifying information are used.

---

## 1. Transaction Selection

### Transaction ID

[INSERT TXID]

### Explorer

Mempool.space

### Transaction URL

[INSERT MEMPOOL TRANSACTION URL]

### Date Analyzed

[INSERT DATE]

### Reason for Selection

This transaction was selected as a publicly observable example for demonstrating Bitcoin transaction-analysis methodology.

---

## 2. Transaction Overview

| Metric | Observation |
|---|---|
| Transaction ID | [TXID] |
| Confirmation Status | [Confirmed / Unconfirmed] |
| Block Height | [HEIGHT] |
| Number of Inputs | [NUMBER] |
| Number of Outputs | [NUMBER] |
| Total Input Value | [BTC] |
| Total Output Value | [BTC] |
| Transaction Fee | [BTC] |
| Fee Rate | [sat/vB] |
| Transaction Size | [BYTES] |
| Virtual Size | [vB] |

---

## 3. Input Analysis

Each Bitcoin transaction input references an output created by a previous transaction.

### Input Summary

| Input | Previous TXID | Output Index | Value |
|---|---|---:|---:|
| 1 | [TXID] | [VOUT] | [BTC] |
| 2 | [TXID] | [VOUT] | [BTC] |

### Observations

The transaction contains [NUMBER] input(s).

The combined value of the inputs is approximately:

**[VALUE] BTC**

The inputs represent previously created UTXOs that are being consumed by this transaction.

Bitcoin's transaction model requires the referenced outputs to be available for spending; an output can only be spent once. 

---

## 4. Output Analysis

### Output Summary

| Output | Value | Script / Address Type | Status |
|---|---:|---|---|
| 0 | [BTC] | [TYPE] | [Spent / Unspent] |
| 1 | [BTC] | [TYPE] | [Spent / Unspent] |

### Observations

The transaction creates [NUMBER] outputs.

The combined output value is approximately:

**[VALUE] BTC**

The outputs represent newly created UTXOs until they are subsequently spent.

---

## 5. Transaction Fee

Bitcoin transaction fees can be determined from the difference between the total value of the inputs and the total value of the outputs.

### Calculation

```text
Transaction Fee =
Total Input Value - Total Output Value
