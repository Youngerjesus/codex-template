# Test Layer Selection

Pick the cheapest layer that can reproduce the failure honestly.

## Default Order

1. Unit test
2. Integration or API test
3. Browser or end-to-end reproduction
4. One-off script or targeted command

Escalate only when the cheaper layer cannot represent the real failure mode.
