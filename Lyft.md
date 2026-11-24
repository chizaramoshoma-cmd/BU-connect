# PRODUCT REQUIREMENTS DOCUMENT
## [lyft] babcock keke ride sharing & dispatch app
**Version 1.0 | 23 November 2026**

| Metadata | Details |
| :--- | :--- |
| **Product Owner / Author** | BU-COS209 Group 3, 200-level Software Engineering C |
| **Document Status** | Draft Document — for review |
| **Institution** | Babcock University |
| **Course / Supervisor** | Mr. Samuel |

---

## 1. Document Overview
This Document (PRD) defines the product goals, user roles, requirements, workflows, business rules, constraints, and acceptance criteria for a mobile-friendly web application that connects Babcock University students with campus keke drivers. It is intended to guide design, development, testing, and the pilot release.

### 1.1 Purpose
Students at Babcock University depend on kekes to move around campus. Today a student stands at the roadside and waits for one to pass. Nothing tells the student when a keke will come, who else is going the same way, or what the ride will cost.

The purpose of this product is to replace informal, chance-based keke pickup with a request-and-dispatch process that helps students obtain rides at predictable per-seat fares and enables drivers to view and serve passenger demand across campus.

### 1.2 Product Summary
The application allows students to request rides between predefined campus locations. The system can group compatible requests—up to three passengers—into a ride, present grouped requests to drivers, and provide ride-status updates. Administrators manage locations, fare zones, driver records, and operational reporting.

### 1.3 Product Vision
Make campus keke transportation more predictable, accessible, transparent, and efficient for students and drivers.

---

## 2. Problem Statement
Campus keke transportation currently relies on roadside waiting, driver discretion, and fare negotiation. Students may wait without knowing when transport will arrive, may be separated from peers travelling in similar directions, may struggle to access distant or less frequently served locations, and may face inconsistent or inflated fares when travelling alone. Drivers, in turn, may operate with empty seats and have limited visibility into demand.

* Long and uncertain waiting times, often outdoors.
* Compatible passengers may not be grouped into the same ride.
* Distant or low-demand campus destinations may be underserved.
* Keke coverage may be concentrated around busy locations.
* Passengers may be asked to pay for seats they do not occupy.
* Drivers have limited information about pending demand.

Students bear the cost of all. Drivers lose too: they drive with empty seats and cannot see where demand is. A solution is needed because the problem repeats every day and has no workaround for students.

---

## 3. Product Goals and Objectives
* Enable a student to submit a ride request in under one minute under normal operating conditions.
* Display a fare per seat before a student confirms a request.
* Match compatible requests by pickup area and direction within a configurable matching window.
* Limit a grouped ride to a maximum of three passengers, consistent with the stated vehicle capacity assumption.
* Make pending requests—including requests from distant locations—visible to participating drivers.
* Provide administrative control over campus locations, fare zones, drivers, and reporting.
* Measure waiting time, request acceptance, occupancy, fare compliance, and pilot-user satisfaction.

---

## 4. Target Users and Stakeholders

| User / Stakeholder | Needs / Responsibilities |
| :--- | :--- |
| **Student / Rider** | Register or sign in, select pickup and destination, see per-seat fare, request a ride, receive status and driver details. |
| **Keke Driver** | View pending/grouped requests, assess trip details, accept rides, and mark rides completed. |
| **Administrator / Transport Office** | Manage location lists, zones and fares, driver records, monitor demand and waiting-time indicators, and review reports. |
| **Project Developer** | Design, implement, test, document, and deploy the pilot application. |
| **Supervisor** | Review project progress and provide guidance/approval. |
| **Pilot Participants** | Use the pilot, report issues, and provide feedback. |

---

## 5. Scope

