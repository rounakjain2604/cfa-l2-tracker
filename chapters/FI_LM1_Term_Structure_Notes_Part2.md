# Fixed Income LM 1: Part 2 - Term Structure Theories, Factor Models & Practice Problems

---

# PART 5: TRADITIONAL TERM STRUCTURE THEORIES

## LOS 1.h: Term Structure Theories and Implications

---

### THEORY 1: UNBIASED (PURE) EXPECTATIONS THEORY

**Core Claim:** Forward rates are UNBIASED predictors of future spot rates.

**Assumptions:**
- Investors are risk-neutral
- No risk premiums exist
- Bonds of any maturity are perfect substitutes

**Implications:**
- Upward-sloping curve → Market expects rates to RISE
- Downward-sloping curve → Market expects rates to FALL
- Flat curve → Market expects rates UNCHANGED

**Problem:** Assumes risk neutrality, contradicted by evidence of risk aversion.

---

### THEORY 2: LOCAL EXPECTATIONS THEORY

**Core Claim:** Over SHORT holding periods, ALL bonds earn the risk-free rate.

**Key Difference from Pure Expectations:**
- Based on no-arbitrage, not risk neutrality
- Can accommodate risk premiums for LONGER horizons
- Only short-term returns equalize

**Problem:** Empirically, short-term returns on long bonds often EXCEED short bonds.

---

### THEORY 3: LIQUIDITY PREFERENCE THEORY

**Core Claim:** Investors demand LIQUIDITY PREMIUM for holding longer-term bonds.

**Implications:**
$$\text{Forward Rate} = \text{Expected Future Spot} + \text{Liquidity Premium}$$

- Forward rates are UPWARDLY BIASED predictors of future spots
- Premiums INCREASE with maturity
- Explains why curves are usually upward sloping

**Key Insight:** Even with flat rate expectations, curve slopes UP due to premiums.

**Downward slope possible if:** Expected rate decline > liquidity premium

---

### THEORY 4: SEGMENTED MARKETS THEORY

**Core Claim:** Each maturity segment is a SEPARATE market; yields determined by supply/demand in each segment independently.

**Assumptions:**
- Investors CANNOT or WILL NOT move across maturities
- Asset/liability matching constraints (regulatory or self-imposed)
- No arbitrage across segments

**Examples:**
- Life insurers buy long-term (match policy liabilities)
- Banks buy short-term (match deposit liabilities)
- Money market funds restricted to ≤1 year maturities

**Problem:** Too extreme—ignores that investors CAN move if incentivized.

---

### THEORY 5: PREFERRED HABITAT THEORY

**Core Claim:** Investors PREFER certain maturities but WILL move if compensated.

**Key Features:**
- Blends expectations and segmentation
- Risk premiums vary by maturity based on supply/demand
- Most REALISTIC of all theories

**Implication:** Yields reflect BOTH:
- Expected future rates
- Supply/demand imbalances in each segment

---

### PREFERRED HABITAT AND QUANTITATIVE EASING (QE)

**Fed Holdings (2007 vs 2014):**

| Asset | Sep 2007 | Oct 2014 |
|-------|----------|----------|
| Total Securities | $780B | $4,219B |
| T-Bills | $267B | $0 |
| Notes/Bonds | $472B | $2,347B |
| MBS | $0 | $1,718B |

**Effect:** Fed buying MBS reduced supply for private buyers → "Preferred habitat" investors bid up prices → Yields fell from 5-6% to <2%.

---

### CFAI EXAMPLE 9: Traditional Term Structure Theories

**Q1:** Fallen angel yields often exceed otherwise identical bonds because of:
**A:** Segmented markets theory ✓ (forced selling by constrained investors)

**Q2:** Investors induced by attractive yields to deviate from preferred maturities:
**A:** Preferred habitat theory ✓

**Q3:** Unbiased expectations theory assumes investors are:
**A:** Risk neutral ✓

