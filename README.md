# AWS WAF & CAF Assessment – Two-Tier Web Application Migration

## Overview

This repository contains the deliverables for the **"Design and Evaluate an AWS Solution Using the Well-Architected and Cloud Adoption Frameworks"** lab.

The scenario covers migrating a two-tier web application (frontend web server + backend relational database) from on-premises infrastructure to AWS, evaluated through two complementary AWS frameworks:

- **AWS Well-Architected Framework (WAF)** – 5 pillars
- **AWS Cloud Adoption Framework (CAF)** – 6 perspectives

---

## Repository Structure

```
├── README.md                                  ← This file
├── aws_waf_caf_assessment.md                  ← Full assessment report (Tasks 1–4 + Reflection)
└── AWS_Two-Tier_Web_App_Architecture.jpeg     ← Architecture diagram (submitted)
```

### Quick Links

| File | Description |
|------|-------------|
| [aws_waf_caf_assessment.md](aws_waf_caf_assessment.md) | Full lab report — Tasks 1–4 + Reflection |
| [Architecture Diagram](AWS_Two-Tier_Web_App_Architecture.jpeg) | Improved two-tier AWS architecture (JPEG) |

---

## Deliverables Summary

| Deliverable | Location | Description |
|------------|----------|-------------|
| WAF Assessment Table | `aws_waf_caf_assessment.md` → Task 2 | 5-pillar evaluation with strengths, improvements, and supporting AWS services |
| CAF Readiness Summary | `aws_waf_caf_assessment.md` → Task 3 | ~150–200 words per perspective across all 6 CAF perspectives |
| Improved Architecture | `aws_waf_caf_assessment.md` → Task 4 | Multi-AZ, secure, auto-scaling architecture with full AWS service mapping |
| Reflection | `aws_waf_caf_assessment.md` → Reflection | 150-word learning reflection |

---

## Approach

### Task 1 – Architecture Review
Identified all components shown in the architecture diagram: Amazon Route 53, Internet Gateway, Application Load Balancer, EC2 Auto Scaling Group (Web/App), two NAT Gateways, RDS Primary and RDS Standby (Multi-AZ with sync replication), S3 Backups, and the Security & Operations layer (CloudWatch, CloudTrail, GuardDuty, KMS). On-premises risks including single points of failure, absent backups, and permissive security configurations were documented.

### Task 2 – WAF Evaluation
Each of the five WAF pillars was evaluated directly against the services visible in the architecture diagram. Strengths were drawn from what the diagram already shows (e.g., RDS Multi-AZ, GuardDuty, CloudTrail, KMS, Auto Scaling). Gaps were identified where the diagram lacks coverage (e.g., no WAF on ALB, no Secrets Manager, no caching layer, no cost tagging strategy).

### Task 3 – CAF Readiness
All six CAF perspectives (Business, People, Governance, Platform, Security, Operations) were analysed for organisational readiness and tailored to the architecture in the diagram. Key actions and enablers were identified for each perspective.

### Task 4 – Improved Architecture
The architecture described in Task 4 directly reflects the submitted diagram, covering:

- Amazon Route 53 for DNS routing
- Internet Gateway → ALB → EC2 Auto Scaling Group (public subnets)
- RDS Primary + RDS Standby with synchronous Multi-AZ replication (private subnets)
- NAT Gateways (one per public subnet/AZ) for private subnet outbound access
- S3 Backups (AWS Cloud) for automated RDS backup storage
- Security & Operations layer: CloudWatch, CloudTrail, GuardDuty, KMS
- Recommended additions: AWS WAF on ALB and AWS Secrets Manager

---

## AWS Services Referenced

**In the Architecture Diagram:**
- Amazon Route 53, Internet Gateway, Application Load Balancer
- EC2 Auto Scaling Group (Web/App), NAT Gateway x2
- Amazon RDS (Multi-AZ: Primary + Standby with sync replication)
- Amazon S3 (Backups), AWS KMS
- Amazon CloudWatch, AWS CloudTrail, Amazon GuardDuty

**Recommended Additions (not yet in diagram):**
- AWS WAF (attach to ALB), AWS Secrets Manager
- Amazon ElastiCache (Redis), AWS Compute Optimizer
- AWS CodePipeline, AWS CloudFormation
- AWS Cost Explorer, AWS Budgets, EC2 Savings Plans, AWS Trusted Advisor
- AWS Systems Manager, AWS Control Tower, AWS Organizations

---

## How to Use This Repository

1. Open [aws_waf_caf_assessment.md](aws_waf_caf_assessment.md) for the full lab report
2. View the [Architecture Diagram](AWS_Two-Tier_Web_App_Architecture.jpeg) — also embedded inside Task 4 of the assessment
3. Use the WAF table (Task 2) as a quick reference for pillar-by-pillar findings

---

*Lab: Design and Evaluate an AWS Solution Using the Well-Architected and Cloud Adoption Frameworks*
