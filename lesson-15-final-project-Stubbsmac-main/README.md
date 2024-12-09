# Create_15_Final Project

## Project Description

For your final project, you have been tasked with developing a database schema and accompanying documentation for a convention planning system. You will be provided the business needs for the database that have been outlined by the rest of the development team. You will not only be challenged with developing a normalized structure, but you must also consider that development that has already been completed for front end of the system.

You get to pick the theme of the conference when entering sample data. Feel free to make the conference about video games, anime, movies, professional development, or whatever piques your interest.

You will only be writing SQL queries for this assignment, so you can use a standard Jupyter Notebook in Azure Data Studio like we have been for the majority of the semester. You will complete this queries in your regular AWS database, not MongoDB or the Docker SQL container. Prefix all of your tables with fp_.

## Project Deliverables

* Completed ERD for database schema (use of Miro is required)
* Jupyter Notebook file containing
  * Scripts to create tables
  * Scripts to add data to tables
  * Scripts creating requested automation, such as stored procedures and triggers
  * Scripts that create views to pull requested data
  * Any other scripting necessary, with texts cells describing your processes.

## Expectations

* You may not use generative AI for any scripting in this assignment. You may however use it to construct your mock data if that would be helpful.
  * If you choose to user generative AI to construct your data, you must include your prompt in a prompts.txt file in your repo, along with what service you used.
  * I strongly recommend that you master your ERD and database structure before attempting to generate data.
* You should have at least 20+ unique attendees and 8+ sessions. Other data needs only to be enough to demonstrate that you met requirements.
* All code should be properly commented and your Jupyter Notebook should have a good mix of text and code cells walking me through your process.
  * You should have a cell at the end of the notebook to drop all database objects you created and essentially reset the project. The goal is that I could click run all cells and instantly recreate your work. 
* All database objects, including views, procedures, and triggers, should have a prefix of fp_ so that they can be identified as final project resources.
* The due date on this project is firm. There will be no allowance for late work. You will be graded based on whatever is checked into your repo as of the due date/time.
* **You must use Miro for your ERD. Failure to do so will result in a 0 for that portion of the project.**
* It will not be enough for your code to execute correctly. You must use best practices and format your code so that it is readable.
* **All notebook cells must show that they have been executed, or they will not be graded.**
* Your database schema should be in BCNF.
* Below each cell, you should have an additional cell demonstrating that you tested your work. For example, below a stored procedure, you should create a new cell and execute the procedure so that I can view the result.

## Important Definitions

* **Session:** A conference event where attendees listen to a presentation hosted by a speaker or set of speakers (panel). A session can have many or one speakers.

* **Attendee:** Someone who attends a conference and sessions.

* **Speaker:** Someone who hosts a session at a conference.

* **Topic:** A general area that a session pertains too. Many sessions can share the same topic.

* **Title:** The title of a session. This is unique to a session and different than a topic.

## System Requirements

The below system requirements will offer you guidance on what data needs to be included in each of your entities, as well as what views you should create. Give your views names that describe what they are pulling, but do not be too verbose.

### Reporting Needs

The below reporting needs are each a view that you will need to create as part of the system development.

* Report detailing all contact information (address, phone, email) for each conference attendee, as well as their registration date, company, job title, and the type of ticket they purchased.

* Simple list that shows how many of each ticket type (General, VIP, and student) were sold.

* Report listing the information for each speaker (all contact information except address), their job title, company, and the name of any sessions they are hosting. If someone is hosting multiple sessions, print them on the report once per session. Also include the description, start/end time, room and topic for the session.

* Report listing the number of attendees that attended each session.

* Report listing feedback (1-5 rating) from each attendee of a session.

* Report that shows the number of attendees by topic. Several sessions may cover the same topic.

* Report that shows the number of attendees in each session, as well as the average attendees across all sessions. (Window query)

* Report showing all relevant information for a session, as well as the percentage of occupancy in the room filled. If the occupancy was 100 and 57 people showed up this would be .57 or 57%.

### Special Reports

The below reports should be stored procedures that are provided a parameter to select data.

* Detailed report listing the individual contact information for each attendee in a session when provided a session id.

* Report showing the total number of attendees that a speaker drew across all of their sessions when provided a speaker id.

* Report that returns relevant information for all related sessions and their speaker(s) when provided a topic id.

### Development Team Restrictions / Needs

The below information is to help guide you in the creation of your database objects. Read the below carefully for important information regarding your database schema.

* The dev team has already built the form to add rooms to the conference software. For each room they plan to collect the room number and capacity. Room numbers use the leading digit to indicate floor. (Room 342 is room 42 on the 3rd floor.)

* The dev team resolved an issue with the session registration form. Prior to the fix only one speaker could be assigned to a session, after the fix multiple speakers can be assigned to the same session to accommodate panels and group presentations.

* For the attendee and speaker registration process, all contact information fields are required. Email addresses must be unique, same thing with phone numbers.

* On the front end, a speaker (or speakers)will fill out a form to submit their session. Please create a stored procedure that accepts parameters to add a new session to the database.

* Include a trigger in the database that will add a new record to an audit table any time there is a change (update, insert, delete) to a session. The dev team wants the old and new data stored in a JSON format.
