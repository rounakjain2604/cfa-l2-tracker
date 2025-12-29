# Fixed Income LM 1: The Term Structure and Interest Rate Dynamics
## COMPREHENSIVE EXAM-ORIENTED STUDY NOTES (200% EDITION)

---

# MODULE OVERVIEW

This is the foundational Fixed Income module. Master this, and everything else in FI builds on it. **Expect 2-4 questions on the exam.**

## Learning Outcome Statements (LOS):
1. Describe relationships among spot rates, forward rates, YTM, expected/realized returns, and yield curve shape
2. Describe bootstrapping to obtain zero-coupon rates from par curve
3. Describe assumptions about spot rate evolution in active bond portfolio management
4. Describe rolling down the yield curve strategy
5. Explain swap rate curve and its use in valuation
6. Calculate and interpret swap spreads
7. Describe short-term spreads for credit/liquidity risk
8. Explain traditional term structure theories
9. Explain yield curve factor models and risk management
10. Explain yield volatility term structure
11. Explain macroeconomic factors affecting rates and spreads

---

# PART 1: SPOT RATES, FORWARD RATES, AND THE FORWARD RATE MODEL

## LOS 1.a: Relationships Among Spot Rates, Forward Rates, YTM, and Yield Curve Shape

---

### INTUITION FIRST

**The Time Value of Money Has a Term Structure**

Interest rates aren't one number—they're different for different time horizons. The "term structure" is simply the pattern of these rates across maturities.

**Spot Rate (z_N)**: The yield TODAY on a zero-coupon bond maturing in N years. It's "spot" because the transaction happens now.

**Forward Rate (f_{A,B-A})**: The yield agreed TODAY for a loan that STARTS in the future (at time A) and lasts for (B-A) periods.

**Indian Example:**
- You want to invest ₹10 lakh. Option 1: 3-year FD at 7% (spot rate)
- Option 2: 1-year FD at 6%, then a pre-agreed 2-year FD starting next year
- The rate on that future 2-year FD is the forward rate f_{1,2}

**Why do forward rates exist?**
If markets allow you to lock in future rates today, the rates must be mathematically consistent with spot rates—otherwise arbitrageurs would exploit the difference.

---

### CFAI CONCEPT BREAKDOWN

#### Core Definitions

| Term | Symbol | Definition |
|------|--------|------------|
| Discount Factor | DF_N | Price today of ₹1 received at time N |
| Spot Rate | z_N | Annualized YTM on N-period zero-coupon bond |
| Forward Rate | f_{A,B-A} | Rate for loan starting at A, ending at B |
| Spot Curve | — | Graph of spot rates vs. maturity |
| Forward Curve | — | Graph of forward rates for given start date |
| Discount Function | — | Set of all discount factors |

#### FORMULA 1: Discount Factor

$$DF_N = \frac{1}{(1 + z_N)^N}$$

**Meaning**: DF_N is the present value of ₹1 received N periods from now.

If z_3 = 9%, then DF_3 = 1/(1.09)³ = 0.7722
This means ₹1 in 3 years is worth ₹0.7722 today.

---

#### FORMULA 2: Forward Pricing Model (NO-ARBITRAGE)

$$DF_B = DF_A \times F_{A,B-A}$$

Where F_{A,B-A} is the forward PRICE (not rate) of a (B-A) period bond delivered at time A.

**Derivation Logic:**
Two ways to get ₹1 at time B:
1. Buy a B-period zero today: Pay DF_B
2. Enter a forward contract: Pay DF_A today (for A-period zero), then pay F_{A,B-A} at time A for remaining bond

No-arbitrage: Both must cost the same → DF_B = DF_A × F_{A,B-A}

---

#### FORMULA 3: Forward Rate Model

$$\boxed{(1 + z_B)^B = (1 + z_A)^A \times (1 + f_{A,B-A})^{B-A}}$$

**THIS IS THE MASTER EQUATION.**

Rearranged to find forward rate:
$$f_{A,B-A} = \left[\frac{(1 + z_B)^B}{(1 + z_A)^A}\right]^{\frac{1}{B-A}} - 1$$

---

### CFAI EXAMPLE 1: Spot and Forward Prices and Rates (1)

**Given:** z_1 = 7%, z_3 = 9%
**Find:** Forward price F_{1,2} for a 2-year bond delivered in 1 year

