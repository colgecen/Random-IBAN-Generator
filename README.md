# Random IBAN Generator

A single-file, zero-dependency web tool for generating structurally valid IBANs with correct MOD-97 check digits and real bank identifiers. Built for developers testing payment gateway integrations, financial APIs, and banking software.

**[Try it live →](https://colgecen.github.io/Random-IBAN-Generator/)**

> **These are not real bank accounts.** All generated IBANs are synthetic test data.

## Features

- **MOD-97 validated** — every IBAN passes ISO 7064 check digit verification
- **Real bank identifiers** — uses actual bank codes (BIC/sort code prefixes) per country
- **80+ countries** — full BBAN format spec for every supported country
- **Bulk generation** — generate 1–50 IBANs at once
- **Copy options** — copy individual IBANs, all at once (newline-separated), or as structured JSON
- **Structure inspector** — shows BBAN format breakdown and all known banks for the selected country
- **Zero dependencies** — single `index.html` file, no build step, no server required

## Usage

Open `index.html` directly in any modern browser — no installation needed.

1. **Select a country** from the dropdown (sorted alphabetically, shows bank count)
2. **Set the quantity** (1–50)
3. Click **Generate**
4. Click any row to copy the IBAN, or use **Copy All** / **Copy as JSON**

### JSON output format

```json
[
  {
    "iban": "DE89370400440532013000",
    "country": "DE",
    "bank": "Commerzbank",
    "formatted": "DE89 3704 0044 0532 0130 00",
    "valid": true
  }
]
```

## Supported Countries

80+ countries including all SEPA members and many non-European countries:

Albania, Andorra, Austria, Azerbaijan, Bahrain, Belarus, Belgium, Bosnia and Herzegovina, Brazil, Bulgaria, Costa Rica, Croatia, Cyprus, Czech Republic, Denmark, Dominican Republic, East Timor, Egypt, El Salvador, Estonia, Faroe Islands, Finland, France, Georgia, Germany, Gibraltar, Greece, Greenland, Guatemala, Hungary, Iceland, Iraq, Ireland, Israel, Italy, Jordan, Kazakhstan, Kosovo, Kuwait, Latvia, Lebanon, Liechtenstein, Lithuania, Luxembourg, Malta, Mauritania, Mauritius, Moldova, Monaco, Montenegro, Netherlands, North Macedonia, Norway, Pakistan, Palestine, Poland, Portugal, Qatar, Romania, Saint Lucia, San Marino, São Tomé and Príncipe, Saudi Arabia, Serbia, Seychelles, Slovakia, Slovenia, Spain, Sweden, Switzerland, Tunisia, Turkey, Ukraine, United Arab Emirates, United Kingdom, Vatican City, Virgin Islands (British)

## How it works

1. A random bank code is selected from the embedded database of real bank identifiers for the chosen country
2. The remainder of the BBAN is randomly generated following the country's official BBAN format spec (`n` = digit, `a` = uppercase letter, `c` = alphanumeric)
3. The two-digit check number is computed using the MOD-97 algorithm (ISO 7064)
4. Each result is validated before display — a `✓ MOD97` badge confirms correctness

## Intended use

- Seeding test databases with realistic-looking payment data
- Validating IBAN input fields and formatters
- Testing payment gateway integrations without real account numbers
- Generating fixture data for unit and integration tests

## License

MIT
