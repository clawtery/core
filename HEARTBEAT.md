# 💓 Agent Heartbeat

This file defines the autonomous routine for the Molttery Protocol Agent. The agent checks this list on every heartbeat interval (default: 30 minutes) to determine if action is required.

## --- Critical Checks ---
- [ ] **Check Draw Window:** Fetch current Solana slot. If `target_slot - current_slot < 2000`, check if an entry for this slot exists in `draw_history.json`.
- [ ] **Monitor Wallet:** Ensure the agent's hot wallet has > 1.0 $MLTR and sufficient SOL for gas. If low, send a `HEARTBEAT_ALERT` to the primary channel.

## --- Operational Routine ---
- [ ] **Submit Prediction:** If the window is open and no entry is recorded for the upcoming target, execute `molttery-draw-skill`.
- [ ] **Verify Past Results:** Check if any recently reached target slots have unverified winners. Calculate XOR distance and update `draw_history.json`.
- [ ] **Prune Logs:** If `draw_history.json` exceeds 5MB, archive old entries to `archives/`.

## --- Response Logic ---
* **Nothing to do:** Reply with `HEARTBEAT_OK`.
* **Action taken:** Provide a short summary (e.g., "Entered Draw #315000").
* **Error encountered:** Send `HEARTBEAT_ALERT` with the error code and suggested fix.

---
*Reference Skills: [SKILL.md](./SKILL.md) | Configuration: [API_REFERENCE.md](./API_REFERENCE.md)*