**Step 1: Calculate DF_1**
$$DF_1 = \frac{1}{(1+0.07)^1} = 0.9346$$

**Step 2: Calculate DF_3**
$$DF_3 = \frac{1}{(1+0.09)^3} = 0.7722$$

**Step 3: Apply Forward Pricing Model**
$$F_{1,2} = \frac{DF_3}{DF_1} = \frac{0.7722}{0.9346} = 0.8262$$

**Interpretation:** Today, you agree to pay 0.8262 one year from now to receive 1.00 three years from now.

---

### CFAI EXAMPLE 2: Spot and Forward Prices and Rates (2)

**Given:** z_1 = 9%, z_2 = 10%, z_3 = 11%

**Part 1: Calculate f_{1,1}** (one-year rate, one year from now)

$$(1 + z_2)^2 = (1 + z_1)^1 \times (1 + f_{1,1})^1$$
$$(1.10)^2 = (1.09) \times (1 + f_{1,1})$$
$$f_{1,1} = \frac{1.21}{1.09} - 1 = 11.01\%$$

**Part 2: Calculate f_{2,1}** (one-year rate, two years from now)

$$(1 + z_3)^3 = (1 + z_2)^2 \times (1 + f_{2,1})^1$$
$$(1.11)^3 = (1.10)^2 \times (1 + f_{2,1})$$
$$f_{2,1} = \frac{1.3676}{1.21} - 1 = 13.03\%$$

**Part 3: Calculate f_{1,2}** (two-year rate, one year from now)

$$(1 + z_3)^3 = (1 + z_1)^1 \times (1 + f_{1,2})^2$$
$$(1.11)^3 = (1.09) \times (1 + f_{1,2})^2$$
$$f_{1,2} = \sqrt{\frac{1.3676}{1.09}} - 1 = 12.01\%$$

**Part 4: Observation**
Upward-sloping spot curve → Forward rates ABOVE spot rates
Forward rates INCREASE with later start dates (13.03% > 11.01%)

---

### FORMULA 4: Spot Rate as Geometric Average

$$(1 + z_T)^T = (1 + z_1)(1 + f_{1,1})(1 + f_{2,1})...(1 + f_{T-1,1})$$

**Interpretation:** The T-period spot rate is the geometric average of the one-period spot rate and all intervening one-period forward rates.

---

### CFAI EXAMPLE 3: Verification

**Using z_1 = 9%, f_{1,1} = 11.01%, f_{2,1} = 13.03%:**

Verify z_2 = 10%:
$$z_2 = \sqrt{(1.09)(1.1101)} - 1 = \sqrt{1.21} - 1 = 10\% ✓$$

Verify z_3 = 11%:
$$z_3 = \sqrt[3]{(1.09)(1.1101)(1.1303)} - 1 = \sqrt[3]{1.367} - 1 = 11\% ✓$$

---

### KEY RELATIONSHIP: Spot Curve Shape and Forward Curve Position

#### FORMULA 5: Forward Rate Relationship to Spot

$$\left(\frac{1 + z_B}{1 + z_A}\right)^{\frac{B}{B-A}} = 1 + f_{A,B-A}$$

**Implications:**

| Spot Curve | Forward Curve | Forward Rate vs. z_B |
|------------|---------------|---------------------|
| Upward sloping (z_B > z_A) | ABOVE spot curve | f_{A,B-A} > z_B |
| Downward sloping (z_B < z_A) | BELOW spot curve | f_{A,B-A} < z_B |
| Flat (z_B = z_A) | Coincident | f_{A,B-A} = z_B |

---

### CFAI EXAMPLE 4: Confirming the Relationship

**Given:** z_1 = 9%, z_2 = 10%, z_3 = 11% (upward sloping)

**Question 1:** Is f_{1,2} > z_3 or < z_3?
**Answer:** f_{1,2} = 12.01% > z_3 = 11% ✓ (upward slope means forward > long spot)

**Question 2:** Do forward rates rise or fall with later start dates?
**Answer:** They RISE. f_{1,1} = 11.01% < f_{2,1} = 13.03% ✓

---

### TWO INTERPRETATIONS OF FORWARD RATES (MEMORIZE!)

If f_{7,1} = 3% (one-year rate, seven years from now):

**Interpretation 1: Breakeven Reinvestment Rate**
3% is the rate that makes you INDIFFERENT between:
- Buying an 8-year zero-coupon bond, OR
- Buying a 7-year zero and reinvesting proceeds for 1 year at maturity

