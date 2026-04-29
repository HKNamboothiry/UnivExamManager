# University Exams Manager
This software project is mainly concerned with anaging examination lifecycle easily by
1. Distributing students among exam halls
2. Scheduling examination duties to each faculties based on their previous examination duty hours and seniority
3. Generating layouts on how each student should be seated in the given examination hall

## Data Structures
### Examinations List
|Examination Code | Examination Name | Starting Date (Filled automatically after time-table) | Ending Date (Filled automatically after time-table) | Manage Examination (Button) |
|-------|-------|---------|------|-------|
S2UG2026| Second Semester Bachelors Degree Examination 2026 | 29-04-2026 | 13-05-2026 | Manage |

### Examination Time Table
|Date|From (time)| To (time) | Subject Code | Subject Name (Optional)| Program Code | Year of Admission|
|------|--------|-------|---------|----------|-----|---|
23-04-2026|09.00|12.00|PH123|Classical Mechanics| 230  |2026|

### Rooms
|Room Number | Rows | Columns | Students Per bench | Invigilators required |
|-------|-------|---------|---------|----------|
103 | 12 |3 |2|2|

### Student Data
| Candidate Code | Year of Admission (Automatically filled) | Program (Automatically Filled) | Roll Number (Automatically Filled) |
|------|------|------|-----|
23019125007 | 2019 | 230 | 007 |

### Faculty Data
| Faculty Name | Department | Rank (0-4) | Duty Time |
|--------------|------------|------------|-----------|
| Faculty 1    | Physics | 3 (professor)| 3|
| Faculty 2    | Physics | 2 (Associate Professor)| 6|
| Faculty 3    | Physics | 1 (Assistant Professor)|9|
| Faculty 4    | Physics | 0 (Guest Faculty)|3|

## Algorithms
### Algorithm for Faculty Duty Assignment
#### Constraints
1. The number of faculties should meet the requirement of faculties per room.
2. No two faculties from the same department should come together in any rooms.
3. Assignment of faculties should be based on their duty time till the previous examination.
4. Faculties having highest rank should not be given more priority to be assigned as invigilator.
### Description
The requirement of faculty to each room will be identified at first. The faculties will be sorted in the following order of priority:
1. Faculty having least duty time will be given highest priority
2. Within that faculty having lowest rank value will be given more priority

Equal number of faculties will be selected from all departments for the duty. If one more faculty are required (in case of odd number of requirements), 
the faculty having the least duty time and more rank in the entire college will be identified and duty will be assigned to him/her. The process of assigning follows constraint 2 also.

After assignment a report of the following format will be generated:
<College Name as Heading>
<Examination Name as Sub Heading>
| Date | Department | Faculty | Room Number | Programs | 
|-------|---------|----------|----|-------|
|22-10-2025|Physics|Faculty 1| 134|BSc Physics, BSc Chemistry|

### Algorithm for Room allocation
#### Constraints
1. Two students sitting per bench should not be of the same program.
2. Only a maximum of two different program examinations should be conducted per room
3. The arrangement of student should be column wise in the following format
<table>
  <thead>
    <tr>
      <!-- Merges across all 6 sub-columns -->
      <th colspan="6" align="center">Invigilator</th>
    </tr>
    <tr>
      <th colspan="2" align="center">Column 1</th>
      <th colspan="2" align="center">Column 2</th>
      <th colspan="2" align="center">Column 3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>23019125001</td><td>25019125001</td>
      <td>23019125004</td><td>25019125004</td>
      <td>23019125007</td><td>25019125007</td>
    </tr>
    <tr>
      <td>23019125002</td><td>25019125002</td>
      <td>23019125005</td><td>25019125005</td>
      <td>23019125008</td><td>25019125008</td>
    </tr>
    <tr>
      <td>23019125003</td><td>25019125003</td>
      <td>23019125006</td><td>25019125006</td>
      <td>23019125009</td><td>25019125009</td>
    </tr>
  </tbody>
</table>
4. If the total number of students exceed the capacity, assign the remaining students to the adjacent room listed in the table

After allocation is performed, generate the layout (described above) and a report of the following format
<College Name as Heading>
<Name of the Examination>
<Date of Examination>
| Department | Candidate Code Sequence | Room Number | Subject Code and Name |
|---|----|----|----|
|Physics | 23019125001-23019125025|103|PH113-Classical Mechanics|
|Physics | 23019129026-23019125049|102|PH113-Classical Mechanics|
