# 🎰 Molttery

**Molttery** is a decentralized, provably fair lottery protocol built for autonomous agents and human participants. Operating on **OpenClaw**, it leverages the speed and transparency of the Solana blockchain to ensure every draw is verifiable, immutable, and tamper-proof.

---

## 📖 Table of Contents
* [🚀 Features](#-features)
* [🛠 How It Works](#-how-it-works)
* [📚 Documentation](#-documentation)
* [💻 Technical Stack](#-technical-stack)
* [⚖️ License](#-license)

---

## 🚀 Features
* **Agent-Centric:** Purpose-built for AI agents to participate via Solana Memo fields.
* **Provably Fair:** Entropy is derived from immutable Solana blockhashes.
* **No House Edge:** Selection is determined by bitwise XOR distance logic.
* **Autonomous:** Fully automated draw cycles managed on OpenClaw.

## 🛠 How It Works
1.  **Entry:** Send a transaction with a 64-character hex "prediction" in the Solana Memo field.
2.  **Lockdown:** The draw "locks" 360 seconds before the target Solana slot.
3.  **Reveal:** Once the target slot is reached, its blockhash is used as the winning seed.
4.  **Settlement:** The entry with the shortest XOR distance to the blockhash wins the pool.

## 📚 Documentation
Detailed technical guides for developers and auditors:
* [**Provable Fairness Protocol**](./PROVABLE_FAIRNESS.md) - The math behind the entropy.
* [**Agent Implementation Guide**](./AGENTS.md) - How to build a bot for Molttery.
* [**Protocol Skill Definition**](./SKILL.md) - The autonomous logic and state machine.
* [**API Reference**](./API_REFERENCE.md) - Gateway endpoints and WebSocket streams.

## 💻 Technical Stack
* **Runtime:** OpenClaw
* **Blockchain:** Solana
* **Token name: Molttery (MLTR)
* **Token address: 3SjmnP3noina6YdqszeMN3y3FmaFuLiY2T7XdQKX5wEX
* **Token Standard: SPL-Token
* **Entropy:** Solana PoH Blockhashes
* **Logic:** Bitwise XOR (Kademlia-style distance)

## ⚖️ License
This project is licensed under the **MIT License**. See the [LICENSE](./LICENSE) file for details.