**Interpretation 2: Locked-In Rate**
3% is the rate you can LOCK IN TODAY by:
- Buying an 8-year zero instead of a 7-year zero
- The extra return from extending maturity by 1 year = 3%

---

### HISTORICAL DATA: US Treasury (Exhibit 2 & 3)

**July 2013 - Upward Sloping:**
| Maturity | 1yr | 2yr | 5yr | 10yr | 30yr |
|----------|-----|-----|-----|------|------|
| Spot Rate | 0.11% | 0.33% | 1.37% | 2.61% | 3.66% |

Forward curves (1-year, 2-year, etc. ahead) all lie ABOVE the spot curve.

**December 2006 - Downward Sloping (Modified):**
| Maturity | 1yr | 2yr | 5yr | 10yr | 30yr |
|----------|-----|-----|-----|------|------|
| Spot Rate | 4.90% | 4.82% | 4.70% | 4.51% | 4.31% |

Forward curves all lie BELOW the spot curve.

---

### EXAM TRAPS

| Trap | How to Avoid |
|------|--------------|
| Confusing f_{1,2} with f_{2,1} | f_{1,2} = 2-year loan starting in 1 year; f_{2,1} = 1-year loan starting in 2 years |
| Wrong exponent in formula | (B-A) is the TENOR, not start date |
| Forward extends beyond spot curve | Max forward maturity = spot curve length minus start date |

---

## LOS 1.b: Bootstrapping Zero-Coupon Rates from Par Curve

---

### WHAT IS BOOTSTRAPPING? (Complete Walkthrough)

**Problem:** We observe par rates (YTM on coupon bonds trading at par), but we need spot rates for valuation.

**Solution:** Extract spot rates one at a time, starting from shortest maturity.

**Why "Bootstrapping"?** Like pulling yourself up by your bootstraps—each step uses previous steps.

---

### COMPLETE NUMERICAL EXAMPLE

**Given Par Rates (Annual Coupon Sovereign Bonds):**
- 1-year par rate = 5%
- 2-year par rate = 5.97%
- 3-year par rate = 6.91%
- 4-year par rate = 7.81%

**Step 1: z_1 = Par Rate for 1 year = 5%**
(Only one cash flow, so spot = par)

**Step 2: Bootstrap z_2**

A 2-year par bond pays 5.97% coupon and trades at 100:
$$100 = \frac{5.97}{(1+z_1)} + \frac{105.97}{(1+z_2)^2}$$
$$100 = \frac{5.97}{1.05} + \frac{105.97}{(1+z_2)^2}$$
$$100 = 5.686 + \frac{105.97}{(1+z_2)^2}$$
$$94.314 = \frac{105.97}{(1+z_2)^2}$$
$$(1+z_2)^2 = 1.1236$$
$$z_2 = 6.00\%$$

**Step 3: Bootstrap z_3**

$$100 = \frac{6.91}{1.05} + \frac{6.91}{(1.06)^2} + \frac{106.91}{(1+z_3)^3}$$
$$100 = 6.581 + 6.151 + \frac{106.91}{(1+z_3)^3}$$
$$87.268 = \frac{106.91}{(1+z_3)^3}$$
$$z_3 = 7.00\%$$

**Step 4: Bootstrap z_4**

$$100 = \frac{7.81}{1.05} + \frac{7.81}{(1.06)^2} + \frac{7.81}{(1.07)^3} + \frac{107.81}{(1+z_4)^4}$$
$$z_4 = 8.00\%$$

**Summary:**
| Maturity | Par Rate | Spot Rate |
|----------|----------|-----------|
| 1 year | 5.00% | 5.00% |
| 2 years | 5.97% | 6.00% |
| 3 years | 6.91% | 7.00% |
| 4 years | 7.81% | 8.00% |

**Key Insight:** When curve slopes UP → Spot > Par (for maturities > 1)

---

### YIELD CURVE SHAPES

| Shape | Interpretation | Frequency |
|-------|----------------|-----------|
| **Upward Sloping** | Expected rising rates OR liquidity premiums | Most common |
| **Inverted/Downward** | Expected rate cuts, recession fears | Pre-recession signal |
| **Flat** | Transition period | Brief, unstable |
| **Humped** | Intermediate rates highest | Rare |

---