**Q4:** Market evidence shows forward rates are:
**A:** Upwardly biased predictors of future spot rates ✓ (liquidity premiums exist)

**Q5:** Short holding-period returns on short-maturity bonds are most often:
**A:** Less than those on long-maturity bonds ✓ (contradicts local expectations)

---

### THEORY COMPARISON TABLE

| Theory | Forward Rate Predicts | Risk Premium? | Curve Shape Driver |
|--------|----------------------|---------------|-------------------|
| Pure Expectations | Future spot exactly | No | Expectations only |
| Local Expectations | Future spot (short-term) | Yes (long-term) | Expectations + some risk |
| Liquidity Preference | Biased HIGH | Yes (↑ with maturity) | Expectations + liquidity |
| Segmented Markets | N/A | N/A | Supply/demand per segment |
| Preferred Habitat | Biased (varies) | Varies by segment | Expectations + supply/demand |

---

# PART 6: YIELD CURVE FACTOR MODELS

## LOS 1.i: Measuring and Managing Yield Curve Risks

---

### THREE-FACTOR MODEL (LITTERMAN-SCHEINKMAN)

Research shows yield curve changes are well-described by three factors:

| Factor | Description | Variance Explained |
|--------|-------------|-------------------|
| **Level** | Parallel shift (all rates move together) | ~75-80% |
| **Steepness** | Non-parallel (short vs long move differently) | ~15-20% |
| **Curvature** | Middle vs ends move differently | ~3-5% |

---

### SHAPING RISK

**Definition:** Sensitivity to changes in yield curve SHAPE (not just level).

**Why it matters:**
- Options sensitive to curve shape
- Different portfolio positions exposed to different maturities
- Hedging requires matching ALL factor exposures

---

### KEY RATE DURATION

Measures sensitivity to yield changes at SPECIFIC maturities.

**Example Portfolio:** $100 each in 1-year, 5-year, 10-year zeros (total $300)

| Maturity | Duration | Key Rate Duration |
|----------|----------|-------------------|
| 1-year | 1 | 1/$300/0.01 = 0.3333 |
| 5-year | 5 | 5/$300/0.01 = 1.6667 |
| 10-year | 10 | 10/$300/0.01 = 3.3333 |
| **Total** | **16** | **5.3333** |

**Key Property:** Sum of key rate durations = Effective duration (for parallel shift)

---

### PORTFOLIO IMPACT FORMULA

$$\%\Delta P \approx -KeyDur_1 \times \Delta z_1 - KeyDur_5 \times \Delta z_5 - KeyDur_{10} \times \Delta z_{10}$$

**Example:** Only 10-year rate rises 100 bps
$$\%\Delta P = -3.3333 \times 0.01 = -3.33\%$$

---

### FACTOR SENSITIVITY CALCULATIONS

**Factor Movement Definitions:**

| Factor | 1-Year Δ | 5-Year Δ | 10-Year Δ |
|--------|----------|----------|-----------|
| Level (+1) | +1 | +1 | +1 |
| Steepness (+1) | -1 | 0 | +1 |
| Curvature (+1) | +1 | 0 | +1 |

**Calculating Factor Durations:**

**Level (D_L):** Sensitivity to parallel shift
$$D_L = KeyDur_1 + KeyDur_5 + KeyDur_{10} = 0.3333 + 1.6667 + 3.3333 = 5.3333$$

**Steepness (D_S):** Sensitivity to steepening
$$D_S = -KeyDur_1 + KeyDur_{10} = -0.3333 + 3.3333 = 3.0$$

**Curvature (D_C):** Sensitivity to curvature change
$$D_C = KeyDur_1 + KeyDur_{10} = 0.3333 + 3.3333 = 3.6667$$

---

### APPLICATION EXAMPLE

If ΔLevel = -0.50%, ΔSteepness = +0.20%, ΔCurvature = +0.10%:

$$\%\Delta P = -5.3333(-0.005) - 3.0(0.002) - 3.6667(0.001)$$
$$= +2.67\% - 0.60\% - 0.37\% = +1.70\%$$

---

### CFAI EXAMPLE 10: Term Structure Dynamics

**Q1:** Most important factor in explaining yield curve changes:
**A:** Level ✓

**Q2:** Short rate decreases 150 bps, long rate decreases 50 bps:
**A:** Steepening resulting from changes in level and steepness ✓

**Q3:** Intermediate rates decrease while short and long unchanged:
**A:** Change in curvature only ✓

**Q4:** Short-term interest rates are typically:
**A:** More volatile than long-term rates ✓

**Q5:** KeyDur_1=0.50, KeyDur_2=0.70, KeyDur_3=0.90. All yields decline 50 bps:
$$\%\Delta P = -0.50(-0.005) - 0.70(-0.005) - 0.90(-0.005) = +1.05\%$$ ✓

---

# PART 7: YIELD VOLATILITY TERM STRUCTURE

## LOS 1.j: Maturity Structure of Yield Volatilities

---

### YIELD VOLATILITY FORMULA

$$\sigma(t,T) = \frac{\sigma[\Delta r(t,T) / r(t,T)]}{\sqrt{\Delta t}}$$

Annualized standard deviation of PROPORTIONAL yield changes.

---

### TYPICAL VOLATILITY TERM STRUCTURE (Aug 2005 - Dec 2007)

| Maturity | 0.25yr | 0.50yr | 1yr | 2yr | 5yr | 10yr | 30yr |
|----------|--------|--------|-----|-----|-----|------|------|
| σ(t,T) | 35.15% | 31.73% | 29.64% | 27.13% | 21.54% | 16.21% | 11.69% |

**Pattern:** Short-term rates MORE volatile than long-term rates.

---

### WHY SHORT RATES ARE MORE VOLATILE

| Driver | Short Rates | Long Rates |
|--------|-------------|------------|
| **Primary factor** | Monetary policy | Inflation expectations |
| **Volatility** | High (policy surprises) | Lower (anchored expectations) |
| **Response speed** | Immediate | Slow-moving |

---

### PRICE VOLATILITY VS RATE VOLATILITY

**Paradox:**
- Short rates = HIGH volatility, LOW duration → Moderate price volatility
- Long rates = LOW volatility, HIGH duration → HIGH price volatility

$$\text{Price Volatility} \propto \text{Rate Volatility} \times \text{Duration}$$

---

# PART 8: MACROECONOMIC FACTORS

## LOS 1.k: Economic Factors Driving Rates and Spreads

---

### BOND RISK PREMIUM

**Definition:** Expected excess return of long-term bonds over short-term bonds.

**Drivers:**
- Duration risk
- Inflation uncertainty
- Liquidity preference

---

### WHAT DRIVES DIFFERENT PARTS OF THE CURVE

| Curve Segment | Primary Driver | Variance Explained |
|---------------|----------------|-------------------|
| Short-term (2yr) | Monetary policy | ~67% |
| Intermediate (5yr) | Mixed | ~50-50 |
| Long-term (10yr+) | Inflation expectations | ~67% |

---

### CURVE MOVEMENTS AND INTERPRETATIONS

| Movement | Short Rates | Long Rates | Typical Cause |
|----------|-------------|------------|---------------|
| **Bull Steepening** | ↓↓ | ↓ | Rate cuts, recession expectations |
| **Bull Flattening** | ↓ | ↓↓ | Flight to quality |
| **Bear Steepening** | ↑ | ↑↑ | Economic recovery, inflation fears |
| **Bear Flattening** | ↑↑ | ↑ | Tight monetary policy, Fed hiking |

**Memory Aid:**
- "Bull" = rates falling = bond prices UP
- "Bear" = rates rising = bond prices DOWN
- "Steep/Flat" = spread widening/narrowing

---

### PORTFOLIO POSITIONING

| Interest Rate View | Duration Strategy | Curve Strategy |
|-------------------|-------------------|----------------|
| Rates will fall | EXTEND duration | Expect long rates to fall more → Barbell |
| Rates will rise | SHORTEN duration | Reduce exposure |
| Curve will steepen | Duration neutral | Short longs, buy shorts |
| Curve will flatten | Duration neutral | Buy longs, short shorts |
| Flight to quality expected | Extend duration | Buy long-end Treasuries |

---

### BULLET VS BARBELL

**Bullet:** Concentrated in single maturity (e.g., all 5-year)
**Barbell:** Split between short and long (e.g., 2-year + 10-year)

Same duration, different curve exposure:
- Barbell benefits from FLATTENING
- Bullet benefits from STEEPENING

---

### CFAI EXAMPLE 11: Building Rate View

**Q1:** Economic growth expected to return. Consistent yield curve change:
**A:** Increase in term spread of long-term over short-term rates ✓

**Q2:** Fed decreases asset purchases. Effect on term spread:
**A:** Amplifies effect of increased economic activity ✓ (both push long yields higher)

---

# PART 9: COMPREHENSIVE PRACTICE PROBLEMS

## Conceptual Questions

**1.** Given spot rates z₁, z₂, z₃, how many forward rates can be calculated?
**Answer:** Three: f₁,₁, f₂,₁, f₁,₂

**2.** Give two interpretations of: "Two-year forward rate one year from now is 2%"
**Answer:** 
(a) 2% makes investor indifferent between 3-year zero or 1-year zero + 2-year reinvestment
(b) 2% can be locked in by buying 3-year vs 1-year zero

**3.** If yield curve is flat, what is the relationship between spot and forward rates?
**Answer:** All forward rates equal the spot rate.

**4.** Which forward rate CANNOT be computed from 1, 2, 3, 4-year spots: (a) f₂,₁ (b) f₂,₂ (c) f₂,₃?
**Answer:** (c) f₂,₃ - requires 5-year spot rate

**5.** Spot curve is upward sloping. The forward rate f₁,₁ is:
**Answer:** Less than f₂,₁ (forward rates increase with later start dates)

---

## Calculation Questions

**6.** z₁=4%, z₂=5%, z₃=6%. Calculate f₁,₁.
$$f_{1,1} = \frac{(1.05)^2}{1.04} - 1 = \frac{1.1025}{1.04} - 1 = 6.01\%$$

**7.** Same rates. Calculate f₁,₂.
$$f_{1,2} = \sqrt{\frac{(1.06)^3}{1.04}} - 1 = \sqrt{1.1449} - 1 = 7.00\%$$

**8.** Same rates. Calculate f₂,₁.
$$f_{2,1} = \frac{(1.06)^3}{(1.05)^2} - 1 = \frac{1.1910}{1.1025} - 1 = 8.03\%$$

**9.** DF₁=0.9524, DF₃=0.8396. Calculate F₁,₂.
$$F_{1,2} = \frac{DF_3}{DF_1} = \frac{0.8396}{0.9524} = 0.8816$$

**10.** z₁=4%, f₁,₁=6%, f₂,₁=8%. Calculate z₃.
$$(1+z_3)^3 = (1.04)(1.06)(1.08) = 1.1906$$
$$z_3 = \sqrt[3]{1.1906} - 1 = 5.99\%$$

---

## Application Questions

**11.** Swap rate 1.00%, Treasury 0.63%. Swap spread?
**Answer:** 37 bps

**12.** Swap spread quoted as 50 bps. 5-year Treasury yields 2%. Fixed rate in 5-year swap?
**Answer:** 2.50%

**13.** 3-month T-bill drops, MRR unchanged. TED spread:
**Answer:** Increases

**14.** For pricing corporate bond using government spot curve, most helpful spread:
**Answer:** Z-spread

**15.** Rolling down yield curve requires buying bonds with maturities:
**Answer:** Longer than investment horizon

---

## More Advanced Questions

