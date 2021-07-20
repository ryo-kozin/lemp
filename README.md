# You can build lemp by just using docker-compose.
If you are the person who is looking for the way to create lamp server quickly, this repository is for you!!!!      
[Here is the link for lamp.](https://github.com/ryo-kozin/lamp.git)
    
## A must
Docker      

## Sturucture
| container name     | image      | function       |
| ------------------ | ---------- | --------       |
| laravel-app        | laravel    | php            |
| laravel-db         | mariadb    | database       |        
| laravel-phpmyadmin | phpmyadmin | phpmyadmin     |
| laravel-nginx      | nginx      | nginx          |

#laravel (this image will be created by a Dockerfile in your docker images)  
#You don't need use laravel in this local host, names of these containers include laravel though.
    
## Network
| network name     | relation                 | driver |
| ---------------- | ------------------------ | ------ |
| app-db           | php - mariadb            | bridge |
| app-nginx        | php - nginx              | bridge |
| db-phpmyadmin    | mariadb - phpmyadmin     | bridge |
| phpmyadmin-nginx | phpmyadmin - nginx       | bridge |
    

## How to build lamp
1. `git clone https://github.com/ryo-kozin/lemp.git`    
2. `cd lamp`   
3. `docker-compose up -d`
    - If the command can't finish evne you waited for a few minuts, please try the commans below
    - `Ctrl + C`, then `docker-compose start`
    - Lamp will be built soon.
___
If you create a laravel project, keep following the commands below.    
4. `docker exec -it laravel-app bash`  
5. `comopser create-project laravel/laravel {project name}`    
6. `exit`    
7. `open .env file in the project`   
8. Change the infomation.`DB_HOST = laravel-db, DB_DATABASE = user_system, DB_PASSWORD = root`     
- You can create a new database to excute commands below.    
- `docker exec -it laravel-db bash`    
- `mysql -uroot -p`    
- `root`   
- `create database {database name};`   
- `exit;`      
9. Finally open /lemp/nginx/conf.d/app.conf then chage the code.     
- From `root /var/www/html` to `root /var/www/html/{project name}/public`      
11. Access http://localhost, you can see the laravel project.
    
## URL    
localhost : http://localhost   
phpmyadmin : http://localhost:8000    