# PART 2: YTM IN RELATION TO SPOT AND FORWARD RATES

## LOS 1.c: Assumptions in Active Bond Portfolio Management

---

### YTM AS WEIGHTED AVERAGE OF SPOT RATES

**Key Insight:** YTM is a single rate that summarizes discounting at multiple spot rates.

For a coupon bond:
$$\text{Price} = \frac{C}{(1+y)^1} + \frac{C}{(1+y)^2} + ... + \frac{C+Par}{(1+y)^T}$$

Where y = YTM, applied uniformly to all cash flows.

**But true pricing uses:**
$$\text{Price} = \frac{C}{(1+z_1)^1} + \frac{C}{(1+z_2)^2} + ... + \frac{C+Par}{(1+z_T)^T}$$

**Therefore:** YTM is a weighted average of spot rates, with weights based on PV of each cash flow.

---

### CFAI EXAMPLE 5: Spot Rate and YTM

**Given:** z_1 = 9%, z_2 = 10%, z_3 = 11%

**Part 1: 2-Year Bond, 6% Coupon, $1,000 Par**

Using spot rates:
$$Price = \frac{60}{1.09} + \frac{1060}{(1.10)^2} = 55.05 + 876.03 = \$931.08$$

Solving for YTM (y_2):
$$931.08 = \frac{60}{(1+y_2)} + \frac{1060}{(1+y_2)^2}$$
$$y_2 = 9.97\%$$

**Observation:** z_1 = 9% < y_2 = 9.97% < z_2 = 10%

YTM is pulled toward z_2 because the largest cash flow ($1,060) occurs at Year 2.

**Part 2: 3-Year Bond, 5% Coupon, £100 Par**

$$Price = \frac{5}{1.09} + \frac{5}{(1.10)^2} + \frac{105}{(1.11)^3} = £85.49$$

Solving: y_3 = 10.93%

**Observation:** y_3 = 10.93% is very close to z_3 = 11% because principal repayment dominates.

---

### CONDITIONS FOR REALIZED RETURN = YTM

| Condition | Why It Matters |
|-----------|---------------|
| Hold to maturity | Avoid selling at unknown future price |
| No default | Receive all promised cash flows |
| Reinvest coupons at YTM | Maintain compound growth rate |
| Flat yield curve | Reinvestment rate matches YTM |

**When YTM is a POOR estimate:**
1. Volatile interest rates (reinvestment varies)
2. Sloped yield curve (reinvestment ≠ YTM)
3. Default risk (cash flows uncertain)
4. Embedded options (holding period uncertain)

---

### EXPECTED RETURN CALCULATION

**Given:** z_1=5%, z_2=6%, z_3=7%, z_4=8%, z_5=9%
**Bond:** 5-year, 10% annual coupon
**Price:** 105.43, **YTM:** 8.62%

**Forward rates:** f_{1,1}=7.0%, f_{2,1}=9.0%, f_{3,1}=11.1%, f_{4,1}=13.1%

**If forward rates become future spot rates:**

Year 5 cash = 10(1.07)(1.09)(1.111)(1.131) + 10(1.09)(1.111)(1.131) + 10(1.111)(1.131) + 10(1.131) + 110 ≈ 162.22

Expected return = (162.22/105.43)^0.2 - 1 = **9.00%**

**Critical:** 9.00% ≠ 8.62% (YTM)

**YTM only equals expected return if the curve is FLAT.**

---

### CFAI EXAMPLE 6: Yield and Return Concepts

**Q1:** When spot curve is upward sloping, forward curve:
**A:** Lies ABOVE the spot curve ✓

**Q2:** YTM of default-risk-free bond:
**A:** Can be viewed as weighted average of spot rates ✓

**Q3:** When spot curve is downward sloping, later initiation date results in forward curve:
**A:** Greater distance BELOW the spot curve ✓

---

# PART 3: ACTIVE BOND PORTFOLIO MANAGEMENT

## LOS 1.d: Rolling Down the Yield Curve

---

### THE STRATEGY

**Concept:** Buy bonds with maturity LONGER than investment horizon, then sell before maturity.

**Why it works:** With upward-sloping, stable curve, the bond "rolls down" to lower yields → Higher prices → Capital gain.

**Required Conditions:**
1. Upward-sloping yield curve
2. Curve expected to remain unchanged
3. Sell before maturity

---

