# Modular thinking

_Captured: 2015-12-01 at 14:14 from [jonnorris.work](http://jonnorris.work/modular-thinking/)_

While trying to organise my thoughts about how Studious will work, I've mentally broken the features up into three "modules".

## 1\. Contact module

The first module will be to provide schools simple contact functionality with their parents or students. It's important in this module to separate the contact options for parents and students. For lower age groups (Infant and Primary schools) there would obviously not be much utility in being able to contact students (are 9-year-olds even allowed email address yet?), however as the age of the students increases into Secondary schools and Colleges, contacting students directly would become a useful feature.

Things like homework reminders or school newsletters would need to go directly to students, so having their contact details on file is necessary.

Carry on up the age ladder and parent contact details become redundant. Universities or International schools which cater for over-18s would have the actual student as sole point of contact. Parent details would still be required for emergency contact, although they would not be used in the day-to-day running on the school.

The contact module would have the following functions:

**Data collection**

Once basic contact details are entered into the system (Student name / email address and parent name / email address - whichever is more relevant for the age group concerned) [an email can be sent out](http://studious.im/blog/wireframing-the-enrolment-process/) with a link to a secure form allowing for full details to be collected.

**One-to-one emailing**

One-to-one emailing between teachers and parents / students.

**Whole class emailing**

Bulk emailing to entire classes, be they form groups or subject classes. For example at a Primary School you may want to send a group email to Mrs. Smith's class of 6-year-olds, whereas in a Secondary School you may want to contact one particular Science class in Year 8.

**Whole school emailing**

Same as above but for the whole school.

**Reporting**

All of these functions would have underlying reporting built-in. Things such as open rates, clickthroughs - the exact type of thing you see in email marketing software. However as much more detail is held on file about the person receiving the email, more functionality can be built in. For example after three unsuccessful sends of an important email, a teacher could be prompted to print out the message and give it to the student in question.

## 2\. Timetabling module

Using the details collected with the contact module, plus some information from the school ([see this post](http://studious.im/blog/wireframing-the-school-setup-process/)) this module will automatically generate timetables and intelligently assign pupils to classes.

Although somewhat basic to begin with, this area could be expanded to include things like ability-based timetabling. This would involve additions to the student information to add ability levels for certain subjects.

This area would also need to sport advanced timetabling features that can be turned on and off to cater for individual schools. For example:

  * Variable class length (double periods, for example)
  * Single classroom, multiple subjects (for Primary Schools who have one classroom and one teacher per form group, but different classes throughout the day)
  * Free periods (for Colleges that do not fill student timetables completely)
  * Elective classes (If students are not automatically enrolled in all subjects, per-student subject assignment would be needed. This would also work for International Schools where students only take one or two lessons per day)

This module would also be underpinned by certain basic rules, such as making sure there is an even spread of genders and ethnicities in all classes.

## 3\. Portal

This module would combine the results of the Contact and Timetabling modules into a parent- or student-accessible portal. This would allow access to and exporting of timetables, editing and updating of contact information, plus additional functionality such as booking time off for doctor's appointments and holidays, notifying the school of sickness, and online payment for school dinners or trips.

This would also allow access to any other information the school would like to put online. Uniform or inset day information etc.

This area of the system, in particular, would need to be mobile-compatible. To a certain extent the range of devices used by the schools can be controlled and catered for, however parents will be using anything from desktops to iPhones to access information.

This area could also be expanded into a mobile app in the future. For example, a school-branded app that students can download that shows their timetables, doles out homework reminders, and provides contact information.

## Futureproofing

Taking a modular approach means the addition of extra functionality is simple. For example, a curriculum management module could be added in future once the first three elements are in place. This approach also makes customising deployment for individual schools simpler. One school may just want the Contact module, so that's all they'd pay for ([see my thoughts on pricing here](http://studious.im/blog/thoughts-on-pricing/)), whereas another may want all three modules.

One caveat is that the modules would only be available cumulatively. In order for the Timetabling module to work correctly it requires the data gathered by the Contact module (and the Portal module requires that data from the Contact _and_ Timetabling modules) - a module cannot work without the preceding modules.