### 5.1 In Scope — MVP
* Mobile-friendly web application for student and driver workflows.
* Student sign-up/sign-in (authentication approach to be finalized).
* Pickup and destination selection from predefined campus locations.
* Fare display before confirmation; fares configured per seat and route zone.
* Ride request creation and status updates.
* Matching of compatible requests by pickup area and direction within a configurable time window (initial proposed window: five minutes).
* Grouping of up to three passengers per ride.
* Driver dashboard/list of pending and grouped rides, including a visual priority flag for requests waiting beyond a configured threshold or from designated distant locations.
* Driver acceptance and completion status.
* Admin panel for managing locations, zones, fares, drivers, and viewing request/waiting-time reports.
* Pilot testing, feedback collection, and bug fixes.

### 5.2 Out of Scope — Initial Release
* Live GPS tracking or GPS hardware integration.
* Automatic GPS-based pickup detection; locations will be selected from a predefined list.
* Native Android/iOS applications (MVP is a web app).
* Online payment processing unless separately approved and specified.
* Dynamic pricing or driver-negotiated fares.
* Expansion beyond Babcock University campus.
* Advanced route optimization beyond the initial matching rules.

---

## 6. User Journeys and Workflows

### 6.1 Student Ride Request
1. Student signs in.
2. Student selects a pickup location and destination from the campus location list.
3. System calculates and displays the applicable per-seat fare.
4. Student confirms and submits the request.
5. System checks for compatible pending requests within the matching window.
6. Compatible requests are grouped into a ride, up to the passenger limit; otherwise the request remains pending.
7. A driver accepts the ride.
8. Student receives ride status and driver identification details, including driver name and keke number.
9. Driver marks the ride as completed.

### 6.2 Driver Workflow
1. Driver signs in to the driver interface.
2. Driver views pending or grouped requests and relevant pickup/destination details.
3. Requests with longer waits or designated distant locations are visibly flagged.
4. Driver accepts a ride.
5. Driver completes the ride and updates the ride status in the system.

### 6.3 Administrator Workflow
1. Admin signs in to the administration panel.
2. Admin maintains campus locations, zones, per-seat fares, and driver records.
3. Admin monitors ride requests, demand by location, and waiting-time indicators.
4. Admin reviews operational reports and uses insights to assess coverage and fare settings.

---

## 7. Functional Requirements

| ID | Requirement |
| :--- | :--- |
| **FR-1** | The system shall provide an authentication flow for student, driver, and admin roles. |
| **FR-2** | The system shall allow students to select pickup and destination from a predefined campus-location list. |
| **FR-3** | The system shall determine and display the applicable per-seat fare before request confirmation. |
| **FR-4** | The system shall create and store student ride requests. |
| **FR-5** | The system shall identify compatible requests using pickup area and direction, within a configurable matching window; initial proposal is five minutes. |
| **FR-6** | The system shall group compatible requests into a ride with a maximum of three passengers. |
| **FR-7** | The system shall display pending/grouped ride requests to eligible drivers. |
| **FR-8** | The system shall flag requests that meet a configured waiting-time or distant-location priority condition. |
| **FR-9** | The system shall allow a driver to accept an available ride. |
| **FR-10** | The system shall notify the student of ride status and driver details, including name and keke number, after acceptance. |
| **FR-11** | The system shall allow the driver to mark an accepted ride as completed. |
| **FR-12** | The admin shall be able to create, update, and deactivate campus locations and zones. |
| **FR-13** | The admin shall be able to set and update per-seat fares by zone or route. |
| **FR-14** | The admin shall be able to manage driver records and keke vehicle details. |
| **FR-15** | The admin shall be able to view request counts and waiting-time indicators by location. |
| **FR-16** | The system shall maintain ride and passenger records for reporting and review. |

---

## 8. Business Rules
* Fares are calculated and charged per seat; a rider is not charged for unoccupied seats.
* Fare values are determined by the administrator and are displayed before booking confirmation.
* Drivers may not set or negotiate fares within the app.
* A grouped ride may contain no more than three passengers, subject to confirmation of the campus vehicle-capacity rule.
* Matching initially considers pickup area and compatible direction, with a proposed five-minute matching window.
* Requests for distant or low-demand locations may receive a priority flag based on administrator-configured rules.
* Campus pickup and destination locations are selected from a controlled list in the MVP.
* A ride must be accepted by a driver before driver details/status are presented as confirmed to the student (workflow details to be validated).

