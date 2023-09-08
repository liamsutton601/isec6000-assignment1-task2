ISEC6000-Assignment1-Task2

Running a Saleor Stack with Sample Data

**Forking the Saloer Repository**

On the saleor-platform repository page, on the top right hand corner option 'fork' to open the fork menu. Then click on 'Create a fork' and fill in the required details. 

![Step 1](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/b1425164-0926-4d52-88a5-1cb972d630f3) ![Step 2](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/41a6007b-6362-40dd-81f3-602a7185cd9e)

**Cloning the Repository**

On a linux environment, create a new directory. Open a terminal in this directory. 
To clone the repository, run the following command from within the directory: 

git clone git clone https://github.com/<yourusername>/<titleofrepository>.git

For this specific example, the command was used as follows:

git clone https://github.com/liamsutton601/isec6000-assignment1-task2.git

![Step 3](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/01f2e990-bf4c-4f96-a843-4f83399b10d6)

The command has the following output when run: 

![Step 4](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/bd0d619d-8ea6-4dfa-83d1-6e9d4f4c5fd6)

**Running The Saleor-Platform**

Change into the cloned directory:

cd isec6000-assignment1-task2

Build the application:

docker-compose build

![Step 5PNG](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/a71614ea-fee0-4939-a7f3-7665cd0b1925)

Apply the Django migrations: 

docker-compose run --rm api python3 manage.py migrate

![Step 6](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/42ee3cbe-43f5-4a7b-9e1f-740f823cc011)]\

![Step 7](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/551e100a-3898-47ce-a096-aba32c7df750)

Populate the database with example data and create the admin user:

docker-compose run --rm api python3 manage.py populatedb --createsuperuser

![Step 8](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/d2bc696d-37cf-4fa4-8016-c187705453d4)

![Step 9](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/8dc56969-e955-497d-bffc-2714bb86aba2)

Run the application:

docker-compose up

![Step 10](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/06790765-48bb-4ac7-a1f0-9a14f34ca2fb)

![Step 11](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/b003b07f-ab75-4690-ad94-5242b27ba059)

**Confirming The Application Is Running**

The respective applications run on the following ports:

Saleor Core: 8000
Saleor Dashboard: 9000
Jaeger UI: 16686
Mailpit: 8025

The links for the applications are as follows, with pictures as proof of them working: 

- Saleor Core (API) - http://localhost:8000

![Step 12](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/493eb2b2-24ce-405b-9455-f1aa3585ae67)

 
- Saleor Dashboard - http://localhost:9000

![Step 13](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/8f612623-286d-48f3-bed0-6250687e211f)


- Jaeger UI (APM) - http://localhost:16686

![Step 14](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/69ac84d1-c780-4b7d-9073-22d9919624eb)

 
- Mailpit (Test email interface) - http://localhost:8025

![Step 15](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/2743df74-31b3-44a4-be14-05e28edaef11)
  

**Changing The Compose File For Different Ports**

If the stack is running, you must close with the following command:

docker-compose down

![Step 116](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/56cf8c29-e681-454b-9369-aceb4fda86c5)

Open the 'docker-compose.yml' file. 

To change the port of Saleor React Storefront to 3009 from 8000 - 

Under the 'services' heading on line 7 of the compose file, change  '8000:8000' to '3009:8000'.

From This:

![Step 18](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/ea9c240e-a9a3-46bf-8ad6-1718fc2b4a4f)


To This:

![Step 17](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/5158babc-1861-4513-aef2-ff41f436885e)

To Change the port of Saleor Dashboard to 9003 from 9000 - 

Under the dashbhoard heading on line 31 of the compose file, change '9000:80' to '9003:80'

From This:

![Step 19](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/389bef9e-ae99-4e3d-9461-d597aac106b5)


To This:

![Step 20](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/80b5b51c-73bb-4df2-8f59-a269c7e2b766)


**Confirming The Changes Work**

Restart the saleor stack with the command:

docker-compose up

Once started, the programs will be available on the following links:

- Saleor Core (API) - http://localhost:3009
- 
![Step 21](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/ae8c6b89-9504-417f-98f8-6f8474dec13a)

- Saleor Dashboard http://localhost:9003

![Step 22](https://github.com/liamsutton601/isec6000-assignment1-task2/assets/130027096/579ca6e7-a0a8-40d2-bc66-ab7e5c174574)


