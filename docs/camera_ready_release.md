# SolarChain Camera-Ready Release

This repository contains the camera-ready release artifacts for:

**SolarChain: A Physics-Grounded Embodied IoT System for Verifiable Urban Solar Market Design**  
UbiComp Companion '26, Shanghai, China.

## Paper

- Camera-ready PDF filename: `SolarChain_Camera_Ready.pdf`
- PDF SHA-256: `f5e826400919573129805a72e99f199db4d05e7bdedbdf5ff2717a4a541a2b75`

## Core Reproducibility Artifacts

| Artifact | Path | Role |
|---|---|---|
| Dataset provenance | `Simulator/data/datasets_2026_04_month/dataset_provenance.json` | Records the benchmark window, seed, city/node counts, weather cache, and generation pipeline. |
| Monthly node metadata | `Simulator/data/datasets_2026_04_month/urban_energy_nodes.csv` | Defines the 50 synthetic PV nodes and physical parameters. |
| Monthly generation benchmark | `Simulator/data/datasets_2026_04_month/spatiotemporal_generation.csv` | Contains the 36,000 hourly PV records with physics bounds and FDIA labels. |
| Market liquidity benchmark | `Simulator/data/datasets_2026_04_month/market_liquidity.csv` | Contains the selected 20/80 reward/liquidity market trace. |
| P2P trade trace | `Simulator/data/datasets_2026_04_month/p2p_trades.csv` | Contains simulated factory energy purchases and token burns. |
| Attack taxonomy results | `Simulator/data/experiments/attack_taxonomy_results.csv` | Reports detector performance across 11 scripted attack classes. |
| Ratio sweep results | `Simulator/data/experiments/ratio_sweep_results.csv` | Reports the full reward/liquidity allocation sweep. |
| Ratio selection summary | `Simulator/data/experiments/ratio_selection_summary.csv` | Records the selected 20/80 default under the stated simulation assumptions. |
| Event-chain verification | `Simulator/data/experiments/event_chain_verification.csv` | Replays and checks the hash-linked audit trace. |
| Smart contract split test | `smart_contract/test/EnergyExchangeSplit.test.js` | Verifies default 2000 bps reward and configurable allocation bounds. |

## Regeneration Commands

```bash
python Simulator/data/generate_monthly_datasets.py
python Simulator/experiments/run_all_eiot_experiments.py
python Simulator/data/visualizations.py
```

For smart-contract validation:

```bash
cd smart_contract
npm install
npx hardhat test
```

## Scope Statement

The release supports the controlled prototype claims in the paper. It does not
claim field deployment readiness, sensor-origin authenticity, economic
optimality, or a security audit. The benchmark combines sourced city-level
weather, physics-modeled generation bounds, synthetic nodes and markets,
scripted attacks, and replayable audit traces.
