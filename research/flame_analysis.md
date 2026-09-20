# FLAME Analysis

## Three-layer architecture

According to the supplied report, the FLAME defense model is described through three main layers.

### 1. Dynamic filtering

- HDBSCAN
- Cosine similarity
- Directional anomaly detection

Purpose described in the report: identify updates whose direction differs from the main population and exclude them as outliers.

### 2. Adaptive clipping

The report uses the median L2 norm to derive a round-specific clipping threshold `St`.

Purpose described in the report: limit unusually large update magnitudes, including updates that attempt to remain directionally normal while increasing their magnitude.

### 3. Differential Privacy

The report adds Gaussian noise after clipping/aggregation.

Purpose described in the report: preserve privacy while reducing the correlation between observable updates and sensitive information.

## Conceptual update rule

`W(t+1) = W(t) + η · [ (1/n) · Σ clip(Δi, St) + N(0, σ²St) ]`

This equation is reproduced as a conceptual formulation from the supplied report; it is not presented here as an independently implemented algorithm.

## Research question

The report's central security question is whether coordinated low-amplitude, directionally aligned poisoning can remain statistically inconspicuous when anomaly filtering, clipping, and privacy noise operate together.
