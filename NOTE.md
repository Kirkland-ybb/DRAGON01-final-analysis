# Scope and source notes

This public subset covers survival reconstruction/fitting and supplied plotting tables for S2-S4, not the economic analysis. No costs, resource packages, PSA NPZs, economic result tables, or economic reference arrays are distributed. Numeric mortality/survival JSON inputs are retained because unchanged programs read them directly.

OS events are 132/69. PFS event constraints 139/70 derive from published counts and disease-free survivors; they are not a separately reported original IPD event total. Reconstructed OS/PFS identifiers do not link individuals. The all-cause and excess-hazard fits are separate model families; adopted coefficients remain frozen during refitting.

Data origins: DRAGON-01 published KM curves (Yan et al., DOI 10.1001/jamaoncol.2026.1347); China life tables from UN WPP 2024. Fitted coefficients, grids and diagnostic tables are study-derived. Shared generic functions do not constitute a complete economic model.

All 9 Python and 5 R programs are byte-identical to the complete review package. Program paths are preserved. This package uses README commands as its survival entry point; no existing program has been rewritten.
