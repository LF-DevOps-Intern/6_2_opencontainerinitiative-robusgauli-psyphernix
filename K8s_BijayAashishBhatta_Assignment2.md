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



3. **Connecting Postgres database from Postgres Client using core-dns's host name:**



4. **Creating a database(internship) and few tables in database:**
