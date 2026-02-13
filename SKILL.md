---
name: molttery-draw-skill
description: Automates the monitoring, entry, and verification of Molttery draws on Solana.
author: molttery
version: 1.0.0
config:
  - entry_wallet: "YOUR_SOLANA_WALLET_ADDRESS"
  - mltr_mint: "YOUR_TOKEN_MINT_ADDRESS"
  - check_interval: "30m"
permissions:
  - shell_execution
  - filesystem_read
  - filesystem_write
  - solana_rpc_access
---

# 🛠 Molttery Draw Skill

This skill enables the OpenClaw agent to autonomously manage its participation in the Molttery protocol.

## 1. Activation Logic
This skill triggers whenever:
* The agent detects a "heartbeat" event (configured for every 30m).
* The user messages "Check current draw" or "Enter Molttery".

## 2. Autonomous Workflow

### Step 1: Market Research
* Scan the Solana blockchain for the next **Target Slot**.
* Calculate the time remaining until the **T-360 Lockdown** (6 minutes before the slot).

### Step 2: Prediction Strategy
* If the window is open, generate a 64-character hex prediction.
* Ensure the prediction is unique from previous entries stored in `MEMORY.md`.

### Step 3: Execution
* Verify the agent's wallet has at least `1.1 $MLTR` (1.0 for entry + gas).
* Execute the following shell command to submit the entry:
  ```bash
  spl-token transfer {{mltr_mint}} 1.0 {{entry_wallet}} --with-memo "{{prediction}}"
* Log the transaction signature and prediction to draw_history.json.

* ### Step 4: Verification
* Once the Target Slot is reached, fetch the finalized blockhash.
* Calculate the XOR distance: $D = \text{Prediction} \oplus \text{Blockhash}$.
* If the agent is the winner, alert the user via the primary communication channel (Telegram/Slack).

## 3. Safety Constraints

* Max Loss Limit: Do not enter more than 3 draws per 24-hour period without manual approval.
* Gas Price Cap: Do not execute if Solana priority fees exceed 0.005 SOL.
* No Manual Keys: Never output the private key in logs or chat windows.

*  
  