---

## 9. Non-Functional Requirements

| ID | Requirement |
| :--- | :--- |
| **NFR-1 Usability** | The web app should be mobile-friendly and usable on common smartphone screen sizes. |
| **NFR-2 Performance** | Common actions such as opening request screens and submitting requests should respond promptly under pilot load; quantitative targets require confirmation. |
| **NFR-3 Availability** | The pilot should be available during agreed campus operating periods; service-level targets are TBD. |
| **NFR-4 Security** | Role-based access must restrict student, driver, and admin functions. Authentication and authorization controls must be implemented. |
| **NFR-5 Privacy** | Collect only information needed for ride coordination and administration; access to personal and ride data should be restricted. |
| **NFR-6 Reliability** | Ride-request and ride-status changes should be persisted and handled consistently to avoid duplicate or conflicting assignments. |
| **NFR-7 Maintainability** | The application should use modular components and documented configuration for locations, zones, fares, and matching rules. |
| **NFR-8 Compatibility** | The MVP should work on modern mobile and desktop web browsers. |
| **NFR-9 Accessibility** | Use clear text, adequate contrast, and understandable controls; further accessibility standards and testing are to be defined. |

---

## 10. Data Requirements / Core Entities

| Entity | Key Information (conceptual) |
| :--- | :--- |
| **Students** | Student profile and account details required for authentication and ride requests. |
| **Drivers** | Driver identity/contact details and account status. |
| **Keke Vehicles** | Vehicle/registration or campus keke number associated with a driver. |
| **Locations** | Named campus pickup and destination locations. |
| **Zones and Fares** | Zone/route relationships and configured per-seat fare values. |
| **Ride Requests** | Requesting student, pickup, destination, creation time, request status. |
| **Rides** | Grouped trip, driver, ride status, pickup/destination details and timestamps. |
| **Ride Passengers** | Association between individual requests/passengers and a grouped ride. |

---

## 11. Acceptance Criteria

| Feature | Acceptance Criteria |
| :--- | :--- |
| **Ride request** | A signed-in student can select valid pickup and destination locations, see a fare, and submit a request. |
| **Fare transparency** | The fare is visible before confirmation and reflects the configured fare for that route/zone. |
| **Matching** | Compatible pending requests can be grouped according to the configured matching window and matching rule, without exceeding capacity. |
| **Driver view** | A driver can see available requests and priority indicators. |
| **Ride acceptance** | A driver can accept an available ride, and the system updates the ride state. |
| **Student notification** | The student is shown or notified of accepted ride status and driver name/keke number. |
| **Ride completion** | The driver can mark a ride completed and the ride status is saved. |
| **Admin controls** | An admin can manage locations, fares, drivers, and view location-based request/wait indicators. |
| **Pilot** | Pilot feedback and defects are recorded and reviewed before wider release. |

---

## 12. Metrics and Success Measures
Baseline values will be collected during the first project week or pilot preparation to establish a benchmark for evaluating the app's performance.

* **Average student waiting time:** Reduction of 30% against the baseline.
* **Ride occupancy:** At least 70% of eligible grouped rides should carry two or three riders.
* **Distant-location requests:** At least 80% of requests from designated distant locations should receive driver acceptance within 10 minutes.
* **Fare compliance:** 100% fare compliance, ensuring no rider is charged above the configured fare.
* **User satisfaction:** At least 75% of pilot users report willingness to continue using the app.
* **Operational usage:** Track the total number of ride requests, completed rides, cancellations, and driver acceptance rates throughout the pilot to evaluate system adoption and operational performance.

---

## 13. Implementation Plan

| Phase | Activities | Deliverable |
| :--- | :--- | :--- |
| **1 — Requirements** | Interview students and drivers; map locations/zones; validate fare rules. | Requirements and validated location/fare list. |
| **2 — Design** | Database design, screen wireframes, matching-rule design. | Approved design and matching specification. |
| **3 — Development** | Implement student, driver, and admin features. | Working core application. |
| **4 — Testing & Pilot** | Test with sample data; conduct one-week pilot; collect and resolve defects. | Pilot report and issue log. |
| **5 — Launch & Handover** | Final fixes, user guide, release, handover to designated admin. | Release and user guide. |

---

## 14. Proposed Timeline

| Week | Activities | Milestone |
| :--- | :--- | :--- |
| **1** | Interviews, location/zone list, fare agreement | Requirements approved |
| **2** | Database design, wireframes, matching rule | Design approved |
| **3** | Student and driver workflows | Request and acceptance flow working |
| **4** | Admin panel and matching integration | System works with test data |
| **5** | Pilot and bug fixing | Pilot report |
| **6** | Final fixes, user guide, release and presentation | System released |

**Start date:** 25/11/2026. **Completion date:** [To be confirmed].

---

## 15. Resources, Budget, and Dependencies

| Resource | Description / Status |
| :--- | :--- |
| **Development** | Student project developer time; estimated ₦0. |
| **Hardware** | Existing laptop; estimated ₦0. |
| **Software** | Code editor, database, framework and other open-source tools; estimated ₦0. |
| **Hosting** | Pilot hosting cost: [To be confirmed]. |
| **Domain** | Optional domain: [To be confirmed]. |
| **Notifications** | Messaging/SMS service costs, if required: [To be confirmed]. |
| **Internet** | Mobile data for development and testing: [To be confirmed]. |
| **Printing** | Posters and promotional materials: [To be confirmed]. |
| **Pilot support** | Participant support/refreshments, if applicable: [To be confirmed]. |

**Dependencies:** confirmation of campus locations and fare structure; driver participation and registration; access to pilot students; approval from the relevant transport or administrative office; hosting and notification decisions.

---

## 16. Risks and Mitigation

| Risk | Mitigation / Action |
| :--- | :--- |
| **Drivers may not adopt the system.** | Engage drivers early, explain the workflow, and conduct onboarding before pilot. |
| **Insufficient requests for matching.** | Pilot in selected locations and assess whether the matching window or grouping rules need adjustment. |
| **Unvalidated fare zones or amounts.** | Confirm the fare model with the designated campus authority before testing fares. |
| **Poor coverage of distant locations.** | Use request-volume and waiting-time reports; prioritize requests based on agreed rules. |
| **Connectivity issues.** | Test on mobile data and provide clear request/ride-status feedback. |
| **Privacy or unauthorized access.** | Implement role-based access, secure authentication, and limit data access. |
| **Scope expansion or timeline slippage.** | Treat GPS, payment integration, native apps, and advanced optimization as later-phase items unless formally approved. |

---

## 17. Open Questions / Decisions Required
* Confirm the approving transport office or campus stakeholder.
* Confirm the list of campus locations and zone definitions.
* Confirm fare amounts and whether fare mapping is by zone pair or route.
* Validate passenger capacity and matching logic with campus drivers/transport authority.
* Determine notification method (in-app, SMS, or other).
* Define cancellation, no-show, and driver-rejection rules.
* Define account verification requirements for students and drivers.
* Confirm privacy, retention, reporting, and operational access rules.
* Confirm hosting, deployment, and pilot operating hours.
* Set numeric performance and success targets, pilot sample size, and launch dates.

---

## 18. Approval

| Stakeholder | Name | Signature / Date |
| :--- | :--- | :--- |
| **Project Author** | GROUP 5, Black Ops | 23/11/2026 |
| **Supervisor** | Mr. Samuel | 23/11/2026 |
| **Approving Campus / Transport Office** | [To be confirmed] | |