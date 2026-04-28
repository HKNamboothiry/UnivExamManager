# University Exams Manager
This software project is mainly concerned with anaging examination lifecycle easily by
1. Distributing students among exam halls
2. Scheduling examination duties to each faculties based on their previous examination duty hours and seniority
3. Generating layouts on how each student should be seated in the given examination hall

## Data Structures
### Examination Time Table
|Date|From (time)| To (time) | Subject Code | Subject Name (Optional)| Program | Department | Year of Admission|
|------|--------|-------|---------|----------|--|---|---|
23-04-2026|09.00|12.00|PH123|Classical Mechanics| BSc | Physics |2026|

### Faculty Data
| Faculty Name | Department | Rank (0-4) | Duty Time |
|--------------|------------|------------|-----------|
| Faculty 1    | Physics | 0 (professor)| 3|
| Faculty 2    | Physics | 1 (Associate Professor)| 6|
| Faculty 3    | Physics | 2 (Assistant Professor)|9|
| Faculty 4    | Physics | 3 (Guest Faculty)|3|

## Algorithm for Faculty Duty Assignment
The requirement of faculty to each room will be identified at first. The faculties will be sorted in the following order of priority:
1. Faculty having least duty time will be given highest priority
2. Within that faculty having highest rank value will be given more priority

Equal number of faculties will be selected from all departments for the duty. If one more faculty are required (in case of odd number of requirements), 
the faculty having the least duty time and more rank in the entire college will be identified and duty will be assigned to him/her.

After assignment a report of the following format will be generated:
<College Name as Heading>
<Examination Name as Sub Heading>
| Date | Department | Faculty | Room Number | Programs | 
|-------|---------|----------|----|-------|
|22-10-2025|Physics|Faculty 1| 134|BSc Physics, BSc Chemistry|
