# Product Process Flow in Jira Product Discovery (JPD)

## Document Information

| Item | Details |
| :---- | :---- |
| Document Title | Product Process Flow in Jira Product Discovery (JPD) |
| Purpose | Define the end-to-end product idea lifecycle from ideation to validation and closure |
| Applicable Teams | Product Management, Product Designing, Product Engineers |
| Primary Tool | Jira Product Discovery (JPD) |
| Version | 1.0 |
| Owner | Product Management |
| Last Updated | \_\_\_\_\_\_\_\_\_\_ |

# 1\. [Product Discovery Template](https://docs.google.com/document/d/1f7jsl6krCk2KF4S9ck66VG7R9jgKTUicHWpJykV25z8/edit?usp=sharing)

//tech depth, existing products plan, risk- update, idea validation, feature doc explore in JPD, for existing improvisation in existing running product / idea, decide data / insight quality / reliability including customer interviews or primary and secondary research, stakeholder clarity, raci matrix with TL inclusion, flowchart, cumulative approach \- for feature / product process execution

# 2\. Product Idea Lifecycle

The Product Idea Lifecycle provides a structured approach to evaluate, validate, deliver, measure, and close ideas.

The objective is to ensure that investments are aligned with customer needs, business goals, and technical feasibility before significant delivery effort is committed.

## **Lifecycle Overview**

Parking Lot  
↓  
Discovery  
↓  
Ready for Delivery  
↓  
Delivery  
↓  
Value Assessment  
↓  
Done

Rejected (Terminal State – reachable from any stage)

On-Hold (Temporary State – Can be entered from any active stage and resumed back to the originating stage)

# **Product Trio**

The Product Trio collaborates throughout the lifecycle.

| Role | Description |
| ----- | ----- |
| PM | Product Manager |
| PD | Product Designer |
| EM | Engineering Manager (Software / Hardware / Mechanical / Certification as applicable) |

The Product Trio is jointly responsible for ensuring customer value, business value, usability, and technical feasibility throughout the lifecycle.

Accountability for idea outcomes remains with the Product Manager, while Product Designer and Engineering Manager provide expertise in desirability, usability, and feasibility respectively.

# Stage 1: Parking Lot

## Purpose

Capture and organize raw ideas without committing delivery resources.

### Inputs

| Input Type | Examples |
| :---- | :---- |
| Customer Feedback | Feature requests |
| Internal Suggestions | Team proposals / Part / Component changes |
| Market Trends | Competitive insights |
| Strategic Initiatives | Business opportunities |

### Activities

* Log the idea in JPD

* Categorize and tag appropriately

* Attach supporting documents, screenshots, or references

* Record submitter information

| Role | Responsibilities |
| ----- | ----- |
| PM | Capture idea, understand source, categorize opportunity, identify strategic alignment |
| PD | Provide initial perspective on customer experience implications if required |
| EM | Identify obvious technical constraints or dependencies if known |
| Stakeholders | Submit ideas, provide context and business justification |

## **Stage Outcome**

| Decision | Next Stage |
| ----- | ----- |
| Accepted | Discovery |
| On-Hold | On-Hold |
| Rejected | Rejected |

### Jira Artifact

**JPD Idea**

### **Stage In-Charge:** 

Product Manager

### **Approval Authority:**

Product Leader / CEO / to be updated

# Stage 2: Discovery

## Purpose

Validate whether the idea is worth investing in.

### Inputs

| Input | Description |
| ----- | ----- |
| Idea from Parking Lot | An approved idea that has been accepted for further evaluation and validation. |

| ~~Input~~ |
| :---- |
| ~~Idea from Parking Lot~~ |
| ~~Customer Research~~ |
| ~~Market Analysis~~ |
| ~~Competitive Analysis~~ |
| ~~Technical Feasibility Assessment~~ |

### Activities

* Problem validation

* Customer interviews

* User research

* Workflow analysis

* Competitive analysis

* Technical feasibility assessment

* Impact vs effort evaluation

* Solution exploration

* Validate desirability, viability, usability, and feasibility


| Role | Responsibilities |
| :---- | :---- |
| PM | Problem discovery, customer interviews, business case, prioritization, PRD ownership |
| PD | User research, journey mapping, workflows, wireframes, usability validation |
| EM | Technical feasibility assessment, architecture exploration, effort estimation, risk identification |

### 

### Outcome (Discovery Idea)

| Decision | Next Stage |
| ----- | ----- |
| Accepted | PRD Creation → Ready for Delivery |
| Rework Required | Discovery |
| On-Hold | On-Hold |
| Rejected | Rejected |

### Deliverables 

* Discovery Record

* Research Findings

* Prioritization Assessment

* PRD (if Accepted)

### Jira Artifact

* Updated JPD Idea

* Linked Confluence PRD

### **Stage In-Charge:** 

Product Trio

### **Approval Authority:**

Product Manager

# Stage 3: Ready for Delivery

## Purpose

Translate validated requirements into executable delivery work.

## **Inputs**

* Discovery Record  
* Product Requirements Document (PRD)  
* UX Designs  
* Technical Assessments

### Activities

* Create Epics

* Create User Stories

* Grooming followed by Estimate story points

* Assign Sprint Targets

* Conduct Design and Technical Reviews

Convert validated opportunities into executable work.

| Role | Responsibilities |
| :---- | :---- |
| PM | Epic creation, Story definition, acceptance criteria, prioritization, backlog readiness |
| PD | Final UX specifications, design review, edge case validation |
| EM | Epic decomposition, estimation review, technical planning, dependency management |

### Outcome

A fully groomed and prioritized backlog ready for implementation.

## **Stage Outcome**

| Decision | Next Stage |
| :---- | :---- |
| Accepted | Delivery |
| Rework Required | Discovery |
| On-Hold | On-Hold |
| Cancelled | Rejected |

### Deliverables

* Epics department-wise

* User Stories (business \+ technical) & Sprint-ready Backlog

## **Cross-Functional Delivery Tracking**

Each approved Product Idea remains the single source of truth in Jira Product Discovery.

Once the idea enters **Ready for Delivery**, work is decomposed into department-specific execution artifacts within Jira Software.

Example structure:

Product Idea (JPD)

├── Hardware Epic  
│ ├── PCB Design  
│ ├── Component Selection  
│ └── Prototype Validation  
│  
├── Firmware Epic  
│ ├── Camera Driver  
│ ├── ISP Integration  
│ └── OTA Support  
│  
├── AI Epic  
│ ├── Object Detection  
│ ├── Face Recognition  
│ └── Model Optimization  
│  
├── Mechanical Epic  
│ ├── Enclosure Design  
│ ├── Thermal Validation  
│ └── IP Rating Tests  
│  
├── Cloud Epic  
│  
├── Mobile App Epic  
│  
├── Manufacturing Epic  
│  
└── Certification Epic

Each department manages its own sprint cadence and backlog while maintaining traceability through linked Epics back to the originating Product Idea.

The Product Manager will be aware of the overall progress through the Product Idea, while Engineering Managers are responsible for execution within their respective department and cross-departments based on the need.

### **Stage In-Charge:**

Product Trio

# Stage 4: Delivery

## Purpose

Build, test, and release the approved solution.

### Inputs

| Input |
| :---- |
| Groomed Backlog |
| Sprint Plan |
| Design Assets |
| Test Cases |

### Activities

* Sprint Execution

* Development

* Code Reviews

* QA Testing

* Defect Resolution

* Sprint Demo

* Staging Deployment

* User Acceptance Testing (UAT)

Build and release value.

| Role | Responsibilities |
| :---- | :---- |
| PM | Clarify requirements |
| PD | Design support, UX validation, review implementation quality |
| EM | Sprint execution, delivery management, engineering quality, release coordination, stakeholder communication, scope management |

### Outcome