**16.** Two-year spot rate z₂=10%. YTM of 2-year 6% coupon bond paying annually. Is y₂ > z₂ or < z₂?
**Answer:** y₂ < z₂ because YTM is weighted average pulled toward z₁ (which is lower in upward-sloping curve)

**17.** Projected spot curve in 2 years is BELOW current forward curve. Bond Z is:
**Answer:** Undervalued (market discounting at higher rate than expected)

**18.** Five-year spot rate from: z₁=2.50%, z₂=3.00%, z₃=3.50%, z₄=4.00%, par₅=4.37%
**Answer:** Bootstrap: z₅ ≈ 4.45%

**19.** Forward rate f₃,₁ from z₃=3.50%, z₄=4.00%:
$$f_{3,1} = \frac{(1.04)^4}{(1.035)^3} - 1 = 5.51\%$$

**20.** Flat yield curve 6%, 3-year bond 6% coupon at par. If curve shifts to flat 7%, expected return:
$$\frac{6 + \frac{6}{1.07} + \frac{106}{(1.07)^2}}{100} - 1 = 4.19\%$$

---

## Theory Questions

**21.** Which theory: Forward rates are unbiased predictors of future spots?
**Answer:** Pure (Unbiased) Expectations Theory

**22.** Which theory: Liquidity premiums exist and increase with maturity?
**Answer:** Liquidity Preference Theory

**23.** Which theory: Each maturity is a separate market?
**Answer:** Segmented Markets Theory

**24.** Which theory: Investors will deviate from preferred maturities if compensated?
**Answer:** Preferred Habitat Theory

**25.** According to liquidity preference, forward rates are biased:
**Answer:** Upward (higher than expected future spots)

---

## Factor Model Questions

**26.** Most important factor explaining yield curve changes:
**Answer:** Level (~75-80%)

**27.** Short rate ↓150 bps, long rate ↓50 bps describes:
**Answer:** Steepening + Level decline

**28.** Portfolio: KeyDur₁=0.33, KeyDur₅=1.67, KeyDur₁₀=3.33. Effective duration?
**Answer:** 5.33

**29.** Same portfolio. Only 10-year rate rises 25 bps. %ΔP?
**Answer:** -3.33 × 0.0025 = -0.83%

**30.** Level factor sensitivity (D_L) equals:
**Answer:** Sum of key rate durations

---

## Volatility and Macro Questions

**31.** Short-term rates are typically:
**Answer:** More volatile than long-term rates

**32.** Long-term yield volatility is primarily linked to:
**Answer:** Inflation expectations

**33.** During economic expansions, central banks typically cause:
**Answer:** Bear flattening (short rates rise more)

**34.** Flight to quality is associated with:
**Answer:** Bull flattening (long rates fall more)

**35.** Falling government budget deficits likely lead to:
**Answer:** Lower bond yields (less supply)

---

## Comprehensive Scenarios

**36-40.** Given: z₁=2.25%, z₂=2.70%, z₃=3.30%, z₄=4.05%, Swap spreads: 0.25%, 0.30%, 0.45%, 0.70%

**36.** Forward price of 1-year bond delivered in 1 year:
$$F_{1,1} = \frac{DF_2}{DF_1} = \frac{1/(1.027)^2}{1/1.0225} = 0.9694$$

**37.** Under stable yield curve, riding the yield curve provides return:
**Answer:** Higher than maturity-matching strategy

**38.** 4-year zero-coupon bond using swap rate, held 2 years. Annual return:
4-year swap = 4.05% + 0.70% = 4.75%
2-year swap = 2.70% + 0.30% = 3.00%
Return = √(1/1.03² ÷ 1/1.0475⁴) - 1 = √(0.9426/0.8306) - 1 = 6.53%

**39.** 2-year corporate bond, 4.15% coupon, Z-spread 65 bps. Price:
z₁' = 2.90%, z₂' = 3.35%
Price = 4.15/1.029 + 104.15/(1.0335)² = 101.54

