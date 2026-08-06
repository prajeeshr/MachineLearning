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