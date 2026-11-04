# Carrier rules dataset

DIM weight divisors, size and surcharge limits, USPS cubic rules, Amazon FBA size tiers, carrier and moving box sizes,
a dated log of rule changes, and places where carrier documents disagree. Every value has the source document
and the date it was checked.

- Version: **2026.11.04**
- Rules checked against the carrier documents: **2026-09-22**
- Licence: **CC BY 4.0** (see [LICENSE](LICENSE))
- Live copy and documentation: <https://boxvolumecalculator.com/data/>

## Files

| File | Holds |
|---|---|
| `data/carrier-rules.json` | DIM divisors per carrier and service, size and surcharge limits, USPS DIM/cubic/nonstandard rules, Amazon FBA tiers, sources |
| `data/carrier-boxes.json` | USPS, UPS and FedEx box sizes; U-Haul, Home Depot and Lowe's moving boxes; source URL and date for each |
| `data/changelog.json` | Dated rule changes, each with the carrier documents |
| `data/contradictions.json` | Pairs of documents from one carrier or seller that give different values |
| `data/dim-divisors.csv`, `data/size-limits.csv`, `data/carrier-boxes.csv` | The same data for spreadsheets |

Units: lengths in inches, volumes in cubic inches, weights in pounds, divisors in in³/lb or cm³/kg, money in USD.

## DIM divisors

| Carrier | Region | Service | in³/lb | cm³/kg |
|---|---|---|---|---|
| FedEx | US Domestic | All US services | 139 | 5000 |
| FedEx | International | International services | 139 | 5000 |
| UPS | US Domestic | Daily Rates (UPS account) | 139 | 5000 |
| UPS | US Domestic | Retail Rates (UPS Store / counter) | 166 | — |
| UPS | International | International services | 139 | 5000 |
| USPS | US Domestic | Priority Mail | 139 | — |
| USPS | US Domestic | USPS Ground Advantage (commercial) | 139 | — |
| USPS | US Domestic | USPS Ground Advantage – Retail | 139 | — |
| USPS | US Domestic | Priority Mail Express | 139 | — |
| USPS | US Domestic | Parcel Select | 139 | — |
| DHL | Express (from the US) | DHL Express Worldwide / US Domestic Express | 139 | — |
| Parcelforce | Worldwide (international) | Parcelforce Worldwide (international) | — | 5000 |
| Air Freight | Forwarder (1:6 ratio) | Air freight (1:6) | — | 6000 |

## Use

```js
const d = await (await fetch("https://boxvolumecalculator.com/data/carrier-rules.json")).json();
d.dim_divisors.find((x) => x.carrier_id === "ups_dom" && x.service_id === "daily").divisor_in3_per_lb; // 139
```

The live files on boxvolumecalculator.com allow requests from any website (CORS). Please cache them: they change a few
times a year, usually in January and July.

## Credit

Data: [BoxVolumeCalculator carrier rules dataset](https://boxvolumecalculator.com/data/) (CC BY 4.0)

The carriers own their rules and prices. This dataset collects them with the source of each value. Check the source
before you rely on a value for billing.

## Report an error

Open an issue with the link to the carrier document, or email contactus@boxvolumecalculator.com.

Maintained by Sri Murugan Systems.
