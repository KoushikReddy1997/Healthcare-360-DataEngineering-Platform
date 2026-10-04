# Healthcare-360-DataEngineering-Platform

1. Project Overview: Healthcare Claims, Membership & Provider Analytics Platform

Healthcare 360: Claims, Membership & Provider Analytics Platform
- Business domain: Healthcare insurance Analytics
- Project type: End-to-end batch ELT data platform
- Architecture: Cloud object storage(S3) + Databricks Lakehouse + dbt + orchestration
- Primary goal: Build a reliable and scalable data platform that consolidates membership, provider, and medical claims data from different source systems and produces trusted analytical datasets for business reporting.

Key Business Questions
The platform will answer:
1. What is the total medical claim cost by month, provider, member, and insurance plan?
2. Which providers have the highest claim volume and total allowed amounts?
3. What percentage of claims are denied, rejected, or paid?
4. Are claims being submitted for members who were not eligible on the date of service?
5. Which providers have unusually high average claim costs?
6. How are medical costs trending by geographic region and provider specialty?
7. How long does it take from claim submission to payment?
8. Are there duplicate claims, missing provider details, or invalid claim amounts?

Workflow 

                   GitHub
               (Version Control)
                     │
                     ↓
               GitHub Actions
                  (CI/CD)
                     │
                     ↓
AWS S3 ───────→ Databricks
Source             │
CSV/JSON/           │
Parquet             ↓
                  BRONZE
               Raw/Ingested Data
                     │
                     ↓
                  dbt Core
          Transformations + Testing
             + Data Quality
                     │
              ┌──────┴──────┐
              ↓             ↓
            SILVER         GOLD
          Cleaned &       Business/
          Conformed       Aggregated
              │             │
              └──────┬──────┘
                     │
                     ↓
            Databricks Workflows
               Orchestration
                     │
                     ↓
             Monitoring / Audit
