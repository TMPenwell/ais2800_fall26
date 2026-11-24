# Second Chapter — Normalized Tables Key

Oct 31, 2026 · @Tasha

Nine tables in third normal form. This assumes each item sells once and each consignor has one split percentage.

## Core vs. lookup tables

**Core tables** hold the business's main records: the people and things it tracks, plus the transactions between them. They grow as the store operates. Every new sale, item, customer, or consignor adds a row.

**Lookup tables** hold short, fixed lists of allowed values that core tables point to. They rarely change. Each is usually an ID and a name, plus any detail that comes with that value (TAG carries the discount).

**Quick test:** Does this table get new rows every time the store does business? Yes → core. No, it's a list we pick from → lookup.

**Why lookups matter:** they keep values consistent. Typos like "Clothng" can't get in, and a change to the yellow tag discount happens in one row instead of on every item.

## Core tables

### SALE

| Column | Key |
| --- | --- |
| receipt\_id | PK |
| sale\_date |  |
| payment\_method |  |
| customer\_id | FK → CUSTOMER (blank for non-members) |

### ITEM

| Column | Key |
| --- | --- |
| item\_id | PK |
| receipt\_id | FK → SALE (blank if unsold) |
| consignor\_id | FK → CONSIGNOR (blank if donated) |
| category\_id | FK → CATEGORY |
| brand\_id | FK → BRAND |
| tag\_id | FK → TAG |
| description |  |
| size |  |
| condition |  |
| intake\_date |  |
| original\_price |  |
| sale\_price |  |
| sale\_status |  |
| points\_earned |  |

### CUSTOMER

| Column | Key |
| --- | --- |
| customer\_id | PK |
| tier\_id | FK → REWARDS\_TIER |
| customer\_fname |  |
| customer\_lname |  |
| customer\_mi |  |
| customer\_phone |  |
| points\_balance |  |

### CONSIGNOR

| Column | Key |
| --- | --- |
| consignor\_id | PK |
| consignor\_fname |  |
| consignor\_lname |  |
| consignor\_mi |  |
| split\_pct |  |

### ITEM\_FLAW

| Column | Key |
| --- | --- |
| flaw\_id | PK |
| item\_id | FK → ITEM |
| flaw |  |

## Lookup tables

### REWARDS\_TIER

| Column | Key |
| --- | --- |
| tier\_id | PK |
| tier\_name |  |

### CATEGORY

| Column | Key |
| --- | --- |
| category\_id | PK |
| category\_name |  |

### BRAND

| Column | Key |
| --- | --- |
| brand\_id | PK |
| brand\_name |  |

### TAG

| Column | Key |
| --- | --- |
| tag\_id | PK |
| tag\_color |  |
| tag\_discount\_pct |  |

Not stored: `consignor_payout` (sale\_price × split\_pct) and `source_type` (a blank consignor\_id means Donated).

## ERD

&#91;embedded content: Second Chapter ERD · 9 tables, 8 one-to-many relationships\]

Each line runs from the one side (bar) to the many side (crow's foot), and the FK sits on the many side. No many-to-many means no join table. Three FKs can be blank: SALE.customer\_id (non-members), ITEM.receipt\_id (unsold), ITEM.consignor\_id (donated).
