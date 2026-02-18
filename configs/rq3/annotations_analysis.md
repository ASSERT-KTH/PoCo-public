# Annotation Levels Analysis

## Overview
This document categorizes all 23 annotations based on naturally extracted levels of detail:
1. **Abstract**: High-level summary of vulnerability type and affected components
2. **Descriptive**: Code snippets and technical explanation of the vulnerability's mechanism
3. **Procedural**: Step-by-step description of how to exploit the vulnerability

**Extraction Method**: Verbatim extraction with redaction only—no synthesis or augmentation.

## Summary Statistics
- **Total annotations**: 23
- **All 3 levels** (Abstract + Descriptive + Procedural): 9 files (39%)
  - Files: 001, 009, 020, 032, 042, 048, 077, 091, 098
- **Abstract + Descriptive only**: 12 files (52%)
  - Files: 003, 008, 015, 033, 039, 041, 046, 051, 054, 058, 066, 070
- **Abstract + Procedural only** (no Descriptive): 2 files (9%)
  - Files: 018, 049
  - Note: These annotations skip technical exposition and jump directly to exploitation steps

---

## Annotations with All 3 Levels (9 files)

### **001.txt** - Multicall function invariant violation in Size protocol
- **Abstract**: Multicall function DOS vulnerability
- **Descriptive**: Code snippets from Multicall.sol, Size.sol, Deposit.sol, CapsLibrary.sol with technical explanation
- **Procedural**: Detailed scenario with credit-debt pair, specific values (100ke6 USDC, 1 year tenor)

### **009.txt** - NFT royalty fee calculation in PrivatePool
- **Abstract**: Royalty payment flaw summary
- **Descriptive**: Code snippets from PrivatePool.sol, _getRoyalty function analysis
- **Procedural**: Concrete buyer/seller examples with impact scenarios

### **020.txt** - Share price manipulation during liquidity pool initialization
- **Abstract**: Manipulation vulnerability summary
- **Descriptive**: Code from GSPFunding.sol and GSPVault.sol with annotations
- **Procedural**: 4 numbered attack steps with specific values (1001 shares, 1000e18 tokens)

### **032.txt** - Owner can block withdrawals in Putty contract
- **Abstract**: Withdrawal blocking vulnerability
- **Descriptive**: Code from PuttyV2.sol and OpenZeppelin ERC20
- **Procedural**: Two attack methods (zero address, ERC777 hook)

### **042.txt** - Utilization rate manipulation via frequent oracle consultation
- **Abstract**: Rounding issue in rate calculation
- **Descriptive**: Code from VaultAdapter.sol with annotations
- **Procedural**: 2-step attack path

### **048.txt** - Royalty fee manipulation via reentrancy in PrivatePool.buy
- **Abstract**: Royalty calculation flaw
- **Descriptive**: Code with _getRoyalty double-call pattern analysis
- **Procedural**: Attack scenario showing 0% to 100% royalty change

### **077.txt** - Reentrancy in claimRewards allows minting extra NFTs
- **Abstract**: NFT claiming mechanism exploitation
- **Descriptive**: claimRewards function and numRoundsClaimed state variable analysis
- **Procedural**: 7-step call path with roundId=3 example (6 NFTs minted instead of 3)

### **091.txt** - Pump oracle manipulation via shift() and sync() functions
- **Abstract**: Reserve manipulation issue
- **Descriptive**: GitHub links to Well.sol functions with technical explanation
- **Procedural**: 3 numbered exploitation steps

### **098.txt** - SafeTransferLib allows vault creation for non-existent tokens
- **Abstract**: createVault with SafeTransferLib issue
- **Descriptive**: Code from Cally.sol, SafeTransferLib vs SafeERC20 comparison
- **Procedural**: ProjectA/B/C scenario with numbered attacker steps

---

## Annotations with Abstract + Procedural Only (2 files)

These annotations skip technical exposition and jump directly from high-level summary to exploitation steps.

### **018.txt** - PrivatePool token theft via execute and flashLoan
- **Abstract**: Single-sentence vulnerability statement
- **Procedural**: 6 numbered steps with Bob (attacker) and Alice (victim) scenario
- **Note**: No code snippets or technical mechanism explanation

### **049.txt** - Lender can manipulate loan terms via provideNewTermsForRoll
- **Abstract**: Lender manipulation and impact summary
- **Procedural**: Walkthrough with specific values ($1,500 collateral, 1,000 debt tokens)
- **Note**: Code snippets exist but embedded within exploitation scenario; no standalone technical explanation

---

## Annotations with Abstract + Descriptive Only (12 files)

These annotations have high-level summaries and technical/code details but lack structured step-by-step exploitation scenarios.

### **003.txt** - Access control issue in Vault.mintYieldFee
- **Abstract**: Access control flaw summary
- **Descriptive**: mintYieldFee function code snippet with GitHub link

### **008.txt** - Rounding errors in LiquidityPool deposit causing share imbalance
- **Abstract**: Core issue description
- **Descriptive**: Code from deposit and processDeposit functions with audit comments

### **015.txt** - Arbitrary hooks in Vault.setHooks
- **Abstract**: Single sentence vulnerability statement
- **Descriptive**: setHooks function snippet with line number

### **033.txt** - Flash loan fee scaling inconsistency
- **Abstract**: Fee confusion explanation
- **Descriptive**: flashFee function snippet with line numbers

### **039.txt** - Revert on zero-transfer tokens blocking claimProceeds
- **Abstract**: Blocking issue description
- **Descriptive**: Code from AuctionHouse with Transfer.transfer details

### **041.txt** - Auction routing override via lotRouting[0] manipulation
- **Abstract**: Takeover vulnerability summary
- **Descriptive**: lotRouting[0] and auction() function references

### **046.txt** - Zero-amount transfer blocking rewards in CVXStaker
- **Abstract**: Blocking issue description
- **Descriptive**: Code from CVXStaker.sol showing getReward function

### **051.txt** - DOS via front-running deposit in LiquidityPool
- **Abstract**: DOS vulnerability summary
- **Descriptive**: processDeposit/processMint technical explanation with attack flow

### **054.txt** - False transfer success for non-reverting ERC20 tokens
- **Abstract**: Issue with tokens returning false
- **Descriptive**: Full technical explanation with ZRX token example

### **058.txt** - Royalty collection without distribution due to zero recipient
- **Abstract**: Royalty distribution inconsistency
- **Descriptive**: Code from PrivatePool.buy and sell functions

### **066.txt** - Deposit calculation error due to premature asset transfer
- **Abstract**: Issue statement
- **Descriptive**: Code from depositAsset and getAssetDistributionData with function call chain

### **070.txt** - Incorrect pausing implementation in PhiNFT1155
- **Abstract**: Pausing mechanism failure
- **Descriptive**: Parent contract inheritance list with explanation

