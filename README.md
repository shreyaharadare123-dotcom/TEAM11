# TEAM11# College Event Participant Registration System

A complete design specification for a **College Event Participant Registration System**, including data models (ER diagram), operational flowcharts, and core algorithms[span_3](start_span)[span_3](end_span)[span_4](start_span)[span_4](end_span)[span_5](start_span)[span_5](end_span).

---

## 📌 Project Overview

The College Event Participant Registration System simplifies event management by capturing participant info, handling real-time capacity checks, and managing waitlists when events reach full capacity[span_6](start_span)[span_6](end_span)[span_7](start_span)[span_7](end_span)[span_8](start_span)[span_8](end_span).

---

## 🗃️ Database Structure (ER Diagram Specs)

The system relies on a **Many-to-Many** relationship between `Participant` and `Event`, resolved via a `Registration` junction entity[span_9](start_span)[span_9](end_span).

### Entities & Attributes

* **Participant**[span_10](start_span)[span_10](end_span)
  * `Participant_ID` (Primary Key)[span_11](start_span)[span_11](end_span)
  * `Name`[span_12](start_span)[span_12](end_span)
  * `Contact`[span_13](start_span)[span_13](end_span)

* **Event**[span_14](start_span)[span_14](end_span)
  * `Event_ID` (Primary Key)[span_15](start_span)[span_15](end_span)
  * `Event_Name`[span_16](start_span)[span_16](end_span)
  * `Date`[span_17](start_span)[span_17](end_span)
  * `Capacity`[span_18](start_span)[span_18](end_span)

* **Registration** *(Linking Entity)*[span_19](start_span)[span_19](end_span)
  * `Registration_ID` (Primary Key)[span_20](start_span)[span_20](end_span)
  * `Participant_ID` (Foreign Key)[span_21](start_span)[span_21](end_span)
  * `Event_ID` (Foreign Key)[span_22](start_span)[span_22](end_span)
  * `Status` (`Registered` / `Waitlisted`)[span_23](start_span)[span_23](end_span)

### Relationships
* One **Participant** can register for multiple **Events**[span_24](start_span)[span_24](end_span).
* One **Event** can have multiple **Participants**[span_25](start_span)[span_25](end_span).
* **Registration** connects both entities and tracks dynamic status[span_26](start_span)[span_26](end_span).

---

## ⚙️ Core Registration Algorithm

1. **Start**[span_27](start_span)[span_27](end_span)
2. **Input** participant details (`Name`, `ID`, `Contact`)[span_28](start_span)[span_28](end_span).
3. **Display** list of available events[span_29](start_span)[span_29](end_span).
4. **Participant** selects an event[span_30](start_span)[span_30](end_span).
5. **Check** event capacity[span_31](start_span)[span_31](end_span):
   - **If** `Capacity > 0`:
     - Register participant[span_32](start_span)[span_32](end_span)
     - Decrease available capacity by 1[span_33](start_span)[span_33](end_span)
     - Set `Status = "Registered"`[span_34](start_span)[span_34](end_span)
   - **Else**:
     - Set `Status = "Waitlisted"`[span_35](start_span)[span_35](end_span)
6. **Store** registration details in the database[span_36](start_span)[span_36](end_span).
7. **Display** participant status (`Registered` / `Waitlisted`)[span_37](start_span)[span_37](end_span).
8. **End**[span_38](start_span)[span_38](end_span)

---

## 🔄 System Flowchart

```text
       ( Start )[span_39](start_span)[span_39](end_span)
           │
           ▼
[/ Input Participant Details /][span_40](start_span)[span_40](end_span)
           │
           ▼
[/ Display Available Events /][span_41](start_span)[span_41](end_span)
           │
           ▼
 [/ Select Event /][span_42](start_span)[span_42](end_span)
           │
           ▼
   < Is Capacity Available? >[span_43](start_span)[span_43](end_span)
     /                  \
   (Yes)                (No)
    │                    │
    ▼                    ▼
[ Confirm        [ Show "Event Full" ][span_44](start_span)[span_44](end_span)
 Registration ]          │
    │                    ▼
    │            [ Set Status = "Waitlisted" ][span_45](start_span)[span_45](end_span)[span_46](start_span)[span_46](end_span)
    │                    │
    └──────────┬─────────┘
               │
               ▼
   [ Store Registration Details ][span_47](start_span)[span_47](end_span)
               │
               ▼
   [/ Display Participant Status /][span_48](start_span)[span_48](end_span)
               │
               ▼
          ( End )[span_49](start_span)[span_49](end_span)
