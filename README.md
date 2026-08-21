# AWS IAM Least-Privilege Architecture — Oil & Gas (Simulated)

A simulated multi-department IAM structure built on AWS, designed around least-privilege access and enforced MFA — modeled on the kind of access control a mid-sized oil & gas operator would need across engineering, finance, and operations teams.

## Why this project

Most IAM examples online show a single flat policy. In a real organization, different departments need genuinely different access — an engineer shouldn't be able to touch billing, and finance shouldn't be able to spin up EC2 instances. This project builds that separation out properly: department-scoped IAM groups, least-privilege policies attached per group, and MFA enforced at the user level.

## What it covers

- **Department-based IAM groups** — separate groups per function (e.g. engineering, finance, operations), each with only the permissions that function actually needs.
- **Least-privilege policy design** — custom JSON policies scoped to specific actions and resources rather than relying on AWS managed policies with broad grants.
- **MFA enforcement** — a policy that denies most actions unless the user has authenticated with MFA, following AWS's recommended enforcement pattern.
- **User and group provisioning** — scripts to create IAM users, assign them to the correct department group, and apply the associated policy.

## A note on process

While building this, I caught a hardcoded AWS account ID committed in an early version of one of the policy files — a real security mistake, not a hypothetical one. I corrected it before the project went further, which is part of why the policies here are written to avoid hardcoded account-specific values where possible.

## Tools

AWS IAM, AWS CLI / shell scripting for provisioning, JSON policy documents.

## Status

Portfolio / simulated environment — not connected to a production AWS account. Built to demonstrate IAM design thinking, not as a drop-in production template.
