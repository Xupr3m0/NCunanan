# Final  Task Lab 1: MySQL Basics

## ***Create an events table with fields***

- event_id (int, auto-increment, primary key)

- event_name (VARCHAR, up to 255 characters, not null)


![image](https://github.com/user-attachments/assets/834d5694-c0c7-4ff5-94a3-4615124ac72b)

## ***Create an attendees table with fields***

- attendee_id (int, auto-increment, primary key)

- attendee_name (VARCHAR, up to 255 characters, not null)


![image](https://github.com/user-attachments/assets/c0c5e6d7-86b6-4a81-bdf8-3dc1d1d226a9)




## ***Create an event attendees table with fields***

- event_id (int, foreign key to events.event_id)

- attendee_id (int, foreign key to attendees.attendee_id)

- Composite primary key on (event_id, attendee_id)
  

![image](https://github.com/user-attachments/assets/540d9a29-fb9f-40b2-ac72-e613874defab)



## ***Create an event sponsors table with fields***

- sponsor_id (int, auto-increment, primary key)

- event_id (int, foreign key to events.event_id)

- sponsor_name (VARCHAR, up to 255 characters, not null)


 ![image](https://github.com/user-attachments/assets/c4a40071-f3d8-4489-87b6-5b50c1a735a3)

 ## ***EER DIAGRAM***
![image](https://github.com/user-attachments/assets/2450cf4a-028e-4fd0-8433-0e076af59120)

