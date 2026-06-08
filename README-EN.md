# ALM-Simulation-Engine
ALM Projection Engine using Python and SQL

ALM analysis project based on a European G-SIB (Globally Systemically Important Bank). The objective is to test the robustness of regulatory liquidity indicators (**LCR**) and profitability metrics (**NII**) using a Python-based calculation engine.

> **Source Data:** Based on Société Générale's **2025 Universal Registration Document (URD)**.

## Project Architecture
* **Database:** SQL (Balance sheet structure, interest rates, maturities, behavioral/run-off profiles).
* **Calculation Engine:** Python (Pandas) for projecting cash flows over a 120-month horizon.
* **Visualization:** Matplotlib (Automated generation of gap charts).

---

## Liquidity Risk Analysis (LCR)
Analysis performed under a **Run-off** scenario (static balance sheet extinction) to identify breaking points without modeling bias.

| Scenario | Assumption | Result & Observation |
| :--- | :--- | :--- |
| **Baseline** | 20% deposit outflow (volatile portion) | Short-term solvency maintained; refinancing risk identified at month 72. |
| **Stress-Test** | 40% deposit outflow (Bank Run) | **Breach:** LCR drops to **42.19%** (100% regulatory threshold). Net cash position at -€93bn. |

The model demonstrates an insufficiency of HQLA (€90bn vs. €192bn of stressed cash outflows), making external intervention mandatory in the event of a systemic crisis.

---

## Interest Rate Risk (NII)
Measuring the impact of an interest rate shock on the **Net Interest Income** (Baseline NII: €27.04bn) without hedging strategies (off-balance sheet).

### Interest Rate Shock: +200 bps
* **"Standard" Scenario:** Additional profit of **+€8.8bn**.
* **"Beta 60%" Scenario:** Profit reduced to **+€3bn** if 60% of the rate hike is passed through to depositors.

**Analysis Conclusion:**
The balance sheet is structurally **"Asset-Sensitive"**. The bank mechanically benefits from a rate hike, as its assets reprice faster than its liabilities.

> Focus Point: This structure exposes the financial institution to a major margin contraction in a rate-cutting environment, highlighting the critical need for hedging strategies (Interest Rate Swaps) to stabilize the P&L.