| Decision | Next Stage |
| :---- | :---- |
| Successfully Delivered | Value Assessment |
| On-Hold | On-Hold |
| Delivery Stopped | Rejected  |

### Deliverables

### **Engineering Deliverables**

* Software Release  
* Hardware Release  
* Mechanical Release  
* BOM  
* Certifications  
* Deployment Packages

  ### **Business Deliverables**

* Release Notes  
* Launch Materials  
* Datasheets  
* Documentation  
* Installation Guides  
* User Manuals

### Jira Artifact

* Stories moved to Done

* Bugs resolved

* Release Version created

### **Stage In-Charge:**

| Area | Accountable and responsible |
| :---- | :---- |
| Engineering deliverables | EM |
| Business deliverables | PM |

# Stage 5: Value Assessment

## Purpose

Measure whether the delivered solution achieved expected business and customer outcomes.

### Inputs

| Input |
| :---- |
| PRD Success Metrics Activities: |
| Product Analytics  |
| User Feedback |
| Support Data |

Adoption Analysis

Engagement Measurement

Revenue Impact Review

Customer Feedback Collection

Outcome Validation

Validate outcomes against expected results.

| Role | Responsibilities |
| :---- | :---- |
| PM | KPI analysis, business impact assessment, customer feedback analysis |
| PD | User adoption review, usability validation, behavioral insights |
| EM | System performance review, operational metrics analysis |

## **Stage Outcome**

| Decision | Next Stage |
| :---- | :---- |
| Objectives Achieved | Done |
| Additional Opportunity Identified | Discovery |
| On-Hold | On-Hold |
| No Further Investment Justified | Rejected |

### Deliverables

* Impact Assessment Report

* KPI Dashboard

* Retrospective Findings

### Jira Artifact

* Updated JPD Idea

* Linked Impact Report

### **Stage In-Charge:**

Product Trio

# Stage 6: Done

## Purpose

Formally close the idea after successful delivery and validation of outcomes.

## **Inputs**

* Completed Value Assessment  
* Objectives Achieved  
* Completed Documentation

## **Activities**

* Archive documentation  
* Update roadmap records  
* Capture lessons learned  
* Close idea

Capture learnings and formally close the initiative.

| Role | Responsibilities |
| :---- | :---- |
| PM | Document outcomes and lessons learned |
| PD | Capture design learnings and customer insights |
| EM | Capture technical learnings and operational findings |

### Outcome

Initiative fully completed and documented.

### Deliverables

* Lessons Learned

* Archived Knowledge Base

* Final Closure

### Jira Artifact

* Idea Status \= Done

* All linked work items closed

### **Stage In-Charge:**

Product Trio

# **Stage 7: Rejected**

## **Purpose**

Formally record ideas that will not proceed further.

Rejected ideas remain valuable organizational knowledge and should be retained for future reference.

## **Common Reasons**

* Insufficient customer value  
* Insufficient business value  
* Technical infeasibility  
* Strategic misalignment  
* Regulatory constraints  
* Funding constraints  
* Market conditions changed

## **Activities**

* Document rejection rationale  
* Capture supporting evidence  
* Archive related artifacts  
* Update idea status

## **Deliverables**

* Rejection Record  
* Archived Documentation

## **Jira Artifact**

Idea Status \= Rejected

## **Stage In-Charge**

Product Trio

# **Stage 8 – On-Hold**

## **Purpose**

Temporarily pause an idea without rejecting it.

The idea may resume later from the same lifecycle stage where it was paused.

## **Common Reasons**

| Category | Examples |
| ----- | ----- |
| Strategic | Business priority changed |
| Resource | Team capacity unavailable |
| Customer | Awaiting customer feedback |
| Technical | Dependency unavailable |
| Regulatory | Certification pending |
| Commercial | Budget approval pending |
| Manufacturing | Component shortages |
| Market | Timing no longer appropriate |

## **Activities**

* Document hold reason  
* Define unblock criteria  
* Record review date  
* Notify stakeholders  
* Preserve all related artifacts

## **Outcome**

| Decision | Next Stage |
| ----- | ----- |
| Resume | Return to originating stage |
| Continue Hold | Remain On-Hold |
| Cancel | Rejected |

## **Deliverables**

* Hold Record  
* Hold Rationale  
* Review Date  
* Resume Criteria

## **Jira Artifact**

```
Idea Status = On-Hold
```

## **Stage In-Charge**

Owner of originating stage.

| Original Stage | Owner |
| ----- | ----- |
| Parking Lot | PM |
| Discovery | Product Trio |
| Ready for Delivery | Product Trio |
| Delivery | PM \+ EM |
| Value Assessment | Product Trio |

# **Effort Scoring Guidance**

| Score | Effort | T-Shirt Size | Typical Duration (Mandays) |
| ----- | ----- | ----- | ----- |
| 1 | Very Low | XS | 1-3  |
| 2 | Low | S | 4-10  |
| 3 | Medium | M | 11-50  |
| 4 | High | L | 51-100  |
| 5 | Significant | XL | 101-300  |
| 6 | Extreme | EXT | 300+ |

# **3\. Idea Prioritization Framework**

## **Enhanced RICE Model**

During Parking Lot and Discovery stages, ideas should be evaluated using an expanded scoring model.

## **Reach**

### **Definition**

How many users, customers, or systems will be affected during a defined period?

### **Scoring Guidance**

| Score | Reach |
| :---: | ----- |
| 1 | Very limited users |
| 2 | Single customer or niche segment |
| 3 | Multiple customers |
| 4 | Large customer segment |
| 5 | Majority of target market |

## **Impact**

### **Definition**

Expected improvement delivered to customers or business objectives.

### **Scoring Guidance**

| Score | Impact |
| :---- | :---- |
| 1 | Minimal improvement |
| 2 | Low improvement |
| 3 | Moderate improvement |
| 4 | High improvement |
| 5 | Transformational improvement |

## **Confidence**

### **Definition**

How confident are we in our assumptions and supporting evidence?

### **Inputs**

* Customer interviews  
* Analytics  
* Market research  
* Technical validation

### **Scoring Guidance**

| Score | Confidence |
| :---- | :---- |
| 1 | Assumption only |
| 2 | Limited evidence |
| 3 | Some evidence |
| 4 | Strong evidence |
| 5 | Validated evidence |

## **Effort**

### **Definition**

Estimated implementation effort across Product, Design, and Engineering.

### **Scoring Guidance**

| Score | Effort | T-shirt size (Range) |
| :---- | :---- | :---- |
| 1 | Very low effort |  |
| 2 | Small effort |  |
| 3 | Medium effort |  |
| 4 | Large effort |  |
| 5 | Significant initiative |  |

## **Revenue (Additional Business Attribute)**

### **Definition**

Expected revenue contribution or commercial opportunity.

### **Considerations**

* Direct revenue  
* Upsell potential  
* New market access  
* Retention impact  
* Contract wins

### **Scoring Guidance**

| Score | Revenue Potential |
| :---- | :---- |
| 1 | Negligible |
| 2 | Low |
| 3 | Moderate |
| 4 | Significant |
| 5 | Strategic Revenue Driver |

## **Risk (Additional Business Attribute)**

### **Definition**

Business risk if the idea is not implemented.

### **Considerations**

* Customer churn  
* Competitive disadvantage  
* Security concerns  
* Compliance exposure  
* Operational impact (supply chain / internal risk)

### **Scoring Guidance**

| Score | Risk Exposure |
| :---- | :---- |
| 1 | Minimal |
| 2 | Low |
| 3 | Moderate |
| 4 | High |
| 5 | Critical |

## **Recommended Prioritization Formula**

```
Priority Score =
(Reach × Impact × Confidence × Revenue × Risk)
÷ Effort
```

Higher scores indicate stronger prioritization candidates.

**Note:** Revenue Potential and Risk Exposure are organizational extensions to the original RICE framework and are included to support business-oriented prioritization decisions. 

# 

