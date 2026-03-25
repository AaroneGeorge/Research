# Prediction Market Resolution Controversies -- Web Research Findings
**Research Date: 2026-03-25**

---

## 1. Polymarket UMA Oracle Attack: Ukraine Mineral Deal (March 2025)

### What Happened
- **Date:** March 24-25, 2025
- **Market:** "Will Ukraine agree to Trump's mineral deal before April?"
- **Amount at stake:** $7 million
- **Outcome:** Resolved as "YES" despite no official agreement between Ukraine and the U.S.

### How the Attack Worked
- A single actor (dubbed the "UMA tycoon") controlled 5 million UMA tokens distributed across three accounts
- This represented approximately 25% of total voting power in UMA's dispute resolution system
- The market's YES probability surged from 9% to 100% between March 24-25
- The attacker voted YES through the UMA Data Verification Mechanism (DVM), overriding reality
- The bond to propose an outcome was only 750 USDC -- trivially cheap relative to the $7M at stake

### Polymarket's Response
- A team member acknowledged on Discord: "This is an unprecedented situation, and we have been in war rooms all day internally and with the UMA team to make sure this won't happen again"
- Polymarket stated no refunds would be issued, calling it "not a market failure"
- Polymarket defended the UMA voting process while acknowledging the market "resolved too soon"

### Systemic Vulnerability Exposed
- UMA's $44M circulating market cap vs. Polymarket's $330M TVL creates a 15:1 ratio -- meaning control costs roughly $22M despite $330M at stake
- Just two UMA whales control over half of all voting power
- One individual holds up to 7.5 million of the 20 million staked UMA tokens

### Sources
- [The Block: Polymarket says governance attack by UMA whale is 'unprecedented'](https://www.theblock.co/post/348171/polymarket-says-governance-attack-by-uma-whale-to-hijack-a-bets-resolution-is-unprecedented)
- [CoinDesk: Polymarket, UMA Communities Lock Horns After $7M Ukraine Bet](https://www.coindesk.com/markets/2025/03/27/polymarket-uma-communities-lock-horns-after-usd7m-ukraine-bet-resolves)
- [The Defiant: Polymarket's $7M Ukraine Mineral Deal Debacle Traced to Oracle Whale](https://thedefiant.io/news/defi/polymarket-s-usd7m-ukraine-mineral-deal-debacle-traced-to-oracle-whale)
- [Cointelegraph: Polymarket faces scrutiny over $7M Ukraine mineral deal bet](https://cointelegraph.com/news/polymarket-trump-ukraine-bet-whale-governance-attack)
- [Orochi Network: Oracle Manipulation in Polymarket 2025](https://orochi.network/blog/oracle-manipulation-in-polymarket-2025)
- [Yahoo Finance: Polymarket Faces Backlash as $7M Ukraine Mineral Deal Bet Resolves Incorrectly](https://finance.yahoo.com/news/polymarket-faces-backlash-7m-ukraine-010306627.html)

---

## 2. How Polymarket Resolves Markets Using UMA's Optimistic Oracle

### The Resolution Pipeline
1. **Proposal:** Anyone can propose an outcome by posting a bond (typically 750 USDC)
2. **Challenge Period:** 2-hour window where the proposal is assumed correct unless challenged
3. **First Dispute:** If disputed, the proposal is auto-reset and a new request is created (to filter out frivolous disputes)
4. **Second Dispute:** If disputed again, the request escalates to UMA's Data Verification Mechanism (DVM)
5. **DVM Vote:** UMA token holders vote using a commit-reveal scheme; voting power is proportional to tokens held/staked

### Key Design Details
- UMA uses the "Schelling Point" principle: voters are incentivized to vote with truth because they expect others to do the same
- Voters who align with the majority are rewarded; those who vote against the majority are penalized
- Polymarket actually uses three oracles: the Markets Team (internal), Chainlink, and UMA Protocol
- The US version of Polymarket uses the Markets Team for resolution; the international version uses UMA

### The Fundamental Flaw
- The system assumes truth and majority opinion will converge
- When a whale controls enough tokens, the "majority" becomes one actor, and the Schelling Point collapses
- The cost to attack ($22M for controlling UMA) is far less than the value at risk ($330M TVL)

### Post-Attack Fix: Managed Proposers (August 2025)
- UMA passed UMIP-189 governance proposal on August 6, 2025
- Transitioned from Optimistic Oracle V2 (OOV2) to Managed Optimistic Oracle V2 (MOOV2)
- Only whitelisted addresses can now submit resolution proposals
- Initial whitelist: 37 addresses requiring 20+ proposals with >95% accuracy in past 3 months
- Expanded to 177 addresses by November 2025
- Whitelisted proposers had 99.7% accuracy vs. 85.8% for non-whitelisted
- Criticism: This is a step toward centralization, undermining the "decentralized oracle" premise

### Sources
- [Polymarket Documentation: How Are Markets Disputed?](https://docs.polymarket.com/polymarket-learn/markets/dispute)
- [Polymarket Documentation: How Are Prediction Markets Resolved?](https://docs.polymarket.com/polymarket-learn/markets/how-are-markets-resolved)
- [RockNBlock: Inside UMA Oracle](https://rocknblock.io/blog/how-prediction-markets-resolution-works-uma-optimistic-oracle-polymarket)
- [The Block: UMA oracle update to limit resolution proposals to whitelisted parties](https://www.theblock.co/post/366507/polymarket-uma-oracle-update)
- [UMA Blog: Improving Oracle Efficiency with Managed Proposers](https://blog.uma.xyz/articles/managed-proposers)
- [Webopedia: Why Is Polymarket's UMA Controversial?](https://www.webopedia.com/crypto/learn/polymarkets-uma-oracle-controversy/)

---

## 3. Other Polymarket Resolution Controversies

### 3a. Zelenskyy Suit Market (June-July 2025)
- **Market:** "Will Zelenskyy wear a suit before July?"
- **Trading volume:** $237 million
- **Event:** On June 24, 2025, Zelenskyy appeared at a NATO event wearing a black jacket, matching trousers, and a collared shirt
- **Media consensus:** 40+ global media outlets described the outfit as a "suit"
- **Resolution:** UMA oracle ruled "No" on July 1, 2025
- **Controversy:** Traders fought for weeks on Discord over definitions. The "No" ruling contradicted widespread media descriptions.
- **Key quote from traders:** "UMA's voting incentives encourage people to vote with the perceived majority to avoid penalties, not based on factual correctness"
- Sources:
  - [CoinDesk: Polymarket Hit by $160M Controversy Over Whether Zelenskyy Wore a Suit at NATO](https://www.coindesk.com/markets/2025/07/07/polymarket-embroiled-in-usd160m-controversy-over-whether-zelensky-wore-a-suit-at-nato)
  - [Decrypt: Polymarket Rules 'No' on $237M Controversial Bet Over Zelenskyy's Suit](https://decrypt.co/329210/polymarket-rules-no-237m-bet-zelenskyys)
  - [Yahoo Finance: 'This Isn't Decentralized,' Says Polymarket Power User](https://finance.yahoo.com/news/isn-t-decentralized-says-polymarket-111359338.html)

### 3b. UFO Declassification Market (December 2025)
- **Market:** "Will Trump administration declassify UFO files in 2025?"
- **Market size:** $16 million
- **Resolution date:** December 10, 2025
- **Resolution:** "YES" despite no White House declassification order existing
- **Evidence:** CryptoSlate found no contemporaneous federal declassification notice; only routine Pentagon AARO imagery additions from existing archives
- **Suspicious activity:** One trader executed a $615,000 position approximately 10 hours before finalization, suggesting advance knowledge of the oracle timeline
- **Community reaction:** Users labeled Polymarket a "scam" and criticized "proof-of-whales" governance
- Source: [CryptoSlate: Polymarket faces major credibility crisis after whales forced a "YES" UFO vote](https://cryptoslate.com/polymarket-faces-major-credibility-crisis-after-whales-forced-a-yes-ufo-vote-without-evidence/)

### 3c. Venezuela Invasion Market (January 2026)
- **Market:** Whether the U.S. would "invade" Venezuela
- **Amount wagered:** $10.5 million+
- **Event:** U.S. military strikes bombarded Venezuela during the kidnapping of President Maduro
- **Resolution:** "NO" -- Polymarket argued the "snatch-and-extract" mission did not meet the contract's definition of "military operations intended to establish control" over territory
- **Trader reaction:** "That a military incursion, the kidnapping of a head of state, and the takeover of a country are not classified as an invasion is plainly absurd"
- **Insider trading allegation:** An anonymous user created an account on Dec. 26, placed $32K+ in wagers across four Venezuela markets, and reportedly won over $400,000
- Sources:
  - [Yahoo Finance: Polymarket Withholds Payouts on Venezuela Invasion Bets](https://finance.yahoo.com/news/polymarket-withholds-payouts-venezuela-invasion-130701655.html)
  - [Futurism: War Profiteers Furious After Polymarket Refuses to Pay Out](https://futurism.com/future-society/polymarket-venezuela-invasion-bets)
  - [Slashdot: Polymarket Refuses To Pay Bets That US Would 'Invade' Venezuela](https://news.slashdot.org/story/26/01/07/1438220/polymarket-refuses-to-pay-bets-that-us-would-invade-venezuela)

### 3d. Fort Knox Gold Market (March 2025)
- **Market:** "Gold missing from Fort Knox"
- **Amount:** ~$3.5 million stolen via manipulation
- **Resolution:** Resolved as "No" through coordinated UMA whale voting
- **Mechanism:** Two addresses controlled a majority of votes within the UMA system
- **Analyst Folke Hermansen** highlighted this as part of a pattern of markets manipulated by UMA whales
- Source: [Spectrum Search: Polymarket Scandal - Allegations of Market Manipulation by UMA Whales](https://spectrum-search.com/insights/polymarket-scandal-allegations-of-market-manipulation-by-uma-whales-unfold)

### 3e. Cardi B Super Bowl Halftime Market (February 2026)
- **Market:** Whether Cardi B would "perform" at the Super Bowl halftime show
- **Volume:** $47.3 million (across platforms)
- **Event:** Cardi B appeared on stage during Bad Bunny's set, danced but did not sing
- **Polymarket resolution:** YES (appearance counted as performance)
- **Kalshi resolution:** Settled at last traded price ($0.26 YES) citing ambiguity via Rule 6.3(c)
- **Key issue:** Same event, opposite resolutions on two platforms. Polymarket reportedly added language that "participation without singing" qualified after the event occurred.
- **Aftermath:** At least one Kalshi trader filed a CFTC complaint. Drake associate lost $177K on Polymarket.
- Sources:
  - [NBC News: Cardi B's cameo leads to dispute over prediction markets](https://www.nbcnews.com/business/business-news/cardi-b-cameo-bad-bunnys-super-bowl-halftime-show-leads-dispute-predi-rcna258553)
  - [CBS News: Dispute over Cardi B's Super Bowl cameo roils prediction markets](https://www.cbsnews.com/news/cardi-b-super-bowl-prediction-market-dispute/)
  - [Fortune: Prop bet chaos as Kalshi and Polymarket diverge](https://fortune.com/2026/02/11/did-cardi-b-perform-at-super-bowl-prop-bet-kalshi-polymarket/)
  - [DeFi Rate: How Kalshi and Polymarket Settle Event Contracts (and Disputes)](https://defirate.com/prediction-markets/how-contracts-settle/)

---

## 4. Kalshi Tennis Market: $30K Loss on Void Rules

### What Happened
- **Trader:** Chris Dierkes (handle: flupnolide)
- **Amount lost:** $30,000
- **Issue:** A tennis player withdrew (Did Not Play / DNP), and the market was not voided as the trader expected

### How Kalshi Resolved It
- Kalshi settled at "last traded fair price" -- defined as the exchange's estimate of contract value immediately before the disqualifying event
- This is computed from recent prints and resting order depth over a defined window
- Rule 6.3(c) allows Kalshi to settle ambiguous markets at last traded price
- This fundamentally differs from sportsbook conventions where DNP = void

### The Trader's Arguments
- "Last traded fair price" becomes arbitrary during rumor regimes (when DNP news is leaking but not confirmed)
- Cannot reliably estimate the counterfactual "as if player participated" price
- Thin order books and fat-finger prints distort the reference price
- Timestamp ambiguity over when exactly the player status is "known"

### Proposed Fixes (from the trader)
1. **Void with escrow** -- Hold back profits from round-tripped trades until final resolution
2. **Last traded fair price** -- Current Kalshi approach (trader calls it "least favorite")
3. **Binary outcome** -- DNP automatically = NO wins at $1.00
4. **Late listing** -- Post props after official injury reports to reduce DNP frequency

### Broader Kalshi Resolution Issues
- **Biden-Trudeau meeting market:** Biden met and shook hands with Trudeau on TV, but "Yes" bettors lost because the meeting wasn't reported by the two specific sources Kalshi designated in rules
- **Netflix earnings "Warner Bros." market:** An executive said "Warner Brothers" but market resolved "No" because the person didn't say "Bros."
- **No formal dispute mechanism:** Per reporting, the only recourse is "yell at them in Discord"

### Source
- [FiftyCentDollars Substack: I lost $30k after misunderstanding Kalshi's void rules](https://fiftycentdollars.substack.com/p/i-lost-30k-due-to-kalshis-void-rules)

---

## 5. Reddit and Community Discussions

### Key Themes from Social Media (Reddit, Discord, X)
- Reddit and social media channels are "filled with angry traders sharing their losses and expressing their disgust" following the Ukraine mineral deal manipulation
- Users describe UMA's governance model as "proof-of-whales" -- a plutocratic system where wealth equals truth
- A Reddit user explained: "when it came down to the final battle, it became clear that someone sent millions of UMA tokens to the 'Yes' side"
- Many users declared intent to leave Polymarket entirely
- Polymarket's Trustpilot reviews reflect ongoing user frustration with resolutions
- Note: Direct Reddit URLs were not returned by search engines; discussions are referenced in aggregated reporting

### Sources (aggregated references to Reddit discussions)
- [Trustpilot: Polymarket.com Reviews](https://www.trustpilot.com/review/polymarket.com)
- [Cryptopolitan: Polymarket community protests oracle vote by UMA whales](https://www.cryptopolitan.com/polymarket-community-protests-oracle-vote-by-uma-whales-claims-market-manipulation/)

---

## 6. Emerging Solutions and Alternatives

### Augur Lituus (Revived 2025)
- Augur released new oracle infrastructure via the Lituus Foundation
- Key mechanism: "Migration-Based Universe Forking with Supply Restoration"
- After a fork, REP tokens are re-minted and auctioned, forcing any attacker to buy dominance twice
- Attack cost: ~134% of oracle's fully diluted valuation (up from ~92% in old Augur)
- Disputes escalate by requiring progressively larger capital commitments
- Resolution determined by market expectation of which fork retains value, not token-holder voting
- Source: [The Defiant: Augur Reveals Lituus Oracle Infra](https://thedefiant.io/news/defi/augur-reveals-augur-lituus-oracle-whitepaper)

### AI Oracles
- DeepSafe and others propose using LLMs with decentralized computation to verify outcomes
- Chainlink exploring empirical AI oracle development
- Chaos Labs building "Edge Proofs" -- AI-powered prediction market oracles
- Key limitation: LLMs hallucinate and have no ground truth access; verifying the AI's answer recreates the oracle problem
- Sources:
  - [Medium/DeepSafe: The Value of AI Oracles](https://medium.com/@DeepSafe_Official/the-value-of-ai-oracles-insights-from-the-polymarket-oracle-manipulation-case-92d83e2bef0a)
  - [Chainlink Blog: Empirical Evidence in AI Oracle Development](https://blog.chain.link/ai-oracles/)
  - [Chaos Labs: Edge Proofs](https://chaoslabs.xyz/posts/edge-proofs-ai-powered-prediction-market-oracles)

### BNB Chain RFP
- BNB Chain issued an RFP specifically for prediction market oracle infrastructure
- Signals industry recognition that current solutions are inadequate
- Source: [BNB Chain Blog: RFP for Prediction Market Oracle](https://www.bnbchain.org/en/blog/rfp-for-prediction-market-oracle)

---

## 7. Summary of Key Statistics

| Incident | Platform | Amount | Date | Core Issue |
|---|---|---|---|---|
| Ukraine mineral deal | Polymarket/UMA | $7M | Mar 2025 | Whale governance attack (5M UMA tokens, 25% of votes) |
| Fort Knox gold | Polymarket/UMA | $3.5M | Mar 2025 | Coordinated whale voting |
| Zelenskyy suit | Polymarket/UMA | $237M volume | Jun-Jul 2025 | Ambiguity + Schelling Point failure |
| UFO declassification | Polymarket/UMA | $16M | Dec 2025 | Resolved YES with no evidence; suspicious pre-resolution trading |
| Venezuela invasion | Polymarket | $10.5M | Jan 2026 | Definitional dispute ("invasion" vs "military operation") |
| Cardi B halftime | Both platforms | $47.3M | Feb 2026 | Same event, opposite resolutions; rules allegedly changed post-hoc |
| Tennis DNP | Kalshi | $30K | 2025 | Void rules differ from sportsbook conventions |
| Biden-Trudeau meeting | Kalshi | Unknown | 2025 | Overly literal source requirements |

### Structural vulnerabilities identified:
- **UMA token concentration:** 2 whales control >50% of voting power; 1 individual holds 7.5M of 20M staked tokens
- **Economic asymmetry:** UMA market cap ($44M) vs Polymarket TVL ($330M) = 15:1 attack ratio
- **Dispute cost barrier:** $750 USDC bond discourages retail traders from challenging outcomes
- **No formal appeals on Kalshi:** Only recourse is informal Discord complaints
- **Cross-platform divergence:** Identical events can settle oppositely (Cardi B case)
