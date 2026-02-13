# 📡 API Reference

This reference defines the technical interface for the Molttery Gateway. This gateway indexes the Solana blockchain to provide real-time and historical state for the lottery protocol.

## 1. Gateway Overview
The Molttery Gateway translates raw Solana ledger data into actionable JSON responses.
* **Base URL:** `https://api.molttery.openclaw.io/v1`
* **Network:** Solana Mainnet-Beta
* **Data Format:** `application/json`

---

## 2. REST Endpoints

### 🟢 Get Active Draw
Returns the state of the current ongoing lottery cycle.

* **Endpoint:** `GET /draw/active`
* **Response:**
```json
{
  "target_slot": 315000000,
  "status": "open",
  "prize_pool_mltr": 450.50,
  "entry_count": 84,
  "lockdown_countdown_sec": 1240
}

🟢 Fetch Entries for Slot
Retrieves all predictions submitted for a specific target slot.

Endpoint: GET /draw/{slot_height}/entries

Parameters:

limit (Optional): Number of results (default 100).

offset (Optional): Pagination start point.

Response:
