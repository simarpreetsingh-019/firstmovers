
# SIP-6: Redesign of the `StakedSui` Object

## 🔍 Overview
SIP-6 proposes a comprehensive redesign of the `StakedSui` object in the Sui blockchain to enhance **flexibility**, **clarity**, and **developer utility** in staking. This new structure provides richer metadata and supports smart contract interactions, paving the way for advanced DeFi and staking use cases.

---

## 🧱 What’s the Problem?

Prior to SIP-6:
- The `StakedSui` object had **limited metadata**.
- Hard to trace or audit staked assets programmatically.
- Not friendly to **smart contract-based staking logic**.
- Lacked key fields like validator, epoch, and lock info.

---

## 🛠️ Proposed Redesign

```rust
struct StakedSui has key {
    id: UID,
    validator_address: SuiAddress,
    pool_staking_epoch: u64,
    principal: Balance,
    sui_token_lock: Option<Lock>,
}
```

### 🔑 Field Explanations
- `id`: Unique identifier for the stake object.
- `validator_address`: The validator being delegated to.
- `pool_staking_epoch`: Epoch when the stake becomes active.
- `principal`: Amount of SUI staked.
- `sui_token_lock`: Optional lock to prevent early withdrawal.

---

## 📈 Why It Matters

- ✅ **Greater Transparency** – Track who staked what, with whom, and when.
- ✅ **Smart Contract Compatible** – Stake from DAOs or dApps.
- ✅ **Composable** – Enables staking NFTs, wrappers, and DeFi integrations.
- ✅ **Lock-Aware** – Use time-locked staking for reward programs.

---

## 🧪 How It Works

- `add_stake()` now creates a richer `StakedSui` object.
- Optional `sui_token_lock` supports delayed withdrawals.
- Underlying staking mechanics remain the same—just enhanced metadata.

---

## 🔁 Backward Compatibility

- No breaking changes.
- Old `StakedSui` objects remain valid.
- New fields are only used in newer staking flows.

---

## 💡 Use Cases Enabled

| Use Case                 | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| Staking Dashboards       | Query validator, amount, and epoch metadata easily.                         |
| Smart Contract Staking   | dApps and DAOs can manage stake positions.                                 |
| Liquid Staking Protocols | Turn `StakedSui` into transferable or wrapped tokens.                      |
| Locked Reward Systems    | Use `sui_token_lock` for time-based rewards or loyalty mechanisms.         |

---

## ✅ Conclusion

SIP-6 modernizes staking on Sui by making `StakedSui` programmable, traceable, and future-proof.  
It doesn't alter consensus—it **unlocks innovation** in how staking is represented and used.

> If you're building DeFi, DAOs, or advanced staking products on Sui, SIP-6 gives you the tools to do it right.

---