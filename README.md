# H2 + Spring Boot

### Visión General

 Desarrolle una aplicación que exponga una API RESTful de creación de usuarios.
 
 Todos los endpoints deben aceptar y retornar solamente JSON, inclusive al para los mensajes de error.
 
 ### Configurar CodyStyle
 
  - Importar el archivo ubicado en la ruta users\user-boot\src\main\resources\codeStyle
	
	[![Imagen1.png](https://i.postimg.cc/139dsvST/Imagen1.png)](https://postimg.cc/ZCMHLFCF)

 ### H2 Base de Datos
 
  Para ingresar a la base de datos H2 se debe ingresar los siguientes valores:
  - Link: http://localhost:8080/h2
  - JDBC URL: jdbc:h2:mem:nisum
  - UserName: sa
  - Password: password
 
 ### Credenciales para API Rest
 
  Para ingresar al API Rest deberá configurar la autorización a "Basic Auth" donde los datos son:
  
  - UserName: admin
  - Password: thisismypassword
 
 ### Link Swagger
 
  Para validar la api rest de creación deberá ingresar al siguiente link 
  - http://localhost:8080/swagger-ui/index.html

### Esquma Base de Datos 

CREATE TABLE IF NOT EXISTS `USER`(
    `ID` VARCHAR(255)  default random_uuid() NOT NULL,
    `NAME` VARCHAR(30) NOT NULL,
    `EMAIL` VARCHAR(30) NOT NULL,
    `PASSWORD` VARCHAR(30) NOT NULL,
    `CREATED` DATE NOT NULL,
    `MODIFIED` DATE NULL,
    `LAST_LOGIN` DATE NULL,
    `TOKEN` VARCHAR(255) NOT NULL,
    `IS_ACTIVE` BOOLEAN DEFAULT TRUE NOT NULL,
    PRIMARY KEY (`ID`)
);$$$


CREATE TABLE IF NOT EXISTS `PHONE`(
    `ID` INT NOT NULL,
    `NUMBER` VARCHAR(30) NOT NULL,
    `CITY_CODE` VARCHAR(30) NOT NULL,
    `COUNTRY_CODE` VARCHAR(30)NOT NULL,
    `ID_USER` VARCHAR(255) NOT NULL,
    PRIMARY KEY (`ID`)
);$$$


ALTER TABLE `PHONE`
    ADD FOREIGN KEY (`ID_USER`)
        REFERENCES `USER` (`ID`);$$$

DROP SEQUENCE IF EXISTS `PHONE_SEQ`; $$$

create sequence `PHONE_SEQ` start with 1 increment by 1;$$$


### Diagrama de Solución
  
  [![Nisum-Reto-drawio.png](https://i.postimg.cc/MHYkqTP2/Nisum-Reto-drawio.png)](https://postimg.cc/Cndr4Fpm)
