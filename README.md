# clone-lin-morpho-shares

Experimental i64-scale LIN clone of [morpho-org/morpho-blue](https://github.com/morpho-org/morpho-blue) tag `v1.0.0` `SharesMathLib` (`src/libraries/SharesMathLib.sol` + `MathLib.sol`).

- **LIN clone:** [`src/lin_morpho_shares.lin`](src/lin_morpho_shares.lin)
- **Proofs (results only) live in lin-open:** https://github.com/kbelludoo/lin-open/tree/master/examples/morpho_shares
- **Event receipt:** `docs/events/EVENT_MORPHO_SHARES_CLONE_LIN.rulel` in lin-open

This repository is the standalone LIN copy. It is **not** Morpho Blue, **not** a lending market, and does **not** claim Solidity uint256 parity.

File SPDX is GPL-2.0-or-later. The v1.0.0 repo LICENSE was BUSL-1.1 with Change Date 2026-01-01 and Change License GPL-2.0-or-later. This copy is published after that date.

Canonical goldens (uint64-scale, 128-bit product):

- `toSharesDown(1000, 0, 0)` = **1000000000** (VIRTUAL_SHARES=1e6, VIRTUAL_ASSETS=1)
- `toSharesDown(1, 0, 0)` = **1000000**
- `toAssetsDown(1000000, 0, 0)` = **1**
- named contrast OZ ERC-4626 offset-0: `toSharesDown(1000, 0, 0)` = **1000**
- after 1e6-asset donation, victim of 1e6 assets: Morpho **1999996** vs OZ-offset-0 **1**
- `mulDivDown(7, 9, 2)` = **31**; `mulDivUp` = **32** (remainder+1, not x*y+(d-1))
- `1e18 * 1e18 / 1` fail-closes to **0**
