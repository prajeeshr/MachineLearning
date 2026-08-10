# Statistics Study Guide for Data Science & Machine Learning

**Purpose**: Quick reference guide for fundamental statistics concepts needed for DS/ML roles.  
**Last Updated**: August 2026  
**Status**: Foundation concepts completed

---

## Table of Contents

1. [Types of Statistics](#types-of-statistics)
2. [Data Classification](#data-classification)
3. [Descriptive Measures](#descriptive-measures)
4. [Probability Fundamentals](#probability-fundamentals)
   - [A Priori Classical Probability](#a-priori-classical-probability)
   - [Empirical Probability](#empirical-probability)
   - [Law of Large Numbers](#law-of-large-numbers)
   - [Comparison: A Priori vs Empirical vs Subjective](#comparison-a-priori-vs-empirical-vs-subjective)
   - [Combining Approaches](#combining-approaches-real-world-decision-making)
   - [Subjective Probability](#subjective-probability)
   - [Marginal Probability](#marginal-probability)
   - [Odds](#odds)
   - [Prior and Posterior Probability](#prior-and-posterior-probability)
5. [Probability Rules](#probability-rules)
6. [Decision Trees](#decision-trees)

---

## Types of Statistics

### Descriptive Statistics
Summarizes and organizes data to describe its main features, without drawing conclusions beyond the data itself.

**Key Components:**
- Measures of Central Tendency: mean, median, mode
- Measures of Dispersion: variance, standard deviation, range, IQR
- Data Visualization: histograms, box plots, scatter plots
- Frequency Distributions

**When to use**: Exploratory Data Analysis (EDA), understanding your data

---

### Inferential Statistics
Uses sample data to make predictions, generalizations, or decisions about a larger population.

**Key Components:**
- Hypothesis Testing: t-tests, chi-square, ANOVA
- Regression Analysis: linear, logistic, multiple regression
- Confidence Intervals and Estimation
- Correlation Analysis

**When to use**: Making predictions, validating models, A/B testing

---

## Data Classification

### By Nature

| Type | Definition | Examples |
|---|---|---|
| **Qualitative (Categorical)** | Non-numeric, describes qualities | Gender, color, email category |
| **Quantitative (Numerical)** | Numeric, can be measured | Height, salary, age |

### By Measurement Scale

| Scale | Properties | Example |
|---|---|---|
| **Nominal** | Categories only, no order | Blood type: A, B, AB, O |
| **Ordinal** | Ordered categories, unequal intervals | Satisfaction: Poor → Fair → Good → Excellent |
| **Interval** | Ordered, equal intervals, no true zero | Temperature: 0°C ≠ "no temperature" |
| **Ratio** | Ordered, equal intervals, true zero | Height (cm), Weight (kg), Income ($) |

### By Source

- **Primary Data**: Collected firsthand by you (surveys, experiments)
- **Secondary Data**: Already collected by someone else (published reports, databases)

### By Time Dimension

- **Cross-sectional**: Data collected at one point in time across multiple subjects
- **Time Series**: Data collected over time for the same subject
- **Panel/Longitudinal**: Multiple subjects observed over multiple time periods

---

## Descriptive Measures

### Variance and Standard Deviation

#### What is Variance?
**Variance measures how spread out your data is** — how far numbers are from the average.

```
Variance = Average squared distance from the mean
```

**Interpretation:**
- Low variance → data clustered together
- High variance → data spread out

#### What is Standard Deviation?
**Standard Deviation is the square root of variance** — easier to interpret because it's in the same units as your data.

```
Standard Deviation = √(Variance)
```

#### Example: Student Test Scores

Suppose students have:
- Average score: 70
- Standard Deviation: 10

**Interpretation**: On average, students deviate from 70 by about 10 points.
- Most students score between 60-80
- Very few score outside 40-100

#### The 68-95-99.7 Rule

For normally distributed data:
- **68%** of data falls within ±1 SD from mean
- **95%** of data falls within ±2 SDs from mean
- **99.7%** of data falls within ±3 SDs from mean

---

### Z-Score

#### What is a Z-Score?
**A Z-score tells you how many standard deviations away from the average a specific value is.**

```
Z-score = (Your Value - Mean) / Standard Deviation
Z-score = (X - μ) / σ
```

#### Interpretation Guide

| Z-Score | Interpretation | Percentile |
|---|---|---|
| 0 | Exactly at average | 50th |
| +1 | 1 SD above average | 84th |
| +2 | 2 SDs above average | 98th |
| +3 | 3 SDs above average | 99.7th |
| -1 | 1 SD below average | 16th |
| -2 | 2 SDs below average | 2nd |

**Rule of Thumb for Outliers:**
- Z-score between -3 and +3 = Normal value ✅
- Z-score < -3 or > +3 = Outlier/Unusual ⚠️

#### Example: Sales Performance

Daily sales have:
- Average: $10,000
- Standard Deviation: $2,000

Monday's sales: $16,000

```
Z-score = (16,000 - 10,000) / 2,000 = 3.0
```

**Interpretation**: Sales were 3 SDs above average → Extremely high! Investigate what happened.

---

## Probability Fundamentals

### A Priori Classical Probability

#### Definition
**Probability of an event calculated BEFORE any experiment happens, based on logical reasoning.**

```
A Priori Probability = Favorable Outcomes / Total Possible Outcomes
```

**Key Characteristics:**
- Theoretical, not experimental
- Known before testing
- Based on equally likely outcomes
- Exact value

#### Examples

**Coin Flip:**
```
P(Heads) = 1/2 = 0.5 or 50%
```

**Rolling a Dice:**
```
P(Rolling a 3) = 1/6 ≈ 16.7%
```

**Drawing a Card (Ace):**
```
P(Ace) = 4/52 = 7.7%
```

---

### Empirical Probability

#### Definition
**Probability of an event based on actual observed data from experiments or real-world observations.**

Also called **Experimental Probability** or **Frequency Probability**.

```
Empirical Probability = Observed Favorable Outcomes / Total Trials Conducted
```

**Key Characteristics:**
- Based on real data and observations
- Calculated AFTER conducting experiments
- Can vary based on sample size
- Gets more accurate with more trials (Law of Large Numbers)

#### Examples

**Coin Flip Experiment**

Theoretical (A Priori): P(Heads) = 0.5

Empirical (100 flips): You observe 52 heads
```
P(Heads) = 52/100 = 0.52
```

Empirical (1,000 flips): You observe 501 heads
```
P(Heads) = 501/1000 = 0.501
```

Notice: As you increase trials, empirical probability approaches theoretical (0.5)

**Website Click-Through Rate**

A Priori (design estimate): "We expect 3% CTR"

Empirical (after testing): 
- Campaign showed 150 clicks from 5,000 impressions
```
P(Click) = 150/5000 = 0.03 or 3%
```

**Quality Control in Manufacturing**

A Priori (design target): Defect rate = 2%

Empirical (after producing 1,000 units):
- 25 units were defective
```
P(Defective) = 25/1000 = 0.025 or 2.5%
```

Slightly higher than target. Need to investigate.

---

### Law of Large Numbers

**As you repeat an experiment many times, empirical probability approaches a priori (theoretical) probability.**

#### Coin Flip Example

| Number of Flips | Heads Observed | Empirical Probability | Distance from 0.5 |
|---|---|---|---|
| 10 | 6 | 0.60 | 0.10 |
| 100 | 48 | 0.48 | 0.02 |
| 1,000 | 501 | 0.501 | 0.001 |
| 10,000 | 4,998 | 0.4998 | 0.0002 |
| ∞ | → 50,000 | → **0.5000** | → 0 |

As you flip more times, you get closer to the theoretical 0.5!

---

### Comparison: A Priori vs Empirical vs Subjective

| Aspect | A Priori Classical | Empirical | Subjective |
|---|---|---|---|
| **Based on** | Logic & theory | Observed data | Personal judgment |
| **When known** | Before experiment | After experiment | Before or during |
| **Requires data?** | No | Yes | No |
| **Objective?** | Yes | Yes | No (varies by person) |
| **Example** | P(Heads) = 0.5 | P(Heads) = 0.52 from 100 flips | "I think 0.6 based on my intuition" |
| **Accuracy** | Perfect (if assumptions hold) | Real-world accurate | Depends on expertise |
| **Used in** | Bayesian prior estimate | Model validation | Bayesian prior beliefs |

---

### Combining Approaches: Real-World Decision Making

**Step 1: Start with A Priori (Theoretical Expectation)**
```
Prior belief: P(Click) = 0.03 (3% CTR based on design)
```

**Step 2: Gather Empirical Data (Real Observations)**
```
Campaign data: 150 clicks from 5,000 impressions
Empirical: P(Click) = 0.03 (exactly matches!)
```

**Step 3: Update with Subjective Judgment (Bayesian Approach)**
```
Final belief: 0.03 with high confidence
(Theory + data + experience = strong belief)
```

This is the **Bayesian approach**: Combine prior expectations with empirical evidence!

---

### Subjective Probability

#### Definition
**Probability based on personal judgment, experience, belief, or intuition — NOT on logical calculation.**

**Key Characteristics:**
- Personal and varies from person to person
- Based on experience, expertise, and beliefs
- Can be influenced by biases
- Used in Bayesian statistics as "prior" beliefs

#### Examples

**Stock Investment**
- Conservative investor: "Apple stock will go up 20% with 30% probability"
- Aggressive investor: "Apple stock will go up 20% with 70% probability"

**Startup Success**
- You: "I believe 30% probability (founders are experienced)"
- Another investor: "I believe 50% probability (great business model)"

#### Common Biases

⚠️ **Overconfidence Bias**: Overestimating your prediction accuracy

⚠️ **Confirmation Bias**: Believing things confirming your existing beliefs

⚠️ **Availability Bias**: Overweighting recent or memorable events

---

### Bayesian Approach

Combines subjective prior beliefs with empirical data:

```
Posterior = Prior × Likelihood / Evidence
P(θ | Data) ∝ P(Data | θ) × P(θ)
```

**Example: Email Spam**
- Prior: "I believe 20% of emails are spam" (subjective)
- Data: "Email contains 'FREE MONEY'"
- Posterior: "Updated belief: 85% likely spam" (after seeing content)

---

### Marginal Probability

#### Definition
**Probability of a single event occurring, ignoring or "marginalizing out" all other events.**

The probability of one variable, without considering any other variables. Called "marginal" because it appears in the margins (edges) of a contingency table.

```
Marginal Probability = Probability of one event
                       (regardless of other events)
```

#### Examples

**From a Deck of Cards:**

Marginal P(Red card) = 26/52 = 0.5
- We ignore the rank (Ace, King, etc.)

Marginal P(King) = 4/52 ≈ 0.077
- We ignore the color (red or black)

**From Student Data:**

Marginal P(Female) = Total females / Total students
- We ignore their major, GPA, year, etc.

Marginal P(Math major) = Total Math majors / Total students
- We ignore their gender, year, etc.

#### Contingency Table Example

Example: **Gender vs Job Satisfaction** (100 employees)

```
              Satisfied    Not Satisfied    Total (Marginal)
Male              20           30              50
Female            35           15              50
Total (Marginal)  55           45             100
```

**Marginal Probabilities from margins:**

From rows:
- P(Male) = 50/100 = 0.50
- P(Female) = 50/100 = 0.50

From columns:
- P(Satisfied) = 55/100 = 0.55
- P(Not Satisfied) = 45/100 = 0.45

These totals appear in the table's **margins** (edges), hence "marginal"!

#### Real-World Application: Email Spam Detection

```
                Spam    Not Spam    Total
Contains FREE   40         10         50
No FREE        60         90        150
Total         100        100        200
```

**Marginal Probabilities:**

```
P(Contains "FREE") = 50/200 = 0.25
P(Is Spam) = 100/200 = 0.50
P(Is Not Spam) = 100/200 = 0.50
```

#### Relationship to Other Probabilities

| Type | Definition | Example |
|---|---|---|
| **Marginal** | One event, ignore others | P(Spam) = 0.50 |
| **Joint** | Two events together | P(Spam AND "FREE") = 0.20 |
| **Conditional** | One given another | P(Spam \| "FREE") = 0.80 |

**Formula Connection:**
```
Joint = Marginal × Conditional
P(A AND B) = P(A) × P(B|A)
```

#### Why it Matters in Data Science

✅ **Baseline Probabilities**: Marginal P(Target) is your baseline before considering features

✅ **Feature Independence**: Check if features are independent from target

✅ **Bayesian Prior**: Prior probability P(θ) is marginal before seeing data

✅ **Model Calibration**: Predicted probabilities should match marginal target distribution

---

### Odds

#### Definition
**Odds express the ratio of the likelihood that an event will happen to the likelihood that it won't happen.**

A different way to express probability using a ratio of favorable to unfavorable outcomes.

```
Odds = P(Event) / P(NOT Event)
     = P(Event) / (1 - P(Event))
```

#### Probability vs Odds

| Aspect | Probability | Odds |
|---|---|---|
| **Formula** | P(A) | P(A) / P(NOT A) |
| **Range** | 0 to 1 (or 0% to 100%) | 0 to infinity |
| **Example** | 0.75 or 75% | 3:1 or 3 |
| **Interpretation** | 75 out of 100 chance | 3 successes per 1 failure |
| **Use in ML** | Direct predictions | Logistic regression |

#### Converting Between Probability and Odds

**Probability to Odds:**
```
Odds = P / (1 - P)
```

**Odds to Probability:**
```
P = Odds / (1 + Odds)
```

#### Example: Medical Diagnosis

**If disease probability = 0.25 (25%):**

Convert to Odds:
```
Odds = 0.25 / (1 - 0.25)
     = 0.25 / 0.75
     = 0.333 or 1:3
```

**Interpretation**: For every 1 person with disease, 3 don't have it.

**If odds of recovery = 2:**

Convert to Probability:
```
P = 2 / (1 + 2)
  = 2/3 ≈ 0.667 or 66.7%
```

#### Real-World Application: Sports Betting

**If a team has 2:1 odds to win:**

```
Odds = 2
P(Win) = 2 / (2 + 1) = 2/3 ≈ 66.7%
```

The team has a **66.7% chance** to win.

**If odds are 1:5 (underdog):**

```
Odds = 1/5 = 0.2
P(Win) = 0.2 / (1 + 0.2) = 0.167 ≈ 16.7%
```

The team has only a **16.7% chance** to win.

#### Odds Ratio (Comparing Two Groups)

**Odds Ratio compares odds between two groups.**

```
Odds Ratio = Odds(Group 1) / Odds(Group 2)
```

**Example: Drug Effectiveness**

Group A (Drug): 80 recovered, 20 didn't
- Odds = 80/20 = 4

Group B (Placebo): 60 recovered, 40 didn't
- Odds = 60/40 = 1.5

```
Odds Ratio = 4 / 1.5 ≈ 2.67
```

**Interpretation**: The drug group is **2.67 times more likely** to recover than placebo.

#### Odds in Machine Learning: Logistic Regression

**Logistic Regression models log-odds of an event:**

```
log(Odds) = β₀ + β₁X₁ + β₂X₂ + ...
```

The regression coefficients directly affect the log-odds, which are then converted back to probability for predictions.

**Why this matters**: Understanding odds helps you interpret logistic regression coefficients and understand how features affect the probability of outcomes.

#### Quick Comparison: Probability vs Odds

| Scenario | Probability | Odds | Interpretation |
|---|---|---|---|
| Fair coin | 0.5 (50%) | 1:1 (or 1) | Equal chance |
| Rolling a 6 | 0.167 (16.7%) | 1:5 (or 0.2) | 1 success per 5 failures |
| High probability | 0.80 (80%) | 4:1 (or 4) | 4 successes per 1 failure |
| Low probability | 0.10 (10%) | 1:9 (or 0.111) | 1 success per 9 failures |

---

### Prior and Posterior Probability

#### Definition

**Prior Probability (P(A))**
- Your belief about an event **BEFORE** seeing any evidence
- Based on previous experience, general knowledge, or assumptions
- Your "initial guess"

**Posterior Probability (P(A|B))**
- Your belief about an event **AFTER** seeing evidence B
- Updated belief based on prior + new evidence
- Your "revised guess" after learning something new

```
Prior = Belief BEFORE evidence
Posterior = Belief AFTER evidence
```

#### Simple Analogy: Weather

**Prior Probability (Before checking weather forecast):**
```
"It's monsoon season, so there's a 60% chance of rain today."
Prior P(Rain) = 0.60
```

**Posterior Probability (After seeing weather app):**
```
"Weather app shows storm clouds approaching my area."
Posterior P(Rain | Storm clouds) = 0.95
```

You **updated your belief** from 60% to 95% after seeing evidence!

#### Real-World Examples

**Example 1: Medical Test**

Prior (Before test):
```
"The disease is rare in my age group, only 1% chance I have it"
Prior P(Disease) = 0.01
```

Posterior (After positive test):
```
"Test came back positive. Given the test accuracy, 
 I estimate there's an 80% chance I have the disease"
Posterior P(Disease | Positive Test) = 0.80
```

Your belief jumped from 1% to 80% based on test evidence!

**Example 2: Email Spam Detection**

Prior (Before reading):
```
"Historically, 20% of my emails are spam"
Prior P(Spam) = 0.20
```

Posterior (After seeing email content):
```
"Contains 'FREE MONEY!!!' and unknown sender"
Posterior P(Spam | Email Content) = 0.95
```

The suspicious content updated your belief from 20% to 95%!

**Example 3: Job Interview**

Prior (Before interview):
```
"Typically 30% of candidates who interview get hired"
Prior P(Hired) = 0.30
```

Posterior (After great interview):
```
"Nailed all questions, interviewer gave positive signals"
Posterior P(Hired | Interview Performance) = 0.80
```

The interview evidence increased your belief from 30% to 80%!

#### How They Connect: Bayes' Theorem

The relationship between prior and posterior:

```
Posterior = (Prior × Likelihood of Evidence) / Probability of Evidence

P(A|B) = P(B|A) × P(A) / P(B)
```

**Simple interpretation:**
```
Updated Belief = Old Belief × How much new evidence changes it
```

#### Comparison Table

| Aspect | Prior | Posterior |
|---|---|---|
| **When known** | BEFORE seeing evidence | AFTER seeing evidence |
| **Based on** | General knowledge, experience | Prior + specific evidence |
| **Example** | 5% of suspects are guilty | 90% guilty after fingerprints |
| **Purpose** | Starting point | Updated conclusion |
| **Certainty** | Lower | Higher (usually) |

#### Key Insight: Prior Matters a Lot

Your prior belief **significantly affects** your posterior belief.

**Example: Same positive COVID test, two different priors**

Doctor A (Low prior):
```
Prior: "COVID is rare in this area, 2% chance"
After positive test → Posterior = 30%
(Only 30% confident because prior was low)
```

Doctor B (High prior):
```
Prior: "Patient traveled to hotspot, 50% chance"
After positive test → Posterior = 98%
(98% confident because prior was high)
```

**Same test, different conclusions!** Because their priors were different.

#### Updating Beliefs: Continuous Process

You don't stop at one posterior. New evidence keeps updating your beliefs:

```
Prior P(Guilty) = 0.05
    ↓ (Find fingerprints)
Posterior = 0.60
    ↓ (Witness confirms ID)
New Posterior = 0.85
    ↓ (Alibi witness contradicts)
Final Posterior = 0.40
```

**Previous posterior becomes the next prior!** This is continuous belief updating.

#### Why This Matters in Data Science

✅ **Handling Uncertainty** - Update beliefs as you gather more data

✅ **Domain Knowledge** - Prior captures expert opinion and existing knowledge

✅ **Sequential Learning** - Perfect for real-time decision making

✅ **Bayesian ML Models** - Explicitly model and update uncertainty

✅ **Understanding Decisions** - How evidence should change your mind

#### Real Application: Email Spam Filter

**Initially (before any data):**
```
Prior P(Spam) = 0.20 (20% of emails are typically spam)
```

**After seeing one email:**
```
Contains "FREE MONEY" → Posterior P(Spam) = 0.70
```

**After seeing multiple features:**
```
+ Unknown sender → Posterior P(Spam) = 0.85
+ Suspicious link → Posterior P(Spam) = 0.92
+ Grammar errors → Posterior P(Spam) = 0.96
```

Each feature updates your belief higher!

---

## Probability Rules

### Mutually Exclusive Events

#### Definition
**Events that CANNOT happen at the same time. If one occurs, the other cannot.**

```
Mutually Exclusive = P(A AND B) = 0
```

#### Examples

- Coin flip: **Heads** OR **Tails** (can't be both)
- Email: **Spam** OR **Not Spam** (can't be both)
- Dice: **Rolling a 3** OR **Rolling a 5** (can't happen together)
- Traffic light: **Red** OR **Green** (can't both be on)

#### Venn Diagram

```
Mutually Exclusive Events
    Event A          Event B
   (Heads)          (Tails)
   ┌────┐          ┌────┐
   │    │          │    │
   └────┘          └────┘
   
   No overlap!
```

---

### Addition Rule

#### Definition
**Calculates the probability of two events happening (Event A OR Event B).**

#### Formulas

**For Mutually Exclusive Events:**
```
P(A OR B) = P(A) + P(B)
```

**For Non-Mutually Exclusive Events:**
```
P(A OR B) = P(A) + P(B) - P(A AND B)
```

The subtraction accounts for overlap (we don't want to count it twice).

#### Example 1: Rolling a Dice (Mutually Exclusive)

**What's the probability of rolling a 3 OR a 5?**

```
P(3 OR 5) = P(3) + P(5)
          = 1/6 + 1/6
          = 2/6 = 1/3 ≈ 33%
```

#### Example 2: Drawing a Card (Non-Mutually Exclusive)

**What's the probability of drawing a Red card OR a King?**

- P(Red) = 26/52
- P(King) = 4/52
- P(Red AND King) = 2/52 (Red kings exist!)

```
P(Red OR King) = 26/52 + 4/52 - 2/52
               = 28/52 = 7/13 ≈ 54%
```

We subtract 2/52 because Red Kings were counted in both categories.

---

### Independent Events

#### Definition
**Events where the outcome of one does NOT affect the outcome of another.**

One event happening doesn't change the probability of the other event.

#### Examples

- **Coin flips**: First flip being heads doesn't affect second flip probability
- **Dice rolls**: Previous roll doesn't affect next roll
- **Independent customers**: One customer's purchase doesn't affect another's
- **Different tests**: Passing math doesn't determine chemistry score

#### Non-Examples (Dependent Events)

- **Drawing without replacement**: Removing a card changes remaining deck
- **Weather**: Monday's weather influences Tuesday's weather
- **Sequential approvals**: Passing stage 1 affects probability of stage 2

---

### Multiplication Rule

#### Definition
**Calculates the probability of two events happening together (Event A AND Event B).**

#### Formulas

**For Independent Events:**
```
P(A AND B) = P(A) × P(B)
```

**For Dependent Events:**
```
P(A AND B) = P(A) × P(B|A)
```

Where P(B|A) = "Probability of B given A already happened"

#### Example 1: Two Coin Flips (Independent)

**What's the probability of Heads AND Heads?**

```
P(H AND H) = P(H) × P(H)
           = 0.5 × 0.5
           = 0.25 or 25%
```

#### Example 2: Two Independent Tests

**Pass Math (80%) AND Pass Logic (70%)?**

```
P(Both pass) = 0.80 × 0.70
             = 0.56 or 56%
```

#### Example 3: Drawing Without Replacement (Dependent)

**Drawing 2 Aces from a deck?**

- First draw: P(Ace) = 4/52
- Second draw: P(Ace | First Ace) = 3/51 (only 3 aces left, 51 cards left)

```
P(2 Aces) = 4/52 × 3/51
          = 12/2652 ≈ 0.45%
```

Notice: Probability changed for second draw because first draw affects it.

#### Real-World Application: System Reliability

A system has 3 independent components:
- Component A: P(Works) = 0.95
- Component B: P(Works) = 0.98
- Component C: P(Works) = 0.99

**What's P(Entire system works)?**

```
P(System) = 0.95 × 0.98 × 0.99
          = 0.922 or 92.2%
```

So there's a **7.8% chance the system fails** (at least one component fails).

---

## Decision Trees

### When to Use Addition Rule (OR)

```
Question: "What's P(A OR B)?"
                    ↓
    Are A and B mutually exclusive?
                    ↓
        ┌───────────┴───────────┐
        ↓ YES                    ↓ NO
    
    P(A OR B) =              P(A OR B) =
    P(A) + P(B)              P(A) + P(B) - P(A AND B)
    
Example:                     Example:
P(3 OR 5 on dice) =          P(Red OR King) =
1/6 + 1/6                    26/52 + 4/52 - 2/52
```

---

### When to Use Multiplication Rule (AND)

```
Question: "What's P(A AND B)?"
                    ↓
    Are A and B independent?
                    ↓
        ┌───────────┴───────────┐
        ↓ YES                    ↓ NO
    
    P(A AND B) =             P(A AND B) =
    P(A) × P(B)              P(A) × P(B|A)
    
Example:                     Example:
P(H AND H) =                 P(2 Aces) =
0.5 × 0.5                    4/52 × 3/51
```

---

## Quick Reference: Choosing Your Rule

| Situation | Rule | Formula |
|---|---|---|
| "Event A OR Event B" (same can't happen) | Addition (Mutually Exclusive) | P(A) + P(B) |
| "Event A OR Event B" (can overlap) | Addition (Non-Mutually Exclusive) | P(A) + P(B) - P(A∩B) |
| "Event A AND Event B" (independent) | Multiplication (Independent) | P(A) × P(B) |
| "Event A AND Event B" (dependent) | Multiplication (Dependent) | P(A) × P(B\|A) |

---

## Preparation Priority for DS/ML Interviews

### Must Know (Foundation)
- ✅ Descriptive statistics (mean, variance, SD, Z-score)
- ✅ Data types and classification
- ✅ Probability basics (A priori, subjective)
- ✅ Mutually exclusive events & Addition rule
- ✅ Independent events & Multiplication rule

### Very Important (Core)
- Hypothesis testing and p-values
- Confidence intervals
- Correlation and causation
- Regression analysis

### Advanced (Specialized)
- Bayesian statistics
- Time series analysis
- Causal inference
- Experimental design

---

## Common Interview Questions

**Q: "Explain variance and standard deviation"**
> Variance measures how spread out data is. Standard deviation is its square root, making it easier to interpret because it's in the same units as your data. For example, if height has mean 170cm and SD 8cm, most people are between 162-178cm.

**Q: "What does a Z-score of 2.5 mean?"**
> A Z-score of 2.5 means the value is 2.5 standard deviations above the average — very unusual. Using the 68-95-99.7 rule, about 99.4% of values are below this, so it's in the extreme tail of the distribution.

**Q: "Explain mutually exclusive events and the Addition Rule"**
> Mutually exclusive events cannot both happen simultaneously. For example, a coin flip can be heads or tails, but not both. The Addition Rule for these is simple: P(A OR B) = P(A) + P(B). If events can overlap, we subtract the overlap: P(A OR B) = P(A) + P(B) - P(A AND B).

**Q: "When do you use the Multiplication Rule?"**
> The Multiplication Rule calculates P(A AND B). For independent events, simply multiply: P(A AND B) = P(A) × P(B). For dependent events, we account for how the first event affects the second: P(A AND B) = P(A) × P(B|A).

---

## Recommended Kaggle Datasets for Practice

### Beginner
- **Iris Dataset**: Learn descriptive statistics, distributions, correlation
- **Titanic**: Data cleaning, EDA, categorical variables
- **Housing Prices**: Linear regression, correlations, outlier detection

### Intermediate
- **Adult Income**: Hypothesis testing, categorical analysis
- **Credit Card Fraud**: Anomaly detection, imbalanced data, Z-scores
- **E-commerce Sales**: Time series patterns, aggregation

### Advanced
- **Stock Market Data**: Time series analysis
- **Medical Datasets**: Hypothesis testing, conditional probability

---

## Notes Section

*Use this area to add your own notes, examples, and clarifications as you learn.*

---

**Document Control**: This is version 1.0 of the study guide. New sections will be added without modifying existing content. Updates will be marked with date stamps.