# Method

How the dashboard was built, end to end.

## 1. Source data

Four Excel tables maintained by the programme: Project Details (1,836 rows), Package Details (1,585), Bill Expenditure (1,155) and Risk Details (36), plus a small Risk Master lookup (14). The workbook is not included in this repository.

## 2. Load and model

- Tables imported into Power BI with Power Query.
- Relationships modelled as many-to-one, single direction, on Project Code between Project Details, Package Details, Bill Expenditure and Risk Details, plus the Risk Master lookup.
- Row counts were checked against the source sheets after load.

## 3. Calculated columns (row-level logic)

13 calculated columns on Project Details implement the brief's categorizations: AS amount band, financial/physical progress ratios and their bands, progress difference, pending status, milestone stage, and the sort keys the charts need (see `dax/calculated-columns.dax`).

## 4. Measures (aggregations)

30 measures cover the funnel stages (each counting projects whose required dates are present), the KPI figures (awarded, expenditure, billing, risk resolution) and three HTML-styled measures that render the KPI cards through the HTML Content custom visual (see `dax/measures.dax`).

## 5. Report design

- A custom JSON theme (`Project_Monitoring_-_Professional`) was applied report-wide so every visual inherits the same palette.
- Nav bar with page-navigation buttons on every page.
- Hide/show slicer panel driven by bookmarks - District, Implementation Agency and Project Status on both pages, plus Bill Payment Status and Risk Status on the Overview page - with Apply all / Clear all slicers buttons, the brief's "slicers enabled on click of an icon" requirement.

## 6. Design evolution

The build started from a 4-page design draft (Overview / Budget / Progress / Risk, headline KPIs only on the landing page, page-local slicers for Bill Payment Status and Risk Status). In the final build this consolidated into 2 pages - **Overview** (KPI cards, risk donuts, pipeline funnel) and **Analysis** (budget allocation, pendency, progress toggle, district awarded-vs-expenditure) - which kept related analysis on one screen and reduced navigation. The draft spec is not included here; this section records the change for provenance.

## 7. Verification

Headline figures were recomputed from the loaded data (e.g. awarded 3,486.54 Cr, expenditure 864.66 Cr) and the two distinct "completed" statuses ("Physically Completed" vs "Completed") were confirmed as real, separate values per the brief.
