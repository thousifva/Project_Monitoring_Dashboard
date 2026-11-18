# Functional requirements (summary)

Summarized from the programme's original Functional Requirements brief. The brief itself is not included in this repository; this is a faithful summary of what the dashboard was required to do.

## Categorizations the dashboard must implement

- **AS Amount category** - bucket each project by Approved Sanction amount: <1 Cr, 1-5, 5-10, 10-25, 25-50, >50 Cr. Purpose: distribution by budget size, financial segmentation, high-value monitoring.
- **Financial Progress** - expenditure divided by awarded amount, then banded: <25%, 25-50%, 50-75%, >=75%.
- **Physical Progress** - the project's completion percentage as a ratio, banded the same way.
- **Progress Difference** - absolute gap between Physical and Financial Progress, banded: <5%, 5-25%, 25-50%, 50-75%, >=75%.
- **Milestone stage** - derived from which key dates exist: Pre DPR (no dates), DPR Issued, AS Issued, Started, Completed, else WIP.
- **Pending status** - which milestone date is missing next: DPR Pending, AS Pending, Not Started, Not Completed, Completed.

## Required dashboard components

1. Project Status KPI card - total projects, completed (Project Status = "Physically Completed"), remaining %
2. Awarded Amount KPI card - awarded (Cr), expenditure (Cr), remaining
3. Bill Amount KPI card - billed (Cr), approved bills, pending bills
4. Risk resolution - total vs resolved risks (status = "Solved")
5. Risk analysis - risk category vs total projects
6. Budget allocation - AS amount category vs project count, sorted by category
7. Pendency chart - pending category vs project count
8. Progress visualization - progress category vs count across the three progress types, sorted ascending
9. Awarded vs expenditure - by district
10. Progress summary funnel - DPR Approved, AS Issued, TS Issued, NIT Issued, Awarded, Started, Completed, each stage counting projects whose required dates (from Project Details and Package Details) are present

## Required behaviour

A slicer set that can be shown or hidden by clicking an icon - implemented in the final report as a bookmark-driven slicer panel on each page.
