---
title: "Business Context, Opportunity & Requirements Brief"
domain: "business-context"
version: "1.0"
status: "APPROVED"
owner: "Sarah Chen (Business Manager)"
approved_by: "sarah.chen@example.com"
approved_at: "2025-12-01T09:00:00Z"
created: "2025-11-28"
updated: "2025-12-01"
project: "Medication Adherence Platform"
structure_hash: "sha256:cb2d88a9b0309db8"
---

# Medication Adherence — Business Context, Opportunity & Requirements Brief

This document defines the foundational business context, opportunity, and
high-level requirements for the Medication Adherence Platform. It provides the
upstream source for Business Context SCDs and frames *why* this initiative
exists, *who* benefits, and *what* success looks like. It avoids solution detail
and defers architecture, UX, data, and operational specifics to their respective
domains.

---

## 1. Problem Overview

Medication non-adherence remains a major clinical and economic challenge across
the U.S. healthcare system. Studies consistently show that:

- ~50% of patients do not take medications as prescribed  
- Non-adherence leads to avoidable hospitalizations, complications, and costs  
- Clinicians lack visibility into patient behavior between visits  
- Existing reminder apps are fragmented, non-clinical, and do not integrate into
  care workflows  

For high-risk conditions (diabetes, hypertension, post-operative recovery), even
small deviations from medication timing or frequency can meaningfully impact
outcomes.

Health systems lack a unified, clinically integrated tool to help patients stay
on track and give clinicians real-time insight into adherence patterns.

---

## 2. Target Users & Stakeholders

### **Primary Users**
**Patients** taking chronic or complex medication regimens:
- Elderly adults with polypharmacy  
- Post-operative patients during recovery  
- People managing chronic conditions  
- Individuals with low tech literacy  

**Needs:**  
Clear reminders, simple check-ins, supportive language, easy visibility into
daily medications.

---

### **Secondary Users**
**Clinicians**  
- Need actionable adherence signals  
- Need escalation visibility  

**Care Coordinators / Population Health Teams**  
- Monitor at-risk patients  
- Manage outreach workflows  

**Pharmacists (optional future persona)**  
- Provide medication counseling  
- View adherence patterns  

---

### **Internal Stakeholders**
- Clinical leadership  
- Compliance & privacy  
- IT & integrations  
- Data science  
- Care management leadership  
- Operations / program implementation teams  

Each has a different requirement for safety, reliability, compliance,
transparency, and workflow fit.

---

## 3. Why Now

Several factors converge to make this initiative time-critical:

- Health systems are moving toward **value-based care**, where outcomes and
  readmissions affect reimbursement.  
- CMS and payer programs increasingly require **adherence reporting**.  
- Trends in remote care demand continuous patient insight.  
- The rise of generative AI makes personalized reminder timing feasible.  
- Clinicians face burnout and need tools that surface only the highest-risk
  patients.  
- Patients expect accessible, mobile-friendly interactions.  

Not pursuing this opportunity risks poor patient outcomes, lost revenue
opportunities, and failure to meet regulatory and contracting requirements.

---

## 4. Opportunity Summary

This initiative enables:

- Improved clinical outcomes through better adherence  
- Reduction in readmissions and complications  
- Increased patient engagement and satisfaction  
- More efficient clinician workflows  
- Stronger payer and regulatory alignment  
- Differentiation for partnering health systems  

A unified adherence platform that integrates with EHR systems and care teams is
a competitive differentiator. It can also expand into additional behavioral
domains (activity, recovery milestones, PROs).

---

## 5. Desired Business Outcomes

- Increase medication adherence rates across target populations  
- Reduce missed doses for high-risk medications  
- Improve clinician visibility into adherence in near real time  
- Reduce avoidable readmissions or postoperative complications  
- Improve patient communication and engagement  
- Support health system reporting for payer/regulatory programs  
- Enable care teams to focus on the right patients at the right time  

Success must be measurable, sustainable, and tied directly to clinical and
financial outcomes.

---

## 6. Guiding Principles & Vision

### **Vision**
A simple, supportive platform that helps patients stay on track with their
medications and gives clinicians clear visibility into adherence patterns in
real time.

### **Principles**
- **Supportive, not punitive** — encourage patients, never shame them.  
- **Clinically trustworthy** — based on accurate data synced from EHRs.  
- **Accessible for everyone** — designed especially for older adults.  
- **Actionable for care teams** — highlight what matters, not everything.  
- **Safe by design** — reminders must be accurate; no clinical decisions automated.  
- **Interoperable** — integrates cleanly with EHR workflows and care systems.  

---

## 7. Key Assumptions

- Patients will use a mobile app or SMS for reminders.  
- EHR integration for medication lists is feasible.  
- Clinicians will use dashboards integrated into existing workflows.  
- AI-based prediction can enhance but not replace clinician judgment.  
- SMS will remain a primary communication channel for certain populations.  
- Customers will require HIPAA compliance from day one.  

---

