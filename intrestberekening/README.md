# Interest calculation documentation

## TEST CASES REASONING

The interest calculation template does not have a lot of different values, but the user can enter accounts where the calculated interest should be handled in a lot of different ways.

Biggest challenge with building the liquid testing code efficiently for this template is that a lot of the code is duplicate.

All 4 calculation types (day / month / quarter / year) is duplicate code instead of only swapping out the specific parameters that change. There was also a major update to the interest calculation and this code was duplicated 4 more times. This means there’s no point where we can assume that if a (part) of the calculation works for one type that it also works for the other types so we’ll need to test each type separately.

We’ll split the units/scenarios/blocks/? based on the account type (debet/credit) and its value (debet/credit).
Then we’ll split up the tests in each unit based on how the user has chosen to perform the calculation (chosen calculation type, checks applied, default or adjusted values).

The checks code has two versions (one for before the major update and after), so we’ll assume that if it works for one calculation type it will also work for the others as there are only specific parameters that change.

These are the things we need to cover in the liquid testing:

1. We need to cover the checks that can occur on the interest value (requalification to dividend / excessive interest for disallowed expenses calculated correctly)
2. User can manually adjust the default values that the interest is calculated on (interest should adjust accordingly)
3. User can add add one or more accounts (sums should be calculated correctly)
4. User can add only debet accounts, only credit accounts or a combination of both (combining different account types and values should sum correctly)
5. The calculation can be made in 4 different ways (day / month / quarter / year)
6. Certain updates were made that only affect bookyear after 1/1/2021, so we need to make tests to check if the changed values in these new periods work

So we’ll need to build out a separate test per calculation type for each unit/scenario/block/?
The year calculation in the old calculation (= before the major update) only has one default value that can be adjusted, so we’ll need to build two separate cases to test debet & credit manually adjusted values.

The company where the tests were performed can be found here: https://live.getsilverfin.com/f/14400/1223644/ledgers/24579074/workflows/1971483/reconciliation_texts/48343831?debug=1

## OVERVIEW YAML TESTS

###  Units

**UNIT 0:** Empty state

**UNIT 1:** Debet account with a credit value

**UNIT 2:** Debet account with a debet value

**UNIT 3:** Credit account with a credit value (includes additional tests - manually adjusted interest rates)

**UNIT 4:** Credit account with a debet value 

---

Tests for combinations of accounts are aimed at testing if the summations are behaving correctly.
Tests for every calculation type is not necessary since we already have detailed tests per individual account.

---

**UNIT 5:** Two debit accounts with debet value

**UNIT 6:** Two credit accounts with credit value

**UNIT 7:** Debet account with a debet value & Credit account with a credit value

**UNIT 8:** Debet account with a credit value & Credit account with a credit value

**UNIT 9:** Debet account with a debet value & Credit account with a debet value

**UNIT 10:** Debet account with a credit value & Credit account with a debet value

**UNIT 11:** Credit account with a credit value + period: 2022-06-30

**UNIT 12:** Credit account with a credit value + period: 2022-06-30 

---
---

### Tests per unit - individual accounts

**TEST 1:** updated broken bookyear calculation - day - default values

**TEST 2:** updated broken bookyear calculation - day - manually adjusted credit & debet value

**TEST 3:** updated broken bookyear calculation - month - default values

**TEST 4:** updated broken bookyear calculation - month - manually adjusted credit & debet value

**TEST 5:** updated broken bookyear calculation - quarter - default values

**TEST 6:** updated broken bookyear calculation - quarter - manually adjusted credit & debet value

**TEST 7:** updated broken bookyear calculation - year - default values

**TEST 8:** updated broken bookyear calculation - year - manually adjusted credit & debet value

**TEST 9 (only for accounts with credit values):** updated broken bookyear calculation - day - default values - requalification applied

**TEST 10 (only for accounts with credit values):** updated broken bookyear calculation - month - default values - requalification applied

**TEST 11 (only for accounts with credit values):** updated broken bookyear calculation - day - default values - excessive interest applied

**TEST 12 (only for accounts with credit values):** updated broken bookyear calculation - month - default values - excessive interest applied

**TEST 13:** old broken bookyear calculation - day - default values

**TEST 14:** old broken bookyear calculation - day - manually adjusted credit & debet value

**TEST 15:** old broken bookyear calculation - month - default credit values

**TEST 16:** old broken bookyear calculation - month - manually adjusted credit & debet value

**TEST 17:** old broken bookyear calculation - quarter - default credit values

**TEST 18:** old broken bookyear calculation - quarter - manually adjusted credit & debet value

**TEST 19:** old broken bookyear calculation - year - default credit values

**TEST 20:** old broken bookyear calculation - year - manually adjusted credit value

**TEST 21:** old broken bookyear calculation - year - manually adjusted debet value

**TEST 22 (only for accounts with  credit values):** old broken bookyear calculation - day - default credit values - requalification applied

**TEST 23 (only for accounts with  credit values):** old broken bookyear calculation - month - default credit values - requalification applied

**TEST 24 (only for accounts with credit values):** old broken bookyear calculation - day - default credit values - excessive interest applied

**TEST 25 (only for accounts with credit values):** old broken bookyear calculation - month - default credit values - excessive interest applied

---
---

### Tests per unit - combined accounts

**TEST 1:** updated broken bookyear calculation - day - default values

**TEST 2:** updated broken bookyear calculation - day - manually adjusted credit & debet value

**TEST 3 (only for accounts with credit values):** updated broken bookyear calculation - day - default values - requalification applied

**TEST 4 (only for accounts with credit values):** updated broken bookyear calculation - day - default values - excessive interest applied

**TEST 5:** old broken bookyear calculation - day - default values

**TEST 6:** old broken bookyear calculation - day - manually adjusted credit & debet value

**TEST 7 (only for accounts with credit values):** old broken bookyear calculation - day - default values - requalification applied

**TEST 8 (only for accounts with credit values):** old broken bookyear calculation - day - default values - excessive interest applied

---
---

### Tests per unit - updates after a certain date

**TEST 1:** updated broken bookyear calculation - day - default values

**TEST 2:** updated broken bookyear calculation - day - manually adjusted credit & debet value

### Additional tests per unit - manually adjusted interest rates

**TEST 1:** updated broken bookyear calculation - day - old standard custom interest adjusted

**TEST 2:** updated broken bookyear calculation - day - updated standard custom interest adjusted

**TEST 3:** updated broken bookyear calculation - day - line-specific custom interest adjusted

### Additional tests per unit - manually adjusted interest rates

**TEST 1:** updated broken bookyear calculation - day - old standard custom interest adjusted

**TEST 2:** updated broken bookyear calculation - day - updated standard custom interest adjusted

**TEST 3:** updated broken bookyear calculation - day - updated standard custom interest adjusted + line-specific custom interest adjusted