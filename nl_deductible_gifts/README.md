LT - Corporate tax - deductible gifts

workflow: nl fiscal position
template handle: nl_deductible_gifts
link to partners environment: https://live.getsilverfin.com/partners/template_collection/reconciliation_texts/919/edit

Overview

UNIT 0: EMPTY STATE
UNIT 1: INCOMING RESULT
UNIT 2: FORI ITEMS
UNIT 3: BUTTON TOTAL GIFTS ALREADY IN ADMIN

##################


UNIT 0: EMPTY STATE

Description: Empty state

Scenario 1: empty state

##################


UNIT 1: INCOMING RESULT

Description: relevant code in shared part nl_tax_calculation_table, which determines the a-priori result and baseline functionality of the template when no data is entered by the user

*Scenario 1: Added simple set of accounts to test - equity method not used (P&L accounts)*

Scenario 2: Added simple set of accounts to test - equity method used (BS accounts)

Scenario 3: Added full set of accounts and custom values in nl_tax_status (real-life case)

##################


UNIT 2: FORI ITEMS

Description: Testing of fori items by which the user can add deductiblle gifts, and simple calculation

*Scenario 1: "Fail" 2x2 items, equity method == true*

*Scenario 2: "Success" 2x2 items, equity method == false*

Scenario 3: "Success" 2x2 items, equity method == true

##################


UNIT 3: BUTTON TOTAL GIFTS ALREADY IN ADMIN

Description: Testing of boolean button by which the deductible gifts can be added or removed to the a-priori result, as that is an input for determining the maximum amount by the template

Scenario 1: Total gifts in admin boolean default (false)

Scenario 2: Total gifts in admin boolean true, which has significant impact on output results