## 8. Constraints

- Must meet HIPAA, SOC2, and health system compliance requirements.  
- Medication data must remain authoritative from the EHR.  
- Reminders must reflect exact dosing schedules; no drift allowed.  
- Must support low-literacy and low-tech-literacy users.  
- Notification timing accuracy is safety-critical.  
- Deployment in healthcare environments may require vendor security review.  

---

## 9. Target Personas & Key Use Cases

### **Personas**
1. **Elderly patient (primary)**  
   Needs clear reminders, large text, simple check-ins.

2. **Chronic condition patient**  
   Needs consistency, predictability, and supportive messaging.

3. **Clinician**  
   Needs concise, actionable adherence risk insights.

4. **Care coordinator**  
   Needs to identify high-risk patients quickly.

---

### **Use Cases**
- Patient receives reminder and confirms dose with one tap  
- Patient views medication schedule for today  
- Patient reviews missed doses and next steps  
- Clinician reviews adherence trends over the last 30 days  
- Coordinator reviews which patients need outreach  
- Admin configures program-level reminder settings  

Notably, none of these specify implementation detail—only intent.

---

## 10. High-Level Solution Direction

The Medication Adherence Platform will:

- Aggregate accurate medication schedules from EHR systems  
- Deliver reliable reminders through mobile and SMS  
- Capture adherence events in real time  
- Provide clinicians with meaningful insights  
- Use AI to enrich—but never replace—clinical evaluation  
- Support escalation workflows for at-risk patients  

Out of scope (at this stage):  
- Automated medication plan changes  
- Clinical diagnosis, triage, or decision-making  
- Pharmacy dispensing or refill workflows  

---

## 11. High-Level Functional Requirements

The system must:

- Provide medication reminders with precise timing  
- Allow patients to confirm or skip doses  
- Sync medication schedules with source-of-truth EHR  
- Handle missed dose logic and escalation flags  
- Provide clinician dashboards with adherence summaries  
- Support outreach workflows  
- Ensure safe and predictable behavior even with limited connectivity  

These are directional only; detailed requirements live in domain SCDs.

---

## 12. UX Considerations

- Simple, supportive, low-friction interactions  
- Minimal steps to complete a check-in  
- Large touch targets and adjustable text sizes  
- High contrast visual design  
- Cognitive load minimized (one main action per view)  
- Clear separation of “due now,” “upcoming,” “completed”  
- Accessible language, 6th-grade reading level  

Deep UX detail resides in the Usability & Accessibility domain.

---

## 13. Technical Considerations

- Must integrate with EHR medication data (FHIR R4 MedicationRequest,
  MedicationStatement, CarePlan).  
- Must support secure, encrypted communication channels.  
- Must scale to large cohorts with peak reminder traffic.  
- Must provide accurate audit logs for compliance.  
- Requires production-grade notification delivery pipeline.  
- Must support future AI components for risk prediction.  

Detailed architecture remains out of scope here.

---

## 14. Data Requirements

- Must ingest and maintain medication schedules from the EHR.  
- Must store adherence events (confirmations, skips).  
- Must support audit logging of all reminder events.  
- Must support analytics on adherence patterns at patient and cohort level.  
- Retention policies required for PHI.  
- Data provenance must be fully traceable for clinical audit.  

Detailed modeling belongs in Data-Provenance domain.

---

## 15. Edge Cases & Error Themes

- Medication schedule changes mid-day  
- Offline or poor network situations  
- SMS failures or delays  
- Duplicate check-ins  
- Medication plans mismatched across systems  
- Time zone changes or travel  
- Patients with irregular routines  

UX patterns and system guards are domain-specific elsewhere.

---

## 16. Dependencies & External Factors

- EHR integration partner  
- SMS vendor reliability and throughput  
- Customer IT onboarding processes  
- Patient identity and authentication system  
- Clinical leadership approval of escalation logic  
- Data science availability for AI features  
- Compliance/legal team early involvement  

---

## 17. Measurement & Success Metrics

**Clinical metrics**
- Increase in adherence rates  
- Reduction in missed doses  
- Reduction in complication or readmission rates  

**Operational metrics**
- Reduced clinician review time  
- Reduced manual outreach volume  

**Product metrics**
- DAU / MAU retention  
- Reminder → check-in conversion rate  
- Error-free reminder delivery %  

**Experience metrics**
- SUS score improvement  
- Reduced confusion/frustration events  
- Accessibility testing pass rates  

---

## 18. Open Questions

- What level of personalization do customers want?  
- How will we handle medication plans that conflict between systems?  
- How much AI transparency do clinicians require?  
- Should SMS-only patients receive simplified workflows?  
- Will health systems require deep co-branding?  
- Are adherence patterns considered clinical data for long-term storage?  

---

## 19. Appendices (Optional)
- Early user interviews  
- Market scans of adherence solutions  
- Compliance notes (HIPAA, CMS, CHAI)  
- AI risk considerations  
- EHR integration assumptions  