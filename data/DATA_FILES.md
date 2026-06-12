\# Persistent Storage Files



The system uses binary files for persistent storage.



\## Files



\### admin.dat

Stores administrator credentials.



\### students.dat

Stores student information and enrollments.



\### faculty.dat

Stores faculty information and offered courses.



\## Access Method



Managed using:



\- open()

\- read()

\- write()

\- lseek()



with mutex protection.

