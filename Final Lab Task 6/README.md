# Final Lab Task 6: Mongo DB Practice


#  Task Step-by-Step

## ***Create database***
- Connect to a running mongo instance, use a database named `mongo_practice`.

- use *mongo_practice*

![image](https://github.com/user-attachments/assets/f6eecad4-bc48-4666-8eb2-9f40683565f9)

## ***Insert Documents***

![image](https://github.com/user-attachments/assets/b1b628fc-e4f4-44fd-8b71-0f542e383180)

![image](https://github.com/user-attachments/assets/92911b5f-0bd6-4395-a687-92f0b50c5bc1)


![image](https://github.com/user-attachments/assets/e6584120-10e6-4fff-8873-26a2667806e7)


![image](https://github.com/user-attachments/assets/4d7ec667-803e-4801-b091-a16f756e20c6)


![image](https://github.com/user-attachments/assets/06ad5489-b986-4dbd-b555-5eedae7bd34f)


![image](https://github.com/user-attachments/assets/6ed6625b-5709-4f91-ac3c-53c56c575ef1)


![image](https://github.com/user-attachments/assets/9353d711-a2be-43d0-97cd-79f54655b56d)


![image](https://github.com/user-attachments/assets/baeb858b-42a9-4157-bf27-91bcf5166ce3)

## ***Query / Find Documents***


1. get all documents


![image](https://github.com/user-attachments/assets/650d4b8a-6ee4-4fec-8aa5-556db602abe2)


2. get all documents with `writer` set to "Quentin Tarantino"

![image](https://github.com/user-attachments/assets/3733e11b-5339-407a-8001-2a1e55b4c360)

3. get all documents where `actors` include "Brad Pitt"

![image](https://github.com/user-attachments/assets/b64a9c7b-b372-405a-b82e-c003bde90fd5)

4. get all documents with `franchise` set to "The Hobbit"


![image](https://github.com/user-attachments/assets/c4093771-b19b-4e5a-8eae-bd1e68bc19ba)

5. get all movies released in the 90s

![image](https://github.com/user-attachments/assets/d83a73d2-ec6c-45a1-ab7c-3a881c40327d)

6. get all movies released before the year 2000 or after 2010

![image](https://github.com/user-attachments/assets/fa451371-a1bd-4e8e-afe6-1b5ede363b9d)


## ***Update Documents***

1. add a synopsis to "The Hobbit: An Unexpected Journey" : "A reluctant hobbit, Bilbo Baggins, sets out to the Lonely Mountain with a spirited group of dwarves to reclaim their mountain home - and the gold within it - from the dragon Smaug."

![image](https://github.com/user-attachments/assets/8e8b9751-4a9e-45cb-ab93-99194c6561f3)


2. add a synopsis to "The Hobbit: The Desolation of Smaug" : "The dwarves, along with Bilbo Baggins and Gandalf the Grey, continue their quest to reclaim Erebor, their homeland, from Smaug. Bilbo Baggins is in possession of a mysterious and magical ring."

![image](https://github.com/user-attachments/assets/648f84d9-f7fc-4e8c-aeab-df3503667aea)

3. add an actor named "Samuel L. Jackson" to the movie "Pulp Fiction"

![image](https://github.com/user-attachments/assets/6261edfb-b473-44fb-b884-da092ffdb4b7)


## ***Text Search***

1. find all movies that have a synopsis that contains the word "Bilbo"

![image](https://github.com/user-attachments/assets/0c7d2b37-ed86-4f90-a7cc-463a8643cb09)

2. find all movies that have a synopsis that contains the word "Gandalf"

![image](https://github.com/user-attachments/assets/0d9d7363-684c-4947-9052-121575f882da)


3. find all movies that have a synopsis that contains the word "Bilbo" and not the word "Gandalf"

![image](https://github.com/user-attachments/assets/92eeef7f-a83f-4927-ab74-debe455735df)

4. find all movies that have a synopsis that contains the word "dwarves" or "hobbit"

![image](https://github.com/user-attachments/assets/8dc1a653-b5ae-4f60-ba35-6ed355f68838)

5. find all movies that have a synopsis that contains the word "gold" and "dragon"

![image](https://github.com/user-attachments/assets/cb9494fc-e5cd-44e0-a985-03d42a7d7e8a)

## ***Delete Documents***

1. delete the movie "Pee Wee Herman's Big Adventure"

![image](https://github.com/user-attachments/assets/c55ec0c0-8727-4940-8b22-387c48248e48)

2. delete the movie "Avatar"

![image](https://github.com/user-attachments/assets/df8da351-1205-46e0-9c9f-d9395b777289)




