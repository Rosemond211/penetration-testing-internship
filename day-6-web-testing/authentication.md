# Authentication Lab

## Objective
Test an authentication-related weakness in an authorized PortSwigger Web Security Academy training lab.

## Observation
The training lab demonstrated a situation where the application's authentication process did not properly protect access.

## Hypothesis
The authentication mechanism may allow access without correctly verifying the required credentials or authentication state.

## Test
I inspected the authentication behavior within the authorized training environment and tested the lab's provided scenario.

## Evidence
The observed application behavior demonstrated the authentication weakness described by the training lab.

## Result
The lab confirmed that the authentication control could be bypassed or improperly handled under the conditions provided by the exercise.

## Lesson Learned
Authentication verifies who a user is, while authorization determines what that user is allowed to access. Both controls must be implemented correctly.
