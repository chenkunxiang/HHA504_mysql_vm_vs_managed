### Self-Hosted MySQL on Azure VM

---

1. Create resource and select virtual machine.
2. Choose Ubanto 22.04, auto region and size.
3. Set admin creditials and allow SSH access.
4. Enter commands:
    ``` 
    sudo apt-get update
    sudo apt install mysql-server mysql-client -y
    ```
5. Enter mysql with:
    ``` 
    sudo mysql
    ```
6. Create a user and grant privilages to the user:
   ``` 
   CREATE USER 'chen'@'%' IDENTIFIED BY 'snakes000!';
   GRANT ALL PRIVILEGES ON *.* TO 'chen'@'%' WITH GRANT OPTION;
   
   # can check privileges using:
   SELECT * FROM mysql.user \G
   ```
7. Create database and select database:
    ```
    show databases;
    create database assignment4;

    # check creation of table:
    show databases;
    use assignment4;
    ```
8. Exit and configure Nano in order to allow all ingress actvity:
   ```
   sudo apt install nano
   sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf

   # find and change the bind-address and mysqlx-bind-address to 0.0.0.0 in order to allow all ingress activity
     - press CTRL + O to save
     - press CTRL + X to exit out
   # restart SSH to confirm changes
   sudo systemctl restart mysql
   ```
9. Given that the previous steps were performed correctly then we should be able to connect to the SSH through an external window:
   ```
   # Create your own .env file with details
   VM_DB_HOST=your-vm-public-ip
    VM_DB_PORT=3306
    VM_DB_USER=class_user
    VM_DB_PASS=change_me
    VM_DB_NAME=class_db_netid
   ```
10. Run vm_demo.py to create datafram inside of the created dataset.
11. Check if the dataset exists:
   ```
    sudo mysql
    show databases;
    use vm-for-hw4;
    show tables;
    select * from visits;
   ```








   
   
