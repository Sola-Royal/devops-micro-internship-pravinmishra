# Assignment 6 — Capstone: Deploy Book Review App (Three-Tier Architecture) on Azure

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

This is the most important assignment of the course. You will deploy the Book Review App in a production-ready, best-practice-compliant three-tier architecture on Azure: separated presentation, application, and database tiers, least-privilege network access, a controlled public entry point, protected secrets, and availability/monitoring evidence.

---

# Task 1 — Design the Azure Three-Tier Architecture

## Goal

Create an architecture diagram and implementation plan identifying the presentation, application, and database components, the chosen Azure services, the public entry point, and the internal traffic paths.

### Evidence

#### Screenshot 1 — Architecture diagram showing the public entry point, three tiers, network boundaries, and traffic flow

![alt text](image-30.png)

---

#### Screenshot 2 — Written architecture assumptions and selected Azure services

Selected Azure ServicesEdge Security & Routing: Azure Front Door with Web Application Firewall (WAF)Presentation Tier (Web): Azure App Service (Linux, Premium v3, Zone-Redundant)Business Tier (App/API): Azure App Service (Linux, Premium v3, Zone-Redundant)Data Tier (Database): Azure Database for PostgreSQL (Flexible Server, Zone-Redundant HA)Secrets & Security: Azure Key Vault using System-Assigned Managed IdentitiesMonitoring & Logging: Azure Monitor Application Insights & Log Analytics WorkspaceCore Implementation AssumptionsIdentity & Access: Azure Active Directory (Entra ID) handles all RBAC permissions for resource deployment.Public Access: No direct public internet ingress is permitted to the Web, App, or Data tiers; all traffic is forced through Azure Private Endpoints.SSL/TLS Termination: Custom domains and SSL certificates are managed entirely at the Azure Front Door edge.Network Capacity: The 10.0.0.0/16 VNet space provides sufficient IP headroom for future scale out across all four subnets.

---

# Task 2 — Create the Azure Network Foundation

## Goal

Create a dedicated Resource Group and VNet with separate subnets for the web, application, and database tiers, keeping the application and database tiers without direct public access.

### Evidence

#### Screenshot 3 — Resource Group overview showing the assignment resources

![alt text](image-31.png)
---

#### Screenshot 4 — VNet overview showing the address space and all required subnets

![alt text](image-32.png)

---

#### Screenshot 5 — Route-table or Private DNS evidence where applicable

![alt text](image-33.png)

---

# Task 3 — Configure Security and Secret Management

## Goal

Apply least-privilege NSG rules so traffic flows Internet → public entry point → web tier → application tier → database tier, and store credentials in Azure Key Vault or another approved secure mechanism.

### Evidence

#### Screenshot 6 — NSG rules proving least-privilege access between the tiers

![alt text](image-34.png).

---

#### Screenshot 7 — Key Vault or approved secret-management configuration (without displaying secret values)

Add your screenshot here.

---

# Task 4 — Deploy the Presentation (Web) Tier

## Goal

Deploy the Book Review App presentation layer on the approved web-tier compute service, configured to route requests to the internal application-tier endpoint, and not directly exposed except through the public entry service.

### Evidence

#### Screenshot 8 — Web-tier compute overview showing subnet and availability configuration

![alt text](image-35.png)

---

#### Screenshot 9 — Terminal or service output proving the presentation layer is running

![alt text](image-39.png)

---

# Task 5 — Deploy the Business (Application) Tier

## Goal

Deploy the Book Review App backend privately in the application subnet, configured to use the private database endpoint and secured environment values, reachable only through its internal endpoint.

### Evidence

#### Screenshot 10 — Application-tier compute overview showing private subnet placement

![alt text](image-37.png)

---

#### Screenshot 11 — Backend process, service, or listening-port evidence

![alt text](image-38.png)

---

#### Screenshot 12 — Internal health-check or API response (without exposing secrets)

![alt text](image-40.png)

---

# Task 6 — Deploy the Managed Database Tier

## Goal

Create a private Azure managed database (public access disabled), with availability/backup/retention settings, the Book Review App schema imported, and access restricted to the application tier only.

### Evidence

#### Screenshot 13 — Database overview showing private connectivity and public access disabled

![alt text](image-41.png)

---

#### Screenshot 14 — Availability, backup, and retention configuration

![alt text](image-42.png)

---

#### Screenshot 15 — Successful schema or connectivity verification (without exposing credentials)

![alt text](image-43.png)

---

# Task 7 — Configure Traffic Management, Availability, and Monitoring

## Goal

Configure the approved public entry service with health probes and backend pools, internal routing for the application tier where required, and enable Azure Monitor/diagnostics/logs/alerts for the key resources.

### Evidence

#### Screenshot 16 — Public entry service showing listener, frontend endpoint, and healthy web targets

![alt text](image-44.png)

---

#### Screenshot 17 — Internal application-tier load-balancing or routing configuration where applicable

![alt text](image-45.png)

---

#### Screenshot 18 — Azure Monitor, diagnostic settings, logs, metrics, or alert evidence

![alt text](image-46.png)

---

# Task 8 — Validate the Production-Style Deployment

## Goal

Confirm the Book Review App works end to end through the public endpoint, with at least one database read and one write, confirm private tiers are not internet-reachable, and complete a safe availability test.

### Evidence

#### Screenshot 19 — Browser showing the Book Review App through the public endpoint

![alt text](image-47.png)

---

#### Screenshot 20 — Proof of successful database-backed read and write operations

![alt text](image-48.png)

---

#### Screenshot 21 — Evidence that private tiers are not publicly accessible

![alt text](image-49.png)

---

#### Screenshot 22 — Availability-test and healthy-target evidence

![alt text](image-50.png)

---

#### Public Endpoint

Paste your public endpoint URL here:

http://74.248.34.9/

---

### Notes

Summarize what worked, issues encountered and how they were fixed, and the availability/security/secrets/monitoring/backup choices made.

Write your answer here.

---

# Submission Instructions

- Add all required screenshots and links in your submission
- Do not expose passwords, keys, connection strings, or subscription IDs

---

# Completion Checklist

- [ ] Task 1: Architecture diagram and assumptions documented (Screenshots 1–2)
- [ ] Task 2: Network foundation created with isolated tiers (Screenshots 3–5)
- [ ] Task 3: Least-privilege security and secret management configured (Screenshots 6–7)
- [ ] Task 4: Presentation tier deployed (Screenshots 8–9)
- [ ] Task 5: Application tier deployed privately (Screenshots 10–12)
- [ ] Task 6: Managed database tier deployed privately (Screenshots 13–15)
- [ ] Task 7: Public entry, internal routing, and monitoring configured (Screenshots 16–18)
- [ ] Task 8: End-to-end validation and availability test completed (Screenshots 19–22, Public Endpoint, Notes)
- [ ] No sensitive data exposed

---

## 📌 About DMI & CloudAdvisory

DevOps Micro Internship (DMI) is a project-based DevOps program run by Pravin Mishra (The CloudAdvisory) focused on real-world execution, systems thinking, and career readiness.

It helps learners build strong DevOps foundations with hands-on experience.

---

## 📌 Resources

- 🌐 DMI Official Website: https://dmi.pravinmishra.com?utm_source=github&utm_medium=readme  
- 🎓 University: https://university.pravinmishra.com?utm_source=github&utm_medium=readme  
- 💬 Discord Community: https://discord.pravinmishra.com?utm_source=github&utm_medium=readme  
- 📝 Blog: https://dmi.pravinmishra.com/blog?utm_source=github&utm_medium=readme  
- ▶️ YouTube Playlist: https://www.youtube.com/playlist?list=PLFeSNDtI4Cho  
- 🔗 Pravin Mishra (LinkedIn): https://www.linkedin.com/in/pravin-mishra-aws-trainer/  
- 🏢 CloudAdvisory (LinkedIn): https://www.linkedin.com/company/thecloudadvisory/

---

*This submission is part of DevOps Micro Internship (DMI) — Agentic AI Track.*