### WHEN SPOT RATES EVOLVE AS IMPLIED BY FORWARD CURVE

**Given:** z_1=9%, z_2=10%, z_3=11%, f_{1,1}=11.01%, f_{1,2}=12.01%

**If one-year spot curve matches forward curve:**

**1-Year Zero Return (1 year holding):**
$$(100 ÷ \frac{100}{1.09}) - 1 = \frac{100}{91.74} - 1 = 9\%$$

**2-Year Zero Return (1 year holding):**
$$\left(\frac{100}{1+f_{1,1}} ÷ \frac{100}{(1.10)^2}\right) - 1 = \left(\frac{90.08}{82.64}\right) - 1 = 9\%$$

**3-Year Zero Return (1 year holding):**
$$\left(\frac{100}{(1+f_{1,2})^2} ÷ \frac{100}{(1.11)^3}\right) - 1 = \left(\frac{79.71}{73.12}\right) - 1 ≈ 9\%$$

**Result:** ALL bonds earn the one-period risk-free rate (9%) if forwards become spots.

---

### WHEN ACTUAL FUTURE SPOTS ≠ FORWARDS

**Scenario:** Spot curve at Year 1 is FLAT at 10%

**1-Year Zero Return:** 9% (matures at par)

**2-Year Zero Return:**
$$\left(\frac{100}{1.10} ÷ \frac{100}{(1.10)^2}\right) - 1 = 10\%$$

**3-Year Zero Return:**
$$\left(\frac{100}{(1.10)^2} ÷ \frac{100}{(1.11)^3}\right) - 1 = 13.03\%$$

**Result:** Returns DIFFER when actual spots ≠ forwards.

---

### DETAILED ROLLDOWN EXAMPLE

**Spot Rates:** 1yr=2%, 3yr=4%, 4yr=5%, 5yr=6%, 6yr=7%
**Investment Horizon:** 2 years

**Strategy A: Maturity-Matching (Buy 5-year 6% bond at par)**

After 2 years (becomes 3-year bond at 4%):
- Coupon 1 reinvested: 6 × 1.02 = 6.12
- Coupon 2: 6
- Bond price at 4%: 6/1.04 + 6/1.04² + 106/1.04³ = 105.55
- Total = 117.67
- **Annualized return = 8.48%**

**Strategy B: Rolling Down (Buy 6-year 7% bond at par)**

After 2 years (becomes 4-year bond at 5%):
- Coupon 1 reinvested: 7 × 1.02 = 7.14
- Coupon 2: 7
- Bond price at 5%: 7/1.05 + 7/1.05² + 7/1.05³ + 107/1.05⁴ = 107.09
- Total = 121.23
- **Annualized return = 10.10%**

**Excess return from rolling = 1.62%**

---

### CFAI EXAMPLE 7: Active Bond Portfolio Management

**Q1:** Rolling down requires buying bonds with maturities:
**A:** Longer than investment horizon ✓

**Q2:** A bond is overvalued if expected spot rate is:
**A:** Higher than current forward rate ✓ (market discounts too low)

**Q3:** Flat 6% curve, 3-year £100 bond, 6% coupon. Expected return if curve shifts to flat 7%?
$$\frac{6 + \frac{6}{1.07} + \frac{106}{(1.07)^2}}{100} - 1 = 4.19\%$$ ✓

**Q4:** Forward contract price increases if future spot rates are:
**A:** Lower than predicted by current forward rates ✓

---

### MATURITY SPREAD CARRY TRADE

Post-2008, steep curves enabled:
- Borrow short-term (cheap)
- Invest long-term (higher yield)
- Profit from spread

**Risk:** Unexpected rate spike (inflation surprise) causes losses on long positions.

---

# PART 4: THE SWAP RATE CURVE

## LOS 1.e: Swap Curve and Valuation

---

### WHAT IS AN INTEREST RATE SWAP?

**Fixed-for-Floating Swap:**
- Party A pays FIXED rate (swap rate)
- Party B pays FLOATING rate (MRR - Market Reference Rate)
- No principal exchanged, only net interest difference

**Swap Rate:** The fixed rate that makes swap value = 0 at initiation.

---

### WHY USE SWAP CURVE?

| Situation | Use Swap Curve |
|-----------|----------------|
| Limited government bond market | Swap market more liquid |
| Large private sector | More relevant benchmark |
| Bank balance sheet hedging | Matches swap exposures |
| Cross-country comparisons | More standardized |

