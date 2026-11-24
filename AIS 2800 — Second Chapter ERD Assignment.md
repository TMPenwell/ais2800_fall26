# AIS 2800 — Second Chapter ERD Assignment

Nov 1, 2026 · @Tasha

## What you're doing

You've already split the Second Chapter file into tables. Now you'll draw how those tables connect. An ERD (entity relationship diagram) is the map a database team works from: it shows every table, its keys, and how the tables link.

**You'll use:** your normalized tables from the normalization assignment, or the class version from our review.

**The nine tables:** SALE, ITEM, CUSTOMER, CONSIGNOR, ITEM\_FLAW, REWARDS\_TIER, CATEGORY, BRAND, TAG.

**Draw it in:** \[tool: Figma, draw.io, or paper and a photo\]

## Part 1: Say how the business works

Before drawing anything, write one sentence for each pair of tables that connect. Use a verb that describes what happens at the store.

**Example:** A customer *makes* many sales.

Write a sentence for each of these pairs:

1. CUSTOMER and SALE
2. SALE and ITEM
3. CONSIGNOR and ITEM
4. ITEM and ITEM\_FLAW
5. REWARDS\_TIER and CUSTOMER
6. CATEGORY and ITEM
7. BRAND and ITEM
8. TAG and ITEM

**Pause and Reflect:** Which sentence was hardest to write? What about the store did you have to think through?

## Part 2: Count both ways

For each pair, pick one row from each table and count its matches in the other. The table that shows up as "many" is the **many side**. That table holds the foreign key (FK): a column with the other table's primary key (PK).

The first row is done for you.

| Pair | Pick one of the first... how many of the second? | Pick one of the second... how many of the first? | Many side (holds the FK) | FK column |
| --- | --- | --- | --- | --- |
| CUSTOMER / SALE | One customer, many sales | One sale, one customer | SALE | customer\_id |
| SALE / ITEM |  |  |  |  |
| CONSIGNOR / ITEM |  |  |  |  |
| ITEM / ITEM\_FLAW |  |  |  |  |
| REWARDS\_TIER / CUSTOMER |  |  |  |  |
| CATEGORY / ITEM |  |  |  |  |
| BRAND / ITEM |  |  |  |  |
| TAG / ITEM |  |  |  |  |

**Pause and Reflect:** Did any pair come out "many" in both directions? What would that mean for the design?

## Part 3: Draw the ERD

Now turn your sentences and counts into a diagram.

**Each table is a box.**

- The table name goes at the top.
- List every column below it.
- Mark the primary key **PK** and each foreign key **FK**.

**Each relationship is a line** between two boxes, in crow's foot notation:

- **A single bar ( | )** at the "one" end.
- **A crow's foot ( three prongs )** at the "many" end. The crow's foot always touches the table that holds the FK.

**Tip:** Start with ITEM in the middle. Most of the other tables connect to it.

**Pause and Reflect:** Look at your finished diagram. If a manager asked, "Which consignor brought in the item on receipt 9001?", which lines would you follow to answer?

## Part 4: Find the five mistakes

A teammate drafted these tables. Each table has **one column that doesn't belong**. For each one, find the column, explain why it doesn't belong, and say what to do with it.

| Table | Columns |
| --- | --- |
| SALE | receipt\_id (PK), sale\_date, payment\_method, customer\_id (FK), consignor\_id |
| ITEM | item\_id (PK), receipt\_id (FK), consignor\_id (FK), category\_id (FK), brand\_id (FK), tag\_id (FK), customer\_phone, description, size, condition, intake\_date, original\_price, sale\_price, sale\_status, points\_earned |
| CUSTOMER | customer\_id (PK), tier\_id (FK), tier\_name, customer\_fname, customer\_lname, customer\_mi, customer\_phone, points\_balance |
| CONSIGNOR | consignor\_id (PK), consignor\_fname, consignor\_lname, consignor\_mi, split\_pct, item\_id |
| ITEM\_FLAW | flaw\_id (PK), item\_id (FK), flaw, customer\_id |

For each mistake, fill in:

| Table | Column that doesn't belong | Why (use "If I know \_\_\_, do I know \_\_\_?") | What to do with it |
| --- | --- | --- | --- |
| SALE |  |  |  |
| ITEM |  |  |  |
| CUSTOMER |  |  |  |
| CONSIGNOR |  |  |  |
| ITEM\_FLAW |  |  |  |

**Pause and Reflect:** Which mistake would have been easiest to make yourself? Spotting it now is a win worth celebrating.

## What to submit

Submit one file to Canvas with:

- [ ] Part 1: your eight relationship sentences
- [ ] Part 2: your completed count table
- [ ] Part 3: your ERD (an image or export from \[tool\])
- [ ] Part 4: your completed mistakes table

**Due:** \[date\]

## How it's graded

| Part | What earns full credit | Points |
| --- | --- | --- |
| 1. Sentences | All eight pairs, each with a verb and "one" or "many" | \[\_\_\] |
| 2. Count table | Many side and FK column correct for each pair | \[\_\_\] |
| 3. ERD | All nine tables with PK and FK marked; crow's foot on the many side of every line | \[\_\_\] |
| 4. Mistakes | Each mistake found, with a reason and a fix | \[\_\_\] |
| **Total** |  | **\[\_\_\]** |
