# Cybersecurity Frameworks and Maturity

Now that we've covered the basics and some regulations and compliance, let's dive into how it's all implemented.

We talked about business needs. Whether you're working with a small organization or a large organization, it all comes down to business needs.

How do we implement them, though?

Fortunately, some organizations and governments have put together some frameworks for us—things that they either require or things that we can start with.

We're going to go through these frameworks:
- ISO/IEC 27000
- COBIT
- NIST (Cybersecurity Framework)
- CIS
- US Government’s CMMC
- Australia’s ASD

---

## ISO/IEC 27000

- Developed by the **International Organization for Standardization (ISO)** and the **International Electrotechnical Commission (IEC)**.
- Guidelines are **broad in scope**, covering more than privacy, confidentiality, and cybersecurity.
- Applicable to **organizations of any size**.
- Broken into multiple publications:
  - **ISO 27001**: Requirements. It's the basis.
  - **ISO 27002**: Code of practice for how to implement controls.
- Widely used globally by organizations and governments.

---

## COBIT (Control Objectives for Information Related Technologies)

- Created by **ISACA**.
- Goes beyond IT management into **IT governance**.
- Covers **business goals and generic IT processes**, not just cybersecurity.
- Provides a broader picture useful for many organizations.

---

## NIST Special Publication 800-53

- From the **National Institute of Standards and Technology (NIST)**, USA.
- Required for **all US federal information systems** (except national security).
- A **catalog of security and privacy controls**.
- Provides:
  - Baseline controls (800-53B)
  - Guides assessment scope and feedback.
- Agencies are expected to be compliant.
- Helps understand:
  - What controls an organization already follows.
  - What needs to be included in reports.
  - How to relate findings back to customers.

---

## CIS (Center for Internet Security)

- Non-profit organization.
- Provides **18 prioritized safeguards** to prevent cyber-attacks.
- Follows a **defense-in-depth model**.
- Offers a **free tool** for self-assessment.
- Builds strategies based on the most prevalent attacks.
- Easy to understand and implement.
- Free products available.

---

## CMMC (Cybersecurity Maturity Model Certification)

- Developed by the **US Department of Defense (DoD)**.
- A **training, certification, and third-party assessment program**.
- Applies to any company working with or touching the **DoD**.
- Compliance is **mandatory**.
- CMMC Version 2:
  - **Five Maturity Levels**.
  - **17 Capability Domains**.
- Enables tiered access to different levels of classified information.
- Higher levels mean more sensitive access.

### CMMC Maturity Levels

- **Level 1: Performed** – Basic security practices.
- **Level 5: Optimizing** – Defining new industry practices and baselines.

---

## ASD Essential Eight (Australia)

- Developed by the **Australian Cyber Security Centre** and the **Australian Signals Directorate**.
- Known as the **Essential Eight**.
- A **baseline framework** to defend against cyber threats.
- Publicly available and globally applicable.
- Targets **Microsoft Windows-based** systems.
- Defines **4 maturity levels**:
  - Start small and grow toward best practices.
- Helps organizations assess:
  - Current security maturity.
  - Where to improve.
  - How to move to the next level.

---

## Why This Matters

Why are we covering this in a pentesting course?

Because your **penetration test results need to align** with the customer's business and framework.

You must **add value**. Your report must fit into their:
- Risk management model.
- Compliance framework.
- Maturity level.

### Tiered Recommendations

- Must-do: Critical, could lead to breach.
- Should-do: Important.
- Could-do: Nice to have.
- Extra recommendations: For long-term maturity.

**Severity levels and tiering** are important.

**Use their language** to maximize report value.

---

## Before Pentesting: Start with Auditing

- Understand what auditing involves before diving into pentesting.
- Many organizations can begin with an audit.
- Audits can guide:
  - Implementation.
  - Risk posture.
  - Scope of pentesting.


