# Python-Tutorial
This notebook serves as a comprehensive collection of Python concepts, algorithms, and best practices.
# Notebook : python_tutorial summary 

# Notebook Summary

This notebook serves as a comprehensive collection of Python concepts, algorithms, and best practices. Here is a summary of the key sections covered:

1. **Data Manipulation & Math Utilities**:
   * Utilizing `numpy.clip()` to restrict array values within a specified range.
   * Basic mathematical operations such as addition, subtraction, area calculation of a triangle, variable swapping, and generating random numbers.
   * Conversion utilities (kilometers to miles, Celsius to Fahrenheit) and displaying calendar tables using the built-in `calendar` module.
   * Solvers for quadratic equations, identifying prime numbers in specific intervals, and computing Factorials (both iterative and recursive).
   * Algorithms to find the Least Common Multiple (LCM) and Highest Common Factor (HCF) of two numbers, as well as generating Fibonacci sequences.

2. **Array and Matrix Operations**:
   * Finding the sum and the largest element in an array.
   * Performing array rotations and split-and-add operations.
   * Checking if an array is monotonic.
   * Fundamental matrix operations including addition, multiplication, and transposing matrices.

3. **Python Styling & Programming Conventions (PEP 8)**:
   * **Class Names**: Demonstrating the `CapWords` naming convention.
   * **Function Names**: Demonstrating snake_case (`lowercase_with_underscores`) naming conventions.
  
   # Executive Summary: FinRoute Case Study

This notebook demonstrates a structured, **9-part financial routing and risk analytics case study** using Python and Pandas. It begins with core Series and DataFrame fundamentals, processes a simulated transaction data lake containing 10,000 transactions, and concludes with actionable commercial insights across three analytical phases.

## Notebook Breakdown

### 1\. Pandas Foundations (Parts 1–3)

**Series Handling**

- Demonstrates Series creation from lists and dictionaries.
- Explores vectorized operations, filtering, and index alignment.
- Uses `.add(fill_value=0)` to avoid unintended `NaN` values when combining Series with mismatched indices.

**DataFrame Inspection**

- Establishes a standard analytical inspection checklist using:
  - `.shape`
  - `.isnull().sum()`
  - `.duplicated()`
  - `.info()`
  - `.describe()`

**Subsetting and Indexing**

- Distinguishes label-based selection with `.loc` from position-based selection with `.iloc`.
- Demonstrates dynamic row filtering using `.query()`.
- Uses `.isin()` for exact-value inclusion and `.str.contains()` for text-based matching.

### 2\. Data Lake Setup and Cardinality Mapping (Part 4)

The notebook generates simulated datasets representing the core components of a payment processing environment.

| Dataset | Description |
| --- | --- |
| `df_txns` | 10,000 credit card transaction records, including routing destinations and transaction statuses. |
| `df_merchants` | Profiles for 50 merchants, including Merchant Category Codes (MCCs) and historical chargeback rates. |
| `df_costs` | Fixed and variable processing costs for two acquiring banks: Bank A and Bank B. |

**Entity Relationship and Cardinality Validation**

- Performs cardinality checks to validate the relationship between transactions and merchant profiles.
- Confirms the expected **many-to-one (N:1)** relationship between transaction records and merchant records.
- Helps prevent unintended row multiplication during analytical joins and merges.

### 3\. Analytics Core (Parts 5–9)

#### Part 5: Baseline Exploratory Data Analysis (EDA)

The baseline analysis establishes the following transaction performance metrics:

| Metric | Result |
| --- | --- |
| Transaction success rate | 88.13% |
| Server timeout rate (E05) | 7.56% |
| Insufficient funds rate (E01) | 4.31% |
| Average transaction value | $150.05 |

The analysis indicates that transaction values are positively skewed, with larger transactions contributing disproportionately to the overall transaction value.

#### Phase 1: Quantifying Lost Revenue (Part 6)

The notebook distinguishes between recoverable routing failures and non-recoverable consumer-side declines.

- **E05 — Server Timeouts:** Classified as recoverable errors when they occur on Bank A, because routing eligible transactions to a more reliable processor may improve authorization outcomes.
- **Estimated revenue opportunity:** Approximately **$2,255.89 per day**, equivalent to roughly **$823,000 annually**, in potentially lost merchant discount rate (MDR) commissions.
- **E01 — Insufficient Funds:** Classified as consumer-side issues that generally cannot be resolved through network routing optimization alone.

#### Phase 2: Algebraic Break-Even Analysis (Part 7)

This phase evaluates when Bank B's higher processing costs and higher reliability make it more profitable than Bank A's lower costs and lower reliability.

- Formulates the break-even condition by equating the expected profits of both processors:
  $$
  \text{Profit}_A = \text{Profit}_B
  $$
- Solves for the transaction value at which the two routing options have equal expected profitability.
- Identifies a break-even transaction value of **$21.43**.

**Key insight:** Under the notebook's modeled assumptions, Bank B becomes the more cost-effective routing option for transactions above $21.43.

#### Phase 3: Chargeback Risk Profiling (Part 8)

The notebook merges `df_txns` with `df_merchants` to analyze chargeback exposure across merchant industries.

- Aggregates chargeback rates and expected losses by Merchant Category Code (MCC).
- Identifies **Digital Goods**, with an estimated expected daily loss of approximately **$15,001**, as a major risk segment.
- Highlights **Travel**, with an estimated expected daily loss of approximately **$11,685**, as another high-risk segment.

These findings help identify merchant categories that may require enhanced fraud monitoring, risk controls, or targeted mitigation strategies.

#### Part 9: What-If Smart Routing Simulation

The final phase simulates a dynamic routing strategy that redirects eligible E05 server-timeout transactions from Bank A to Bank B.

**Routing strategy**

- Identifies transactions experiencing E05 server timeouts on Bank A.
- Applies the **$21.43 break-even threshold** to prioritize transactions for which Bank B is expected to be more profitable.
- Uses the modeled success rates of **85.6% for Bank A** and **98.3% for Bank B** to estimate the potential recovery opportunity.

**Simulation results**

| Metric | Result |
| --- | --- |
| Transactions recovered | 656 |
| Additional daily MDR revenue | $282.62 |
| Annualized revenue uplift | $103,158 |

The simulation suggests that selective, value-based routing can improve transaction recovery and generate additional merchant fee revenue without moving every transaction to the higher-cost processor.

## Conclusion and Business Impact

The FinRoute case study demonstrates how Python and Pandas can support data-driven payment routing and risk management decisions.

By combining foundational data manipulation, transaction-level exploratory analysis, processor break-even modeling, merchant chargeback profiling, and what-if simulation, the notebook identifies opportunities to improve payment success rates and commercial performance.

The key business takeaways are:

1. **Recover lost revenue:** Identify recoverable server timeouts and route eligible transactions to a more reliable processor.
2. **Optimize processing costs:** Use transaction-value thresholds to balance processor reliability against processing expenses.
3. **Manage merchant risk:** Identify high-exposure merchant categories to support targeted risk mitigation.
4. **Quantify routing impact:** Estimate transaction recovery and incremental revenue before implementing a routing strategy in production.


   * **Program Structure**: Standard structure showcasing the usage of `def main()` and the `if __name__ == '__main__':` boilerplate.

4. **Input, Output, and Variables**:
   * Interacting with the user using the `input()` function.
   * Different string formatting techniques including formatted string literals (f-strings) and the `str.format()` method.
   * Declaring and updating variables with different data types (strings, floats, expressions).
