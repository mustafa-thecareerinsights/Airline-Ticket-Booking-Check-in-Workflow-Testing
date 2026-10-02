# Test Execution and Defect Report

**Employee:** Kaleemuddin Mohammed  
**Project:** Airline Ticket Booking & Check-in Workflow Testing

## Execution Summary
- Total test cases: 20
- Passed: 17
- Failed: 3
- Pass rate: 85%
- Environment: local assignment simulation
- No live airline system or real booking transaction was used.

## Defects

### ATB-DEF-001 - Past travel date is accepted
- Severity: High
- Test Case: ATB-004
- Expected: Past travel date must be rejected.
- Actual: Search continued with a past date.
- Recommendation: Enforce client-side and server-side travel-date validation.

### ATB-DEF-002 - Multiple seats temporarily reserved during rapid selection
- Severity: Medium
- Test Case: ATB-010
- Expected: Only one seat should remain selected for a passenger.
- Actual: Two seats were temporarily held.
- Recommendation: Lock seat state and release the previous selection atomically.

### ATB-DEF-003 - Retry after timeout can create duplicate booking reference
- Severity: Critical
- Test Case: ATB-020
- Expected: Retry should reuse an idempotency key and create one booking only.
- Actual: A second booking reference was generated.
- Recommendation: Add idempotent booking confirmation handling before release.

## Conclusion
The standard search, passenger, baggage, booking, and check-in flows worked as expected in the simulation. The duplicate-booking defect should be treated as the release blocker.
