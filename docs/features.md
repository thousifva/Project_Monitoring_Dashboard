# Features and techniques

Everything listed here is implemented in the final report file (verified from the .pbix itself), not just planned in the brief.

## Report structure

- **Two pages - Overview and Analysis** - behind a top nav bar. Page navigation uses Power BI's page navigator (button-style page tabs), so moving between pages is one click from anywhere.
- **Custom JSON theme** applied report-wide, so every visual inherits the same palette and fonts.

## Overview page

- **Three KPI cards rendered as HTML.** Each card is an HTML Content custom visual fed by a DAX measure that returns a styled HTML string (value, label, percentage pill and sub-figures). This gives full control over layout, colours and typography beyond the built-in card visual. The three measures (`Card_TotalProjects_HTML`, `Card_Awarded_HTML`, `Card_Bill_HTML`) are included verbatim in `dax/measures.dax`.
- **Progress Summary funnel.** Seven milestone-stage measures (DPR Approved, AS Issued, TS Issued, NIT Issued, Awarded, Started, Completed) shown as a funnel, so the narrowing of the project pipeline is visible at a glance. Each stage measure counts only the projects whose required dates are present, across the Project and Package tables.
- **Two risk donuts.** Risk resolution (resolved vs total risks, status = "Solved") and risk analysis (projects by risk category).

## Analysis page

- **Budget Allocation** - project count by Approved Sanction amount band (<1 Cr up to >50 Cr), sorted by the band's sort key column rather than alphabetically.
- **Pendency of Projects** - project count by pending category (AS Pending, DPR Pending, Not Started, Not Completed, Completed).
- **Progress Visualization with a 3-way toggle.** A field-parameter slicer (Financial / Physical / Progress) restyled as buttons; the column chart switches between the three progress bandings without leaving the page.
- **Awarded Amount vs Expenditure** - district-level area chart comparing awarded value against expenditure.

## Slicers and interaction

- **Hide/show slicer panel on both pages**, driven by bookmarks: clicking the filter icon toggles a panel containing District, Implementation Agency, Project Status, plus Bill Payment Status and Risk Status where relevant. Four bookmarks (show/hide states per page) implement this - the brief's "slicers enabled on click of an icon" requirement.
- **Apply all / Clear all slicers buttons** inside the panel, using Power BI's built-in slicer actions.
- Cross-filtering is standard Power BI behaviour: selecting an element in one visual filters the others on the page.

## Data and measures

- 4 active many-to-one, single-direction relationships on Project Code between the five tables, plus the Risk Master lookup.
- 13 calculated columns implement the brief's categorizations at row level (amount bands, progress ratios and bands, sort keys, pending status, milestone stage).
- 30 measures cover funnel stages, KPI figures, billing, risk and the three HTML card templates. All of them are in `dax/`, extracted verbatim from the final file.

## Provenance

Based on a real government project monitoring dashboard. The data in the published file and screenshots has been manipulated and uses demo figures for portfolio purposes - no real project figures, names or identifying details are included. The .pbix and source workbook are not part of this repository.
