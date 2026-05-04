# QTCL — Quantum Blockchain MCP Server

<!-- mcp-name: io.github.shemshallah/qtcl-mcp-server -->

**The first post-quantum blockchain with a native Model Context Protocol server.**

Connect any MCP-compatible agent to the QTCL blockchain in seconds — no SDKs, no wallet extensions, no gas estimation. One URL. 11 tools. Flat fees.

```
https://qtcl-blockchain.koyeb.app/mcp/sse
```

---

## Connect in 30 seconds

### Claude Desktop

Add to `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS)  
or `%APPDATA%\Claude\claude_desktop_config.json` (Windows):

```json
{
  "mcpServers": {
    "qtcl": {
      "type": "url",
      "url": "https://qtcl-blockchain.koyeb.app/mcp/sse",
      "name": "qtcl"
    }
  }
}
```

Restart Claude Desktop. You'll see a 🔨 Tools indicator when connected.

### Claude.ai (Web)

Settings → Integrations → Add Integration  
**URL:** `https://qtcl-blockchain.koyeb.app/mcp/sse`

### Cursor / VS Code

`.cursor/mcp.json`:
```json
{
  "mcpServers": {
    "qtcl": {
      "type": "sse",
      "url": "https://qtcl-blockchain.koyeb.app/mcp/sse"
    }
  }
}
```

### Any MCP-compatible agent

```json
{
  "type": "url",
  "url": "https://qtcl-blockchain.koyeb.app/mcp/sse",
  "name": "qtcl"
}
```

### Direct JSON-RPC (no MCP required)

```bash
curl -X POST https://qtcl-blockchain.koyeb.app/rpc \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","method":"qtcl_getBlockHeight","params":[],"id":1}'
```

---

## Tools (11 total)

| Tool | Category | Description |
|------|----------|-------------|
| `qtcl_create_wallet` | Wallet | Generate a new post-quantum wallet address + keypair |
| `qtcl_get_balance` | Wallet | Check confirmed + pending balance for any address |
| `qtcl_send_transaction` | Wallet | Send QTCL with flat 1-qsat fee. Supports 256-char memo |
| `qtcl_get_transaction` | Chain | Look up any transaction by hash |
| `qtcl_get_chain_info` | Chain | Block height, mempool depth, oracle consensus status |
| `qtcl_get_block` | Chain | Block by height or hash with quantum coherence metrics |
| `qtcl_get_recent_transactions` | Chain | Last 50 txs, filterable by address |
| `qtcl_get_quantum_metrics` | Quantum | Live W-state fidelity, entanglement witness, lattice coherence |
| `qtcl_get_oracle_registry` | Quantum | 5 Byzantine consensus oracles — stake, uptime, heartbeat |
| `qtcl_get_peers` | Network | Active P2P peers and topology data |
| `qtcl_get_price` | Price | Live QTCL/USD from Pyth Network oracle feed |

---

## Why agents use QTCL

**Flat 1-qsat fee** — No gas estimation, no auctions, no MEV. Agents budget deterministically.

**Fast settlement** — ~18 second blocks. Submit → hash returned immediately. 1 confirmation = finality.

**Post-quantum security** — HypΓ cryptography (Schnorr-Γ over PSL(2,R)). Transactions are unforgeable even by quantum computers. No migration timeline to worry about.

**Machine-native API** — Pure JSON-RPC. One HTTP POST to transact. No Web3 libraries, no ABI encoding.

**Memo field** — Every transaction carries 256 chars for invoice IDs, service references, or structured agent-to-agent coordination data.

**No approval pattern** — No ERC-20 approve/transferFrom. Direct transfers. One call, one transaction.

---

## Economics

| Parameter | Value |
|-----------|-------|
| Native unit | QTCL |
| Base unit | qsat (1 QTCL = 100 qsat) |
| Fee per operation | 1 qsat (flat) |
| Block time | ~18 seconds |
| Total supply | 998,380 QTCL |
| Block reward | 8.0 QTCL |
| Fee burn rate | 70% |

---

## Quantum infrastructure

- **Oracle network:** 5-oracle Byzantine consensus (3-of-5 majority voting)
- **W-state:** Tripartite entanglement with NPT witness
- **QRNG:** 5-source ensemble (ANU, Random.org, QBICK, HotBits, Fourmilab)
- **Tessellation:** {8,3} hyperbolic Poincaré disk, depth 5, 10,920 triangles
- **Consensus:** Proof of Coherence (PoC) with non-Markovian memory kernel

---

## MCP server details

| Property | Value |
|----------|-------|
| Transport | SSE (Server-Sent Events) |
| Protocol version | MCP 2024-11-05 |
| Endpoint | `https://qtcl-blockchain.koyeb.app/mcp/sse` |
| Tools | 11 |
| Auth required | None |
| Health check | `https://qtcl-blockchain.koyeb.app/mcp/health` |

---

## Cryptography

| Primitive | Specification |
|-----------|---------------|
| Hash | SHA3-256 (NIST FIPS 202) |
| Signatures | Schnorr-Γ over PSL(2,R) — Fiat-Shamir on hyperbolic Fuchsian group |
| Encryption | HypAEAD (SHA3-256-CTR + HMAC-SHA3-256) |
| Key derivation | PBKDF2-HMAC-SHA256, 600,000 iterations |
| Address format | 64-char hex (SHA3-256 of public key) |
| Security level | ~256-bit classical / ~180-bit quantum |

---

## Agent use cases

- Agent-to-agent micropayments for API calls, compute, and data
- Escrow for multi-agent task coordination (agent A pays agent B on task completion)
- Autonomous treasury management with deterministic fee budgeting
- Verifiable payment receipts via transaction hash + memo field
- Cross-agent accounting with structured memo data
- Quantum-secured key management for high-value operations
- Decentralized agent identity anchored to QTCL addresses

---

## Links

- **Explorer:** https://qtcl-blockchain.koyeb.app/
- **Wallet UI:** https://qtcl-blockchain.koyeb.app/tx
- **Architecture:** https://qtcl-blockchain.koyeb.app/hyp
- **Agent docs:** https://qtcl-blockchain.koyeb.app/agents
- **Capability JSON:** https://qtcl-blockchain.koyeb.app/agents/capability.json
- **MCP health:** https://qtcl-blockchain.koyeb.app/mcp/health

---

## License

MIT
