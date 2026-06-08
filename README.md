# India Gratuity Calculator

A single-page web application to compute gratuity under the **Payment of
Gratuity Act, 1972**.

**Formula:** `(Basic + DA) × 15 × Years of Service ÷ 26`

**Features:**
- Step-by-step breakdown of calculation
- Service rounding (>6 months rounds up, <6 months rounds down)
- Taxability information
- Eligibility conditions (including Labour Code 2025 updates)

## Usage

Open `index.html` in any modern browser. No server or build step required.

## Sample Test Values

| # | Basic (₹) | DA (₹) | Service (yrs) | Expected Gratuity (₹) | Notes |
|---|-----------|--------|---------------|----------------------|-------|
| 1 | 50,000    | 15,000 | 12            | 4,50,000             | Exact 12 yrs, no rounding needed |
| 2 | 35,000    | 8,000  | 7.6           | 1,73,654             | 7.6 yrs → rounds up to 8 yrs |
| 3 | 25,000    | 5,000  | 5.3           | 87,692               | 5.3 yrs → rounds down to 5 yrs |
| 4 | 80,000    | 20,000 | 15            | 8,65,385             | No rounding, 15 yrs exactly |
| 5 | 12,000    | 3,000  | 1.4           | 12,115               | 1.4 yrs → rounds down to 1 yr |
| 6 | 45,000    | 10,000 | 20.7          | 9,52,500             | 20.7 yrs → rounds up to 21 yrs |
| 7 | 1,00,000  | 25,000 | 11.0          | 7,93,269             | Exact 11 yrs |
| 8 | 30,000    | 6,000  | 25.5          | 8,30,769             | 25.5 yrs → rounds up to 26 yrs |

### Manual verification (row 1)

```
Salary = 50,000 + 15,000 = 65,000
Years  = 12 (exact)
= 65,000 × 15 × 12 / 26
= 1,17,00,000 / 26
= 4,50,000
```

### Manual verification (row 2)

```
Salary = 35,000 + 8,000 = 43,000
Years  = 7.6 → 0.6 = 7.2 months ≥ 6 → rounds up to 8
= 43,000 × 15 × 8 / 26
= 51,60,000 / 26
= 1,73,654
```

## License

MIT