**40.** Best spread measure for money market risk and liquidity:
**Answer:** MRR-OIS spread (or TED spread)

---

## Advanced Applications (41-56)

**41.** Swap curve better benchmark than government curve when:
**Answer:** Country has large private sector relative to public sector, or illiquid government bond market

**42.** Historical 3-year swap spreads: 1 month ago = 26 bps, 6 months ago = 9 bps, 12 months ago = 78 bps. Lowest credit/liquidity risk:
**Answer:** 6 months ago

**43.** Country A: upward-sloping stable curve. Country B: upward curve expected to invert. Best for riding yield curve:
**Answer:** Country A

**44.** Expected yield curve reversal from upward to downward. Forward curve will be:
**Answer:** Below spot curve (downward slope)

**45.** Assuming future spots = forwards, bonds are:
**Answer:** Fairly valued

**46.** Downward-sloping curve with liquidity premiums indicates:
**Answer:** Expected severe rate declines (deflation expectations)

**47.** Calculate f₃,₂ from z₃=11.80%, z₅=10.70%:
$$f_{3,2} = \sqrt{\frac{(1.107)^5}{(1.118)^3}} - 1 = 9.07\%$$

**48.** Economic expansion, central bank raises rates. Most likely:
**Answer:** Bear flattening

**49.** Budget deficits fall. Effect on yields:
**Answer:** Lower yields (supply decreases)

**50.** Flight to quality associated with:
**Answer:** Bull flattening

**51.** YTM for default-risk-free coupon bond is best viewed as:
**Answer:** Weighted average of spot rates

**52.** Investor expects future spots below forwards. Bond is:
**Answer:** Undervalued (buy)

**53.** 20-year bond, factors: Level=-0.5128%, Steep=-0.3015%, Curve=+0.5227%. 2σ increase in steepness causes:
**Answer:** 2 × (-0.3015%) = -0.603% change in yield

**54.** 5-year bond, 1σ decrease in level and curvature. Level=-0.4352%, Curve=+0.3963%:
$$\Delta y = -(-0.4352\%) - (+0.3963\%) = +0.4352\% - 0.3963\% = +0.0389\%$$

**55.** Local expectations theory predicts 1-month returns on 5-year vs 2-year zeros:
**Answer:** No difference (both earn risk-free rate)

**56.** Segmented markets vs preferred habitat:
**Answer:** Segmented: investors won't move across maturities. Preferred habitat: will move if compensated.

---

# FINAL SUMMARY: KEY FORMULAS

| Concept | Formula |
|---------|---------|
| Discount Factor | DF_N = 1/(1+z_N)^N |
| Forward Pricing | DF_B = DF_A × F_{A,B-A} |
| Forward Rate Model | (1+z_B)^B = (1+z_A)^A × (1+f_{A,B-A})^{B-A} |
| Spot as Geometric Average | (1+z_T)^T = (1+z₁)(1+f₁,₁)...(1+f_{T-1,1}) |
| Swap Rate | Σ(s_T/(1+z_t)^t) + 1/(1+z_T)^T = 1 |
| Swap Spread | Swap Rate - Government Yield |
| TED Spread | 3m MRR - 3m T-bill |
| Key Rate Duration Impact | %ΔP ≈ -ΣKeyDur_i × Δz_i |

---

# EXAM DAY CHECKLIST

✅ Can calculate any forward rate from spot rates
✅ Know when forward curve is above/below spot curve
✅ Can bootstrap spot rates from par rates
✅ Understand YTM ≠ expected return (unless flat curve)
✅ Can calculate rolldown returns
✅ Know all 5 term structure theories and their predictions
✅ Can calculate key rate and factor durations
✅ Understand volatility term structure (short > long)
✅ Can identify curve movements (bull/bear, steep/flat)
✅ Can position portfolio based on rate expectations

---

*These notes cover 200% of LM1 content. Use for comprehensive exam preparation.*
