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

**Not captured in the source data provided for this analysis.**

### Explorer

Mempool.space

### Transaction URL

The source records link the addresses to Mempool.space. The transaction-level URL should be added when the TXID is confirmed.

### Date Analyzed

August 14, 2026

### Reason for Selection

This transaction was selected as a publicly observable example for demonstrating Bitcoin transaction-analysis methodology, including input/output analysis, UTXO tracking, change-output identification, and cautious address attribution.

---

## 2. Transaction Overview

| Metric | Observation |
|---|---|
| Transaction ID | Not captured in supplied data |
| Confirmation Status | Address data shows confirmed UTXOs for analyzed outputs |
| Block Height | Not captured in supplied data |
| Number of Inputs | 1 supplied input |
| Number of Outputs | 15 supplied outputs |
| Total Input Value | **17.13205820 BTC** |
| Total Output Value | **17.13202221 BTC** |
| Transaction Fee | **0.00003599 BTC** (3,599 satoshis) |
| Fee Rate | Not captured in supplied data |
| Transaction Size | Not captured in supplied data |
| Virtual Size | Not captured in supplied data |

### Fee calculation

```text
17.13205820 BTC - 17.13202221 BTC
= 0.00003599 BTC
= 3,599 satoshis
```

The fee calculation is based on the complete set of input/output values supplied for this case study.

---

## 3. Input Analysis

### Input Summary

| Input | Previous Output Address | Previous Output Type | Value |
|---|---|---|---:|
| 1 | `bc1q8pmuc2v0cku2ty0rfxp2jyvrhv6lpsjzq9y6s8` | V0_P2WPKH | **17.13205820 BTC** |

### Witness Data

The supplied witness contains:

- DER-encoded ECDSA signature
- Compressed public key: `023e86a944b9cff6bea3e61d3594820cacbfb122b817934f981256b2bc4e6b8504`

### Previous Output Script

```text
OP_0
OP_PUSHBYTES_20 3877cc298fc5b8a591e34982a91183bb35f0c242
```

Previous output type: **V0_P2WPKH**

### Sequence

```text
nSequence = 0xfffffffd
```

The sequence value is below `0xffffffff`, so the input is not using the final sequence value. This is compatible with signaling conditions associated with opt-in Replace-by-Fee (RBF), although the sequence value alone does not establish that an RBF replacement actually occurred.

---

## 4. Output Analysis

The supplied transaction data contains 15 outputs.

| Output | Address | Value (BTC) | Type |
|---:|---|---:|---|
| 0 | `bc1q3lf0lmnkd5rclu3wtwzt3s5qmjedv36dxr3skj` | 0.00641491 | V0_P2WPKH |
| 1 | `bc1qawq9ge6wxfmmlycwvjrgdhgym2x3y8gtzhl7pf` | 0.00234207 | V0_P2WPKH |
| 2 | `bc1q0q33uhuvrnt8yz0emzw3h757n2tuapmrrv4q6u` | **0.98557605** | V0_P2WPKH |
| 3 | `bc1q0tanq00x7n8597aez6vtectthc76uwjlx6wx0m` | 0.00163868 | V0_P2WPKH |
| 4 | `bc1qelkff3k75a5guy4q8p7kfz55ma4yx3waqzz5hd` | 0.00155125 | V0_P2WPKH |
| 5 | `bc1qaux77jqvjy5af0v4pjmyalz4m489h6ktwdyd3a` | 0.00153161 | V0_P2WPKH |
| 6 | `bc1qjzqzz8fshsdaqdhavkm3qtxncsmvv5yldzq8xp` | 0.03093259 | V0_P2WPKH |
| 7 | `bc1qtta5fpur9k50tkwh5nshnmj00f7zr9lg5lrn5a` | 0.09279459 | V0_P2WPKH |
| 8 | `bc1q2aagunyfyf7aks7yxwayqlwghwl7fhq6wud4t7` | 0.00078122 | V0_P2WPKH |
| 9 | `bc1qqdv4c44z2g4vslrday6ktzm5wlec2fra4gng5w` | 0.00092174 | V0_P2WPKH |
| 10 | `bc1qe9t28g6r7zypzvnjv569h7qczm64ejna8zpecs` | 0.01802719 | V0_P2WPKH |
| 11 | `bc1q9j0k9z39q9z09c3jaxel6zn5ycfcqelgq4x33h` | 0.01918802 | V0_P2WPKH |
| 12 | `bc1qjzqzz8fshsdaqdhavkm3qtxncsmvv5yldzq8xp` | **0.01543178** | V0_P2WPKH |
| 13 | `3DmKGgKdGkMrxp6wbAMCrV1SeXrtViguXy` | 0.00079023 | P2SH |
| 14 | `bc1q8pmuc2v0cku2ty0rfxp2jyvrhv6lpsjzq9y6s8` | **15.95410028** | V0_P2WPKH |

### Total output value

**17.13202221 BTC**

---

## 5. Change / Self-Return Analysis

The most significant structural observation is that the original input address also receives a large output:

```text
Input:
17.13205820 BTC
        |
        +---- 15.95410028 BTC --> bc1q8pmuc2v0cku2ty0rfxp2jyvrhv6lpsjzq9y6s8
```

The difference between the input and the same-address output is:

```text
17.13205820 - 15.95410028
= 1.17795792 BTC
```

The 15.95410028 BTC output is therefore **consistent with a change/self-return output**, but this is an analytical inference rather than proof that the same entity controls both sides of the transaction.

