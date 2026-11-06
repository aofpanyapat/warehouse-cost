# Warehouse Cost - Multi-page upgrade

Each of 9 original tabs has its own HTML page, with shared cached CSS/JS.

| Page | URL |
|---|---|
| Dashboard | index.html |
| Activity settings | pricing.html |
| Employees | employees.html |
| Daily logs | daily.html |
| Rate Card and invoice | ratecard.html |
| Activity breakdown | activity.html |
| Workforce plan | workforce.html |
| Ageing | ageing.html |
| P&L | summary.html |

Data: same Supabase project and tables. Large-table queries only run on pages
that require them. When needed, queries read all rows in batches of 500 to
avoid the Supabase 1000 row default cap and inaccurate financial totals.
Daily log history shows 50 rows per page with no loss of calculated history.
Full Excel export fetches all data before building the workbook.

Before merging this change into `main`: back up Supabase, compare Dashboard
and Summary metrics with the live site, check Rate Card IMEI import / invoice
print, check Ageing month close, test one daily-log add/delete and refresh.
Verify the 9 links. This branch does not modify Supabase schema or records.
Ensure Supabase Auth/RLS is properly configured before sharing write access.