# 4\. Lifecycle Deliverables Summary

| Stage | Primary Deliverable |
| :---- | :---- |
| Parking Lot | Idea Record |
| Discovery | Discovery Record \+ PRD (if Accepted) |
| Ready for Delivery | Epics \+ User Stories |
| Delivery | Released Solution |
| Value Assessment | Assessment Report \+ KPI Dashboard |
| Done | Archived Knowledge & Lessons Learned |
| Rejected | Rejection Record |
| On-Hold | Hold Record |

# **RACI Matrix**

(R \= Responsible, A \= Accountable, C \= Consulted, I \= Informed)

| Activity | PM | PD | EM | Stakeholders |
| :---- | :---- | :---- | :---- | :---- |
| Idea Intake | A | I | I | R |
| Discovery | A | R | R | C |
| Prioritization | A | C | C | C |
| PRD Review & Alignment | A | C | C | I |
| Ready for Delivery | A | C | R | I |
| Delivery | C | C | A | I |
| Value Assessment | A | R | R | C |
| Closure | A | C | C | I |

**REFERENCES:**

The closest official reference is Atlassian's Jira Product Discovery workflow:

[Atlassian Jira Product Discovery – Delivery Overview](https://www.atlassian.com/hu/software/jira/product-discovery/guides/delivery/overview?utm_source=chatgpt.com)

Atlassian explicitly describes:

> Parking Lot → Discovery → Ready for Delivery → Delivery

and explains how ideas move from uncertain ideas through validation into execution.

### **Atlassian – Product Discovery:** [Atlassian Product Discovery Guide](https://www.atlassian.com/agile/product-management/discovery?utm_source=chatgpt.com)

Supports:

* Idea collection,   
* Discovery  
* Validation  
* Prioritization  
* Delivery linkage  
* Outcome measurement mindset

### **Jira Product Discovery Ideas:** [Atlassian Ideas in Jira Product Discovery](https://www.atlassian.com/software/jira/product-discovery/guides/ideas/overview?utm_source=chatgpt.com)

### **Appendix A – Industry References**

| Topic | Reference |
| ----- | ----- |
| Jira Product Discovery Workflow | [Atlassian Jira Product Discovery Delivery Overview](https://www.atlassian.com/hu/software/jira/product-discovery/guides/delivery/overview?utm_source=chatgpt.com) |
| Product Discovery Practices | [Atlassian Product Discovery Guide](https://www.atlassian.com/agile/product-management/discovery?utm_source=chatgpt.com) |
| Idea Management | [Atlassian JPD Ideas Guide](https://www.atlassian.com/software/jira/product-discovery/guides/ideas/overview?utm_source=chatgpt.com) |
| Product Operating Model | [SVPG Product Operating Model](https://www.svpg.com/product-operating-model/?utm_source=chatgpt.com) |
| Product Trio Model | [SVPG Product Operating Model](https://www.svpg.com/product-operating-model/?utm_source=chatgpt.com) |
| Discovery vs Delivery | [SVPG Discovery vs Delivery](https://www.svpg.com/discovery-vs-delivery/?utm_source=chatgpt.com) |
| RICE Prioritization | [Intercom RICE Framework](https://www.intercom.com/resources/rice-simple-prioritization-for-product-managers?utm_source=chatgpt.com) |
| Agile Effort Estimation | [Atlassian Agile Estimation Guide](https://www.atlassian.com/agile/project-management/estimation?utm_source=chatgpt.com) |

Additional links:

* [SVPG (Silicon Valley Product Group)](https://www.svpg.com?utm_source=chatgpt.com)  
* [SVPG – Product vs Feature Teams](https://www.svpg.com/product-vs-feature-teams/?utm_source=chatgpt.com)  
* [Continuous Discovery Habits (Teresa Torres)](https://www.producttalk.org?utm_source=chatgpt.com)  
* [Atlassian Jira Product Discovery](https://www.atlassian.com/software/jira/product-discovery?utm_source=chatgpt.com)

  
