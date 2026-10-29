---
name: analyze-flood-risk
description: Investigates flood zone designations, neighboring property flood risks, and environmental risks for real estate investment opportunity analysis.
metadata:
  adk_additional_tools:
    - get_lot_data
---
# Analyze Flood Risk Skill

When evaluating environmental, hydrological, or geographic risks for a lot, you MUST perform all three investigations below and include them in the final memorandum:

1. **Subject Parcel FEMA Flood Zone Flagging & Engineering/Insurance Impacts**:
   - Explicitly state the subject parcel's exact FEMA `flood_zone` designation (e.g., `Zone AE (High Risk)`, `Zone VE (Coastal High Hazard)`, `Zone X (Minimal Risk)`).
   - Explain specific vertical construction and site engineering impacts:
     - For `Zone AE` or `Zone A`: Base Flood Elevation (BFE) compliance, imported structural fill dirt requirements to elevate building pads, elevated mechanical/electrical systems, foundation waterproofing, and mandatory National Flood Insurance Program (NFIP) flood insurance premiums.
     - For `Zone VE`: Coastal velocity hazard requirements including deep driven pile or column foundations, breakaway lower-level enclosure walls, structural wind/wave load engineering, and high-cost coastal NFIP flood insurance.
     - For `Zone X`: Note minimal 100-year flood hazard and lower insurance costs, while still addressing standard municipal stormwater retention and grading requirements.

2. **Mandatory Neighboring Property Flood Risk & Comparative Hydrological Analysis**:
   - Check the `adjacent_parcels` field from the subject parcel's `get_lot_data` record.
   - Call `get_lot_data` for **every single parcel ID** in `adjacent_parcels` (if not already fetched) to inspect each neighbor's `flood_zone`, `topography`, `soil_classification`, and `easement_type`.
   - In the **Risk Assessment** section (and briefly in the **Executive Summary**), include a dedicated subsection titled `### Neighboring Property Flood Zones & Comparative Hydrological Impact Analysis` with a Markdown comparison table comparing the subject lot and every adjacent lot (`Plot ID`, `FEMA Flood Zone`, `Topography / Slope`, `Soil Classification`, `Easements`).
   - Exhaustively analyze:
     - Each neighboring parcel's exact FEMA flood zone classification compared to the subject parcel.
     - Cross-boundary drainage and surface water runoff dynamics based on relative slope/topography grades (`topography`) and soil permeability (`soil_classification`).
     - How high-risk neighboring flood zones (`Zone AE`, `Zone VE`, `Zone A`) or drainage easements on adjacent or subject parcels affect floodplain encroachment, water table elevation, stormwater detention/retention basin sizing, swales/curbing, and overall development feasibility and CapEx on the subject parcel.

3. **Environmental Status (Phase I / Phase II ESA) Due Diligence**:
   - Explicitly state the exact `environmental_status` from the lot data and prescribe actionable due diligence steps (e.g., Phase II ESA subsurface soil and groundwater sampling if a REC or historical Underground Storage Tank is flagged, remediation cost reserves, or standard environmental representations if Phase I ESA is Clean).
