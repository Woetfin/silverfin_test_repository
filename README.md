# VAT balance liquid test

## TEST CASES REASONING

### Success paths

For the **success** paths we need to cover cases with and without defaults:
* Receivable VAT amount: default accounts value are equal to the explained amounts
* Receivable VAT amount: manual accounts value are equal to the explained amounts
* Payable VAT amount: default accounts value are equal to the explained amounts
* Payable VAT amount: manual accounts value are equal to the explained amounts 

### Error paths

For the **error** paths we'll cover four cases where differences could occur and the template needs to be unreconciled:
* Receivable VAT amount: accounts value are higher than the explained amounts
* Receivable VAT amount: accounts value are lower than the explained amounts
* Payable VAT amount: accounts value are higher than the explained amounts
* Payable VAT amount: accounts value are lower than the explained amounts

The units will be split based on the type of VAT (receivable / payable).

We'll also build test cases that use multiple accounts and inputs to test the summations.

---
---

## OVERVIEW YAML TESTS

### Units

**UNIT 1:** Receivable VAT amount

**UNIT 2:** Payable VAT amount

---
---

### Tests per unit

**TEST 01:** default accounts value are equal to the explained amounts

**TEST 2:** manual accounts value are equal to the explained amounts

**TEST 3:** accounts value are higher than the explained amounts

**TEST 4:** accounts value are lower than the explained amounts

### New section

Pushing an update