# Access Control Lab

## Objective
Test an access-control weakness in an authorized PortSwigger Web Security Academy training lab.

## Observation
The lab provided an administrative function that was accessible without the expected access restriction.

## Hypothesis
The administrative functionality may be accessible to an unauthorized user because access control is not being properly enforced.

## Test
I inspected the application and accessed the administrative functionality through the path disclosed by the training lab.

## Evidence
The administrative panel was accessible through the discovered administrative path in the authorized PortSwigger training environment.

## Result
The lab demonstrated that sensitive administrative functionality could be accessed without the expected authorization check.

## Lesson Learned
Authentication and authorization are separate controls. An application must verify that an authenticated user is actually authorized to access sensitive functionality.
