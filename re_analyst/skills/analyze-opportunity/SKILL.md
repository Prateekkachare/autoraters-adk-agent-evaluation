---
name: analyze-opportunity
description: Investigates a land parcel for real estate investment opportunity analysis.
metadata:
  adk_additional_tools:
    - get_lot_data
---
# Analyze Opportunity Skill

When asked to investigate a property or analyze an investment opportunity for a lot, follow every step below thoroughly:

1. **Retrieve Subject Parcel Data**:
   - Use the `get_lot_data` tool to lookup the subject property attributes by its `plot_id`.
   - Explicitly record and present the core specifications (`plot_id`, exact `acreage`, `zoning`, `parcel_apn`, `last_sale_price`, `flood_zone`, `topography`, `utility_access`, and `environmental_status`) in both a structured Markdown summary table and the body text.

2. **Retrieve All Neighboring / Adjacent Parcels Data (`adjacent_parcels`)**:
   - Inspect the `adjacent_parcels` list in the subject lot's data.
   - You MUST call `get_lot_data` for **every** parcel ID listed in `adjacent_parcels` so you can report their exact FEMA `flood_zone` designations, `topography`, `soil_classification`, `easement_type`, `last_sale_price`, and `acreage`.

3. **Calculate & Benchmark Acquisition Cost-Per-Acre (Core Valuation Metric)**:
   - Derive and state the exact mathematical **Acquisition Cost-Per-Acre** from `last_sale_price` and `acreage` using the explicit formula:
     $$\text{Acquisition Cost-Per-Acre} = \frac{\text{Last Sale Price}}{\text{Acreage}} = \frac{\$\text{[last\_sale\_price]}}{\text{[acreage] acres}} = \$\text{[exact value] per acre}$$
   - Always show the full equation and exact numerical result (to 2 decimal places if non-integer), even when acreage is `1.0` acre.
   -Prominently highlight **Acquisition Cost-Per-Acre** in bold and in summary tables in both the **Executive Summary** and **Acquisition Basis and Holding Costs** sections, explicitly labeling it as a **Core Valuation Metric**.
   - Benchmark the subject parcel's cost-per-acre against the adjacent parcels' cost-per-acre (computed from the adjacent parcels' `last_sale_price` and `acreage`) and against typical market land basis for its zoning classification.

4. **Execute Flood, Neighboring Hydrological, and Environmental Analysis**:
   - Consult and load the `analyze-flood-risk` skill to evaluate the subject lot's FEMA flood zone, environmental Phase I/II ESA status, AND to perform a comprehensive comparative hydrological and flood risk analysis of all neighboring/adjacent properties (`adjacent_parcels`).

5. **Execute Tax & Monthly Carrying Cost Analysis**:
   - Consult and load the `analyze-tax-implications` skill to retrieve official tax records via `get_tax_assessment_data` using `parcel_apn` and explicitly calculate the monthly tax holding cost ($\text{Annual Taxes} \div 12$).