---

### BANK FUNDING EXAMPLE (CFAI)

**Scenario:** Bank raises funds via CDs
- $10M CD at 1.50% for 2 years
- $10M CD at 1.70% for 3 years

**Swaps entered:**
- Receive 1.50% fixed, pay MRR - 10 bps (2-year, $10M)
- Receive 1.70% fixed, pay MRR - 15 bps (3-year, $10M)

**Result:** 
- Fixed receipts offset CD payments
- Net funding cost = MRR - 12.5 bps (weighted average)
- Converted fixed liabilities to floating

---

### DERIVING SWAP RATES FROM SPOT RATES

$$\sum_{t=1}^{T} \frac{s_T}{(1+z_t)^t} + \frac{1}{(1+z_T)^T} = 1$$

Left side = PV of fixed payments + PV of notional
Right side = Value of floating leg (always 1 at initiation)

---

### CFAI EXAMPLE 8: Determining Swap Rate Curve

**Given Discount Factors:**
DF_1=0.9524, DF_2=0.8900, DF_3=0.8163, DF_4=0.7350

**Step 1: Derive Spot Rates**
z_1 = (1/0.9524)^1 - 1 = 5%
z_2 = (1/0.8900)^0.5 - 1 = 6%
z_3 = (1/0.8163)^(1/3) - 1 = 7%
z_4 = (1/0.7350)^0.25 - 1 = 8%

**Step 2: Calculate Swap Rates**

s_1 = 5% (trivial)

s_2: Solve s_2/1.05 + (s_2+1)/(1.06)² = 1 → s_2 = 5.97%

s_3: Solve → s_3 = 6.91%

s_4: Solve → s_4 = 7.81%

**Note:** Swap rates = Par rates (same mathematical relationship)

---

## LOS 1.f & 1.g: Swap Spreads and Short-Term Spreads

---

### SWAP SPREAD

$$\text{Swap Spread} = \text{Swap Rate} - \text{On-the-Run Government Bond Yield}$$

**Example:** 5-year swap = 2.00%, 5-year Treasury = 1.70%
Swap spread = 30 bps

**Interpretation:** Premium for bank credit risk over government risk.

---

### NEGATIVE SWAP SPREADS (POST-2008)

30-year Treasury swap spread turned negative after Lehman collapse.

**Reasons:**
- Increased dealer capital requirements
- Strong demand for duration hedging
- Supply/demand imbalances

---

### I-SPREAD (Interpolated Spread)

$$\text{I-Spread} = \text{Bond YTM} - \text{Swap Rate (same maturity)}$$

Uses linear interpolation if exact maturity unavailable.

---

### Z-SPREAD (Zero-Volatility Spread)

Constant spread added to ENTIRE spot curve:

$$\text{Price} = \sum_{t=1}^{T} \frac{CF_t}{(1 + z_t + Z)^t}$$

**Key:** Z-spread > I-spread usually (accounts for full curve shape)

---

### BOND PRICING WITH SWAP SPREAD

**Example:** GE Capital notes, 1.625% coupon, maturing 2 July 2024
Evaluation: 12 July 2021 (2.97 years remaining)

Treasury 2.97-year interpolated rate: 0.586%
Swap spread: 0.918%
YTM = 0.586% + 0.918% = 1.504%

Invoice price (including accrued interest): $1,003,954.12
Accrued interest: $451.39
Clean price: $1,003,502.73

---

### TED SPREAD

$$\text{TED Spread} = \text{3-month MRR} - \text{3-month T-bill Rate}$$

**Measures:** Overall credit and liquidity risk in money markets

| Period | TED Spread | Interpretation |
|--------|------------|----------------|
| Normal | ~30-50 bps | Stable |
| Lehman (Sep 2008) | ~450 bps | Extreme stress |
| COVID (Mar 2020) | ~150 bps | Short spike |

---

### MRR-OIS SPREAD

$$\text{MRR-OIS Spread} = \text{MRR} - \text{Overnight Index Swap Rate}$$

OIS = nearly risk-free (overnight unsecured lending)
Spread captures bank credit risk specifically.

---

### SOFR (Secured Overnight Financing Rate)

Transaction-based rate for overnight Treasury repo market.
Replacing LIBOR globally.
Reflects supply/demand in secured funding markets.

---

*[Continued in next section due to length...]*
