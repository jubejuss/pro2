# What we are doing
## ORM
[Ormi link](https://blog.bitsrc.io/what-is-an-orm-and-why-you-should-use-it-b2b6f75f5e2a)  

[TYPEORM](https://github.com/typeorm/typeorm)  

* Install `npm install typeorm`  
* Install `npm install reflect-metadata --save` 
* If note done, then `npm install @types/node --save-dev` 
* Install database driver, depends what you use or want.  At the moment MySql `npm install mysql --save`
* Add to tsconfig.ts two lines:  
```javascript
"emitDecoratorMetadata": true,
"experimentalDecorators": true,
```
And `"lib": ["es6"]`  

* Let's make new file `database.ts`  (Because we allready have db.ts). Put inside:  
```javascript
import "reflect-metadata";
import { createConnection } from "typeorm";

createConnection({
    type: "mysql",
    host: "localhost",
    port: 3306,
    username: "root",
    password: "admin",
    database: "test",
    entities: [
        
    ],
    synchronize: true,
    logging: false
}).then(connection => {
    // here you can start to work with your entities
}).catch(error => console.log(error));
```

* Check username and password  
* Entities are our data
* syncronize - it means, that when it's true, then all data goes to database. Otherwise not. So when the api goies live, then put that false, then noone cant destroy database. It's for developing purpose.  
* kui ühendus loodud, siis ... ja kui error ... siis  
* and finally export from database and import to index  
* `logging: true,` shows queries in terminal  


## make database
Make new database and NM!!!  **Make new schema** 

### Make tables  
* Folder users `entity.ts` 
* Copy from github link part: `Creating an auto-generated column` 
* Change interfaces to what needed (look at interfaces)  

### Send info to table
* `users/service.ts` createuser
* from githab user manual check `Using async/await syntax` 
* To avoid conflicts we must name unical names. eUser in entity. User in interface.

* Get users `get all users`

* at the moment take down middleware what is controlling logging

* 