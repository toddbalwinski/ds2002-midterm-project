# Team charter: Storm Surge Analytics

## Members
- Russell Fullerton (GitHub: rfullerton42)
- Todd Balwinski (GitHub: toddbalwinski)

## Goals
- **good result:** A single notebook that runs top to bottom (Restart and Run All), with a documented cleaning pipeline, a working and verified weather join, and a written answer with a chart for each of the five questions. We want to be able to explain every cleaning decision.
- **what each person wants:** Russell wants to get strong at pandas cleaning and building the SKU mapping. Todd wants hands-on practice with the weather API and joins. Both want a clear presentation on Nov 2.
- **time limits:** Other classes and work. We meet Thursdays 8:30 PM and Sundays 6:30 PM, and work on our own in between.
- **what to avoid:** Analyzing dirty data, both of us editing the same notebook, one person quietly doing all the cleaning, decisions made in chat and never written down, and leaving the weather API to the last week. We avoid these with the rules below.

## Roles

| Role | Owner | Backup |
|---|---|---|
| Cleaning + decision log | Russell Fullerton | Todd Balwinski |
| Weather API + join | Todd Balwinski | Russell Fullerton |
| Analysis Q1-Q5 | Shared (see below) | Shared |
| Charts + presentation | Shared (both build charts) | Shared |

## Question owners

| Question | Owner | Reviewer |
|---|---|---|
| Q1 demand surge | Russell Fullerton | Todd Balwinski |
| Q2 SKU consolidation | Russell Fullerton | Todd Balwinski |
| Q3 weather correlation | Todd Balwinski | Russell Fullerton |
| Q4 stores and geography | Todd Balwinski | Russell Fullerton |
| Q5 signal or artifact | Russell Fullerton | Todd Balwinski |

## How we work
- **repo url:** https://github.com/toddbalwinski/ds2002-midterm-project
- **notebook owner this week:** Todd Balwinski (only he commits `notebooks/team_notebook.ipynb`; the owner rotates weekly)
- **meeting time:** Thursdays 8:30 PM and Sundays 6:30 PM
- **channel:** Team group chat, reply within 24 hours. If you are blocked, say so right away instead of waiting for the next meeting.
- **how we decide:** Look at the data first. If we are still stuck, the owner of that part decides, and the decision goes in the decision log with the reason.
- **if someone goes quiet:** Check in after one day. If there is still nothing after two, bring it to the whole team. If it is still unresolved, email the instructor. Do not wait until the due date.
- **git rules:** Pull before starting, push before stopping. Work in your own notebook under `notebooks/scratch/` and hand finished code to the notebook owner as functions. Commit messages say what changed (for example `Q1: add baseline window`). No keys or tokens in the repo.

## Meetings held
- Thursday, Oct 22, 8:30 PM
- Sunday, Oct 25, 6:30 PM

## Five worst problems in the data
From the profile of `walmart_transactions.csv`. These match the problems the project brief says to expect. Row counts to be added from our profile output.

1. `unit_price` is stored as text (not numeric), and some values start with `$`.
2. Missing values are written several different ways (empty, `NULL`, `N/A`, NaN), so a plain null count undercounts them.
3. Dates and times are in different formats, so they cannot be parsed or compared until cleaned. This blocks Q1.
4. `store_id` is written differently across rows and files, so it will not join to `store_locations.csv` until standardized. This blocks Q4.
5. The same product appears under several SKUs and names, and `product_name`, `category` and `quantity` have inconsistent spelling, capitalization, spacing and negative values. This blocks Q2.
