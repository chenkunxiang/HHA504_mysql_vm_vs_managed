### Managed MySQL on GCP

---

1. Create instance in Cloud SQL
- Ensure that its the latest version of MySQL
- Note the user and password
- Other details can be left the default settings
- Under Network, add a new network and press "Use my IP"
- Create
2. Creating your user in the Instance
- Go under Instance and click on user, and add user account
- Note the name and password used here
- Allow any host
- Add
3. Creating your database in the Instance
- Select database and create database
- Note the name used for the database here
- Create
4. Open the shell and open the terminal and enter
   ```
   gcloud sql connect assignment4 --user=root --quiet
   
   # note that 'assignment4' may have to be changed to what your project is in gcp
   # you will be prompted to fill in your password here but the characters will not show
   ```
5. Once connected, enter
   ```
   GRANT ALL PRIVILEGES ON assignment4.* TO 'user'@'%';
   FLUSH PRIVILEGES;
   ```
6. Create your .env file
   ```
    MAN_DB_HOST=your-managed-endpoint
    MAN_DB_PORT=3306
    MAN_DB_USER=class_user
    MAN_DB_PASS=change_me
    MAN_DB_NAME=class_db_netid
   ```
7. Run managed_demo.py in order to create a table
8. Open the cloud back up and enter
   ```
   gcloud sql connect assignment4 --user=root --quiet

   # enter password again
   # once in mysql
   show databases;
   use assignment4;
   show tables;
   select * from visits;
  ```
