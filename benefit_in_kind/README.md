# Benefit in Kind documentation

## TEST CASES REASONING

### Vehicle - age factor

For vehicles, there are couple of different cases we should test depending on the bookyear data and the vehicles can also have an additionnal date factor we should consider compared to the other benefits. (benefit start- and end date can differ based on date first registration, date entry into service and date out of service)

---
---

## OVERVIEW YAML TESTS

### Vehicle - age factor


### Units

**UNIT 1:** Vehicle - age factor - calendar year

**UNIT 2:** Vehicle - age factor - broken year

---
---

* **TEST 1:** Date first registration is inside bookyear + No date out of service + car age 2 months 
* **TEST 2:** Date first registration is outside bookyear + No date out of service + car age 14 months
* **TEST 3:** Date first registration is outside bookyear + No date out of service + car age 67 months
* **TEST 4:** Date first registration is outside bookyear + No date out of service + car age factor switch equals exact bookyear
* **TEST 5:** Date first registration is inside bookyear + Date out of service inside bookyear
* **TEST 6:** Date first registration is outside bookyear + Date out of service inside bookyear
* **TEST 7:** Date first registration is outside bookyear + Date out of service in previous bookyear