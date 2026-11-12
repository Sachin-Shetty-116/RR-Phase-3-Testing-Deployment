# RELEASE RUSH - PHASE 3 SUBMISSION

Team Name: RR-Phase-3
Team Members: Sachin Shetty (Sachin-Shetty-116)
Submission Time: 2026-11-12 15:16 IST

## CHALLENGE 3 - AUTOMATED TESTING (15 MARKS)

1. What was the root cause?
In `pricing.py`, the discount calculation was subtracting the discount percentage directly as a flat currency amount (`amount - discount_percent`), rather than calculating the percentage deduction from the total amount (`amount * (discount_percent / 100)`).

2. Which line or function was incorrect?
Function: `calculate_final_price` in `challenge-3-testing/pricing.py` (Line 11):
`return round(amount - discount_percent, 2)`

3. What correction did you make?
Updated the return expression to calculate the percentage discount proportionally:
`return round(amount * (1 - discount_percent / 100), 2)`

4. What was the correct calculation formula?
`final_price = round(amount * (1 - discount_percent / 100), 2)`

5. Attach or demonstrate the passing test output.
```
test_full_discount (test_pricing.TestPricing.test_full_discount) ... ok
test_invalid_discount (test_pricing.TestPricing.test_invalid_discount) ... ok
test_ten_percent_discount (test_pricing.TestPricing.test_ten_percent_discount) ... ok
test_twenty_five_percent_discount (test_pricing.TestPricing.test_twenty_five_percent_discount) ... ok
test_zero_discount (test_pricing.TestPricing.test_zero_discount) ... ok

----------------------------------------------------------------------
Ran 5 tests in 0.000s

OK
```

6. What is your fix commit hash?
Will be recorded in the final commit.

## CHALLENGE 4 - DEPLOYMENT RECOVERY (20 MARKS)

1. On which port does the application listen inside the container?
Port 8000 (specified in `server.py` and `Dockerfile` via `ENV PORT=8000`).

2. What was the incorrect port mapping?
`"8080:8080"` in `challenge-4-deployment/compose.yaml` (mapping host port 8080 to container port 8080).

3. What corrected mapping did you apply?
`"8080:8000"` in `challenge-4-deployment/compose.yaml` (mapping host port 8080 to container port 8000).

4. What HTTP response did the /health endpoint return?
HTTP 200 OK
`{"status":"ok"}`

5. Demonstrate your passing deployment workflow.
The `Phase 3 - Deployment Recovery` GitHub Actions workflow runs:
`docker compose -f challenge-4-deployment/compose.yaml up --build --detach`
and verifies `curl http://127.0.0.1:8080/health`.
Output:
`Deployment health check passed.`

6. What is your fix commit hash?
Will be recorded in the final commit.

## FINAL EVIDENCE

- Testing workflow URL: https://github.com/Sachin-Shetty-116/RR-Phase-3-Testing-Deployment/actions/workflows/testing.yml
- Deployment workflow URL: https://github.com/Sachin-Shetty-116/RR-Phase-3-Testing-Deployment/actions/workflows/deployment.yml
- Relevant commit URLs: https://github.com/Sachin-Shetty-116/RR-Phase-3-Testing-Deployment/commits/main
- Evaluator comments: Both Challenge 3 and Challenge 4 resolved and validated green via GitHub Actions.
