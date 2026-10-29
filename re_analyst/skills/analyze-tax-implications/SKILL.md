---
name: analyze-tax-implications
description: Investigates property tax holding costs, acquisition cost-per-acre valuation, and assessment records for a parcel.
metadata:
  adk_additional_tools:
    - get_tax_assessment_data
---
# Analyze Tax Implications Skill

When investigating financial carrying costs, valuation basis, or tax implications for a lot, perform all of the following steps:

1. **Retrieve Official Tax Assessment Records**:
   - Locate the `parcel_apn` from the subject lot's property records.
   - Call `get_tax_assessment_data` with `parcel_apn` to retrieve the official county tax assessment record (`annual_tax_amount`, `assessed_land_value`, `assessed_improvement_value`, `total_assessed_value`, `tax_year`, and `payment_status`).

2. **Derive and Highlight Acquisition Cost-Per-Acre as a Core Valuation Metric**:
   - Using `last_sale_price` and `acreage` from the lot record, explicitly show the mathematical derivation formula and exact result:
     $$\text{Acquisition Cost-Per-Acre} = \frac{\text{Last Sale Price}}{\text{Acreage}} = \frac{\$\text{[last\_sale\_price]}}{\text{[acreage] acres}} = \$\text{[exact cost-per-acre] / acre}$$
   - State and highlight this **Acquisition Cost-Per-Acre** figure prominently in bold and in a Markdown table as a **Core Valuation Metric**.
   - Compare and benchmark the subject lot's Acquisition Cost-Per-Acre against the `total_assessed_value` per acre (`total_assessed_value / acreage`) and against the adjacent parcels' cost-per-acre (`last_sale_price / acreage`).

3. **Calculate Explicit Monthly Tax Holding Cost**:
   - Explicitly calculate and state the monthly tax holding cost during pre-development carrying phases by dividing the annual tax by 12:
     $$\text{Monthly Tax Holding Cost} = \frac{\text{Annual Tax}}{12\text{ months}} = \$\text{[exact monthly amount] / month}$$
   - If the lot data's `estimated_annual_taxes` and the tax database's `annual_tax_amount` differ, show the exact monthly calculation ($\div 12$) for both figures and discuss the carrying cost impact on pre-construction holding budgets, entitlement timelines, and any tax delinquency/lien cure costs.
