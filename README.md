# GetInvolvedUC / 25Live Redesign

## Project Overview
Event planning at the University of Cincinnati is split across two separate platforms. 25Live is used for booking rooms, and GetInvolvedUC is used for posting and managing events. This divided workflow creates significant inefficiencies for students and student organizations.

25Live presents major usability challenges. Students find it unintuitive, slow, and the way status is displayed can be unclear. It is also difficult to view current bookings or understand what events are already occupying a space. On top of that, many of the questions asked in 25Live repeat again in GetInvolvedUC, making the process feel redundant and time-consuming.

While 25Live contains more detailed room information and comprehensive scheduling tools, GetInvolvedUC is cleaner and more familiar to students. This project aims to bridge the gap by integrating 25Live’s core room-booking functionality directly into the GetInvolvedUC interface, creating a unified system where students can book a space and upload event information in a single, streamlined workflow.

### Link to site

[New design here!](https://improved-getinvolveduc.netlify.app/)

### Demo video link

[Demo link](https://drive.google.com/file/d/1mrIPGzpF-oxufHXFVvz0KEkt87hqx3FU/view?usp=sharing)

### Key Features
- Integrated Room Booking & Event Creation
- Real-Time Room Availability & Visual Calendar
- Enhanced Organization & Event Search

## Design Process

### **Research / Surveying**

We began by gathering general insights from students who use the University of Cincinnati's **25Live** (room booking) and **GetInvolvedUC** (student organizations and events). The goal was to understand how people currently use the two systems, where pain points surface, and what expectations or missing functionality matter most.

#### **Questions Asked**

-   What have you used 25Live and/or GetInvolvedUC for in the past?
    
-   Rate your experience with each system (ease of use, ability to find features, difficulty locating rooms/events).
    
-   What current struggles do you experience with the systems?
    
-   What functionality do you feel is missing that would improve your experience?
    

### **Findings**

-   Students commonly use the systems for finding study rooms, organizing meetings, or browsing campus events.
    
-   Many described the interfaces as functional but unintuitive, especially when trying to locate available rooms or filter events.
    
-   Room availability was a major frustration—users often felt uncertain whether a space was actually open.
    
-   GetInvolvedUC generally felt more modern, but its event filters and forms were described as lengthy or overwhelming.
    
-   Several users mentioned wishing both systems were connected, since event planning often requires switching back and forth.
    
-   Students frequently cited slow loading, unclear labels, and too many clicks as barriers to quick use.
    

### **Interviews**

We conducted a set of informal interviews with students who regularly run meetings, host events, or need rooms for student organizations.

#### **Questions Asked**

-   How do you typically use 25Live and/or GetInvolvedUC in your role?
    
-   Which parts of the process feel most frustrating or time-consuming?
    
-   Which platform feels easier to use, and why?
    
-   What would make planning or reserving spaces smoother?
    
-   Are there any ideas from other systems you wish UC used?
    

#### **Findings**

-   Interviewees described event planning as split between two different tools, making the workflow feel scattered.
    
-   25Live was frequently described as outdated and difficult to navigate, especially for first-time users.
    
-   The approval process felt slow or unclear; users often didn’t know when something was “truly” approved.
    
-   GetInvolvedUC was viewed as more approachable, but the event creation process was said to be repetitive.
    
-   Participants wished information entered in one system could automatically populate in the other.
    
-   Many referenced other tools they use (Google Calendar, Outlook, EMS) and liked features such as clear visual calendars, drag-and-drop scheduling, and quicker confirmations.

### **Heuristic Evaluation Summary**

Using Nielsen’s usability heuristics, we found recurring themes across both systems:

-   **Low visibility of system status:** Slow responses with minimal feedback.
    
-   **Non-student-friendly language:** 25Live uses facility management terms unfamiliar to most users.
    
-   **Limited control and flexibility:** Editing submissions or rebooking recurrent events is harder than it should be.
    
-   **Inconsistencies and clutter:** 25Live pages feel dense and outdated; GetInvolvedUC is cleaner but still crowded in places.
    
-   **Weak error messaging:** Errors often appear without clear explanation or instructions.
    
-   **Minimal in-platform guidance:** Most help exists as external PDFs rather than built-in support.
    
Across all methods, the biggest takeaway was the same: students want a more unified, clearer, and faster way to plan events and reserve spaces, without switching between two separate systems.


### Sketching

![alt text](https://github.com/kellannd/project3-UI/blob/faith/sketches/Screenshot%202025-11-18%20183204.png)
![alt text](https://github.com/kellannd/project3-UI/blob/faith/sketches/Screenshot%202025-11-18%20183235.png)
![alt text](https://github.com/kellannd/project3-UI/blob/faith/sketches/Screenshot%202025-11-18%20183300.png)
![alt text](https://github.com/kellannd/project3-UI/blob/faith/sketches/Screenshot%202025-11-18%20183320.png)
![alt text](https://github.com/kellannd/project3-UI/blob/faith/sketches/Screenshot%202025-11-18%20183327.png)


## Interface Design
![alt text](https://github.com/kellannd/project3-UI/blob/faith/screenshots/added-event-to-calendar.png)
![alt text](https://github.com/kellannd/project3-UI/blob/faith/screenshots/addedlocation-offcampus.png)
![alt text](https://github.com/kellannd/project3-UI/blob/faith/screenshots/addedlocation-oncampus.png)
![alt text](https://github.com/kellannd/project3-UI/blob/faith/screenshots/eventform-club-2.png)
![alt text](https://github.com/kellannd/project3-UI/blob/faith/screenshots/eventform-club.png)
![alt text](https://github.com/kellannd/project3-UI/blob/faith/screenshots/eventform.png)
![alt text](https://github.com/kellannd/project3-UI/blob/faith/screenshots/locationform-offcampus.png)
![alt text](https://github.com/kellannd/project3-UI/blob/faith/screenshots/locationform-oncampus.png)
![alt text](https://github.com/kellannd/project3-UI/blob/faith/screenshots/locationform-online.png)


#### Future Work
Possible next steps include developing a proper database structure to replace the current set of placeholder data. This would allow the system to support real room information, live availability, and persistent event records. Another area of work is creating a mobile-friendly layout and interaction model, since many students access these tools from their phones. Deeper integration with the university’s existing frameworks and APIs is also a major consideration, as this would allow bookings, approvals, and organization data to move between systems without manual input.

Additional possibilities involve expanding the room search and filtering mechanisms to support criteria such as capacity, building, equipment, and scheduling constraints. Improvements to the underlying architecture, such as more consistent data models and clearer interfaces between services, would help reduce redundancy and simplify maintenance. These efforts would move the project toward a more reliable and scalable system that aligns with real campus use cases.






