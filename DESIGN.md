# Gratuity Calculator – Design Document

## Overview
A single-page HTML application that computes gratuity payable to an employee
under the **Payment of Gratuity Act, 1972 (India)**.

## Formula

```
Gratuity = (Basic + DA) x 15 x Years_of_Service / 26
```

- **Basic**: Last drawn monthly basic salary (INR)
- **DA**: Last drawn monthly Dearness Allowance (INR)
- **15**: 15 days of wages for each completed year
- **26**: Number of working days in a month (as per the Act)
- **Years_of_Service**: Rounded — ≥6 months rounds up, <6 months rounds down

## Service Rounding Rule

| Condition                          | Action       |
|------------------------------------|-------------|
| Fractional part ≥ 0.5 years (6 mo) | Round up    |
| Fractional part < 0.5 years (6 mo) | Round down  |

## Architecture

```
index.html
├── CSS (embedded <style>)
│   ├── Card layout (.card)
│   ├── Form inputs (basic, da, service)
│   ├── Result section (hidden until calculation)
│   ├── Service rounding note, tax note, eligibility section
│   └── Error state
├── HTML (embedded <body>)
│   ├── Input fields (3)
│   ├── Calculate button
│   ├── Result container (dynamic)
│   │   ├── Amount display
│   │   ├── Step-by-step breakdown
│   │   ├── Rounding explanation
│   │   └── Taxability note
│   └── Eligibility section (static)
└── JS (embedded <script>)
    ├── Input parsing & validation
    ├── Service-year rounding logic
    ├── Gratuity computation
    ├── INR-formatting via toLocaleString('en-IN')
    └── DOM rendering of breakdown
```

## Files

| File         | Purpose                           |
|-------------|-----------------------------------|
| index.html  | Single-file application (UI + JS) |
| DESIGN.md   | This document                     |
| README.md   | Usage and test samples            |
| prompt.txt  | Original build prompts            |

## Taxability
- **Government employees**: Fully exempt.
- **Non-government (Act-covered)**: Exemption = minimum of:
  - ₹20,00,000
  - Actual gratuity received
  - Computed gratuity as per formula
  Excess is taxable under "Income from Salary".