Address reuse can provide useful behavioral evidence, but Bitcoin's public ledger does not by itself establish real-world identity or ownership.

---

## 6. Recipient Address Analysis

### 6.1 `bc1q0q33uhuvrnt8yz0emzw3h757n2tuapmrrv4q6u`

Mempool address data supplied for this investigation shows:

- Confirmed balance: **0.98557605 BTC**
- Total received: **0.98557605 BTC**
- Confirmed UTXOs: **1**
- Pending UTXOs: **0**
- Address type: **P2WPKH**
- Transactions shown: **1 of 1**

The address therefore appears to be a **single-use recipient with the full received amount still unspent** at the time of observation.

Analytical classification:

> **Single-use / dormant recipient — attribution not established.**

No exchange, individual, organization, or other real-world entity should be assigned to this address without additional evidence.

---

### 6.2 `bc1qjzqzz8fshsdaqdhavkm3qtxncsmvv5yldzq8xp`

This address receives two separate outputs in the same transaction:

| Output | Value |
|---|---:|
| First output | 0.03093259 BTC |
| Second output | 0.01543178 BTC |
| **Combined** | **0.04636437 BTC** |

Mempool address data supplied for this investigation shows:

- Confirmed balance: **0.04636437 BTC**
- Total received: **0.04636437 BTC**
- Confirmed UTXOs: **2**
- Pending UTXOs: **0**
- Address type: **P2WPKH**

Both outputs remain represented as separate UTXOs.

Analytical classification:

> **Repeated-output recipient requiring further investigation.**

The duplicate destination is noteworthy, but it does not by itself establish the purpose of the transaction or the identity of the controller.

---

## 7. Transaction Flow

```text
                         17.13205820 BTC
                                |
                                v
                 bc1q8pmuc2v0cku2ty0rfxp2jyvrhv6lpsjzq9y6s8
                                |
             +------------------+-------------------+
             |                                      |
             v                                      v
     15.95410028 BTC                         ~1.178 BTC
     same-address output                    distributed
     (likely change)                        across recipients
             |                                      |
             |                 +--------------------+------------------+
             |                 |                                       |
             |                 v                                       v
             |        bc1q0q33...                              bc1qjzqz...
             |        0.98557605 BTC                            0.04636437 BTC
             |        1 UTXO                                    2 UTXOs
             |        unspent                                   unspent
             |
             +---- remaining smaller outputs

Fee: 0.00003599 BTC (3,599 satoshis)
```

---

## 8. Observable Behavioral Patterns

### Pattern 1 — Large same-address return

A 15.95410028 BTC output returns to the address that supplied the 17.13205820 BTC input. This is strongly consistent with change behavior, but ownership is not proven.

### Pattern 2 — Large single recipient output

The transaction sends **0.98557605 BTC** to `bc1q0q33...`, which subsequently remains unspent according to the supplied address snapshot.

### Pattern 3 — Duplicate destination within one transaction

The same `bc1qjzqz...` address receives two outputs totaling **0.04636437 BTC**. The two outputs remain separate UTXOs.

### Pattern 4 — Mixed output types

The transaction uses primarily native SegWit P2WPKH outputs and includes one P2SH output (`3DmKG...`).

### Pattern 5 — Low transaction fee relative to value moved

The transaction moves more than 17 BTC while paying only 3,599 satoshis in fees based on the supplied input/output values.

---

## 9. Analytical Interpretation

The transaction can provisionally be described as:

> **A single-input, multi-output Bitcoin transaction featuring a substantial same-address return/change-like output and multiple smaller recipient outputs.**

The available evidence supports identifying transaction structure and UTXO behavior, but it does **not** support assigning a real-world identity or entity to any address.

Potential interpretations that require further investigation include:

1. Change/self-return combined with payments to multiple recipients.
2. Structured distribution of BTC to multiple addresses.
3. Consolidation or operational wallet activity.
4. Other wallet-management behavior not identifiable from this transaction alone.

No one interpretation should be treated as established without tracing the related addresses and transaction history.

---

## 10. Limitations

This analysis is based on the transaction and address information supplied from Mempool.space.

The following information was not captured and should be added before finalizing the case study:

- Transaction ID (TXID)
- Block height
- Exact confirmation count
- Transaction size
- Virtual size (vbytes)
- Fee rate
- Full previous transaction reference / output index
- Forward transaction history for recipient addresses

Most importantly, **address ownership and real-world identity are not established by this analysis**.

---

## 11. Follow-Up Investigation

The next investigative steps are:

1. Obtain and record the TXID.
2. Record the block height and confirmation count.
3. Trace `bc1q0q33...` forward when its 0.98557605 BTC is spent.
4. Trace `bc1qjzqz...` forward and analyze both UTXOs independently.
5. Trace the 15.95410028 BTC same-address output to determine whether and when it is spent.
6. Examine the previous transaction funding the 17.13205820 BTC input.
7. Check whether any recipient addresses form clusters through subsequent common-input or transaction-history relationships.
8. Preserve all observations separately from attribution hypotheses.

---

## 12. Case Study Classification

**Blockchain:** Bitcoin  
**Analysis Type:** Transaction / UTXO / Address Behavior  
**Primary Method:** On-chain transaction analysis  
**Attribution Level:** Unattributed  
**Evidence Level:** Direct blockchain observations with clearly labeled analytical inferences  
**Status:** **Active investigation**

---

## Source

Mempool.space address and transaction data supplied during the investigation on August 14, 2026.
