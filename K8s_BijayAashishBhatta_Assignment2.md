1. **Deploying Postgres database using PVC & PV cluster:**

        $ sudo mkdir postgreesql
        $ cd postgreesql/
        $ echo "P@ssw0rd" | base64
        $ sudo vim secrets.yaml
        $ sudo vim pv.yaml
        $ sudo vim pvc.yaml
        $ sudo vim deployment.yaml
        $ sudo vim service.yaml
        $ kubectl apply -f secrets.yaml
        $ kubectl apply -f pv.yaml
        $ kubectl apply -f pvc.yaml
        $ kubectl apply -f deployment.yaml
        $ kubectl apply -f service.yaml

2. **Deploying Postgres Client in cluster(psql):**

        $ kubectl create namespace postgre-client
        $ kubectl apply -n postgre-client -f secrets.yaml
        $ kubectl apply -n postgre-client -f pv-client.yaml
        $ kubectl apply -n postgre-client -f pvc.yaml
        $ kubectl apply -n postgre-client -f deployment.yaml
        $ kubectl apply -n postgre-client -f service.yml

3. **Connecting Postgres database from Postgres Client using core-dns's host name:**
   
   I could not connect using dns hostname (postgres.postgre-client.svc.cluster.local), so I am using minikube IP address (192.16.49.2) and port used by postgres client (30235) to connect to database server.
     
        $ psql -h 192.168.49.2 -p 30235 -U postgres (password = P@ssw0rd)
      
   ![image](https://user-images.githubusercontent.com/34814966/145539680-36588773-58ca-434b-974a-a5e21d0c89ce.png)


4. **Creating a database(internship) and few tables in database:**
        
        $ psql -h 192.168.49.2 -p 30235 -U postgres
        # CREATE DATABASE internship;
        # \c internship;
        # CREATE TABLE students (SID serial PRIMARY KEY, Name VARCHAR (70) NOT NULL, Age SMALLINT NOT NULL, Address VARCHAR(255) NOT NULL);
        # CREATE TABLE tutors (TID serial PRIMARY KEY, Name VARCHAR (70) NOT NULL, Post VARCHAR (70) NOT NULL);
   ![image](https://user-images.githubusercontent.com/34814966/145544905-d9ab31f8-6d82-44fc-830c-ebbad39e507f.png)

     
