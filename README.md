Requisitos solicitados.
Desarrolle una aplicación que exponga una API RESTful de creación de usuarios. Todos los endpoints deben aceptar y retornar solamente JSON, inclusive al para los mensajes de error. Todos los mensajes deben seguir el formato: {"mensaje": "mensaje de error"}

registro
Ese endpoint deberá recibir un usuario con los campos "nombre", "correo", "contraseña", más un listado de objetos "teléfono", respetando el siguiente formato:

  {
  "name": "Juan Rodriguez",
  "email": "juan@rodriguez.org",
  "password": "hunter2",
  "phones": [
  {
  "number": "1234567",
  "citycode": "1",
  "contrycode": "57"
  }
  ]
  }
Responder el código de estado HTTP adecuado

En caso de éxito, regrese el usuario y los siguientes campos:

id: id del usuario (puede ser lo que se genera por el banco de datos, pero sería más deseable un UUID)

creado: fecha de creación del usuario

modificado: fecha de la última actualización de usuario

last_login: del último ingreso (en caso de nuevo usuario, va a coincidir con la fecha de creación)

token: token de acceso de la API (puede ser UUID o JWT)

isactive: Indica si el usuario sigue habilitado dentro del sistema.

Si caso el correo consta en la base de datos, deberá devolver un error "El correo ya registrado".

El correo debe seguir una expresión regular para validar que formato sea el correcto. ( aaaaaaa@dominio.cl )

La clave debe seguir una expresión regular para validar que formato sea el correcto. (Una Mayuscula, letras minúsculas, y dos números)

Se debe hacer traza de logs dentro del aplicativo.

El token deberá ser persistido junto con el usuario

Obligatorio:
Banco de datos en memoria.
Gradle como herramienta de construcción.
Pruebas unitarias (Deseable: Spock Framework).
Persistencia con hibernación.
Arranque de primavera del marco.
Java 8 o superior. (Usar más de dos características propias de la versión)
Entrega en un repositorio público (github, gitlab o bitbucket) con el código fuente.
Entregar diagrama de componentes de la solución y al menos un diagrama de secuencia (ambos diagramas son de carácter obligatorio y deben seguir los estándares UML).
README.md debe contener las instrucciones para levantar y usar el proyecto.
Deseable
JWT cómo token
¿Qué contiene el repositorio?
Base de datos de memoria h2.
Unidad de prueba con Junit.
Java versión 8.
Api Rest findUserByEmail responde al requisito.
Token JWT y persistencia del usuario durante la sesión.
Todos los proyectos tienen diversidad de sintaxis para código Java antiguo y nuevo.
Extra :
Bcrypt para contraseña y token.
JWT.
Excepción del controlador con asesoramiento del controlador.
4 Api Rest al requisito de formalización con estándares.
Cambie el nombre del campo countrycode a country_code, por error tipográfico.
Cambie el nombre del campo citycode a city_code, por error tipográfico.
Colección, entorno para Postman con todas las API rest y token persistente en el directorio repositorio-ejercicio-one-globallogic-cl\src\main\resources\postman.
Consola de pancartas.
Antes de empezar
Dependencias
Considere el uso de esta versión.

Dependencia	Versión
IDEA IntelliJ	1.8.0_152
Gradle	4.10.3
H2	2.4.1
Java JDK	1.8
Cartero	7.18.0
ventanas	10
Descanso API
Validaciones comunes
Vacío
Nulo
Descanso API	Método	Protegido	Validaciones	Pedido	Respuesta
/v1/desprotegido/doSignIn	CORREO	FALSO	formatear correo electrónico, formatear contraseña, verificar que el usuario exista correo electrónico, coincidencia de correo electrónico y contraseña	{"name":"FirstNameExample LastNameExample","email":" email@example.com ","contraseña":"Contraseñaexampler12","teléfonos":[{"número":"946644558","city_code":"1 ","country_code":"57"}]}	{"id":1,"created":"16-02-2020 22:34:26","modified":"16-02-2020 22:35:07","last_login":"16-02- 2020 22:35:07","token":"eyJhbGciOiJIUzI1NiJ9","active":true}
/v1/protegido/hacerSignOut	CORREO	FALSO	Experimentación del token en segundos y cierre de sesión de destrucción del token.	ninguno	{"message":"Cierre de sesión exitoso, que tengas un gran día."}
/v1/protected/getUsuarios	CONSEGUIR	verdadero	Experimentación de token en segundos, cierre de sesión de destrucción de token, roles de usuario	ninguno	{"id":1,"name":"FirstNameExample LastNameExample","email":" email@example.com ","contraseña":"$2a$16$gSv/X20v2iC39eVKrkVfSeM3Ky4PFY3Ww/pOMd7nlYsS8/OnUVsJ6","phones": [{"number":"946644558","city_code":"1","country_code":"57"}],"created":"16-02-2020 22:34:26","modified":" 16-02-2020 22:35:07","last_login":"16-02-2020 22:35:07","token":"eyJhbGciOiJIUzI1NiJ9","roles":["ROLE_ADMIN","ROLE_USER"] , "activo": verdadero}
/v1/protected/findUserByEmail	CONSEGUIR	verdadero	Experimentación del token en segundos, destrucción del token, cierre de sesión, roles de usuario, formato del correo electrónico, verificación de que el correo electrónico existe	{"correo electrónico":" correo electrónico@ejemplo.com "}	{"id":1,"created":"16-02-2020 22:34:26","modified":"16-02-2020 22:35:07","last_login":"16-02- 2020 22:35:07","token":"eyJhbGciOiJIUzI1NiJ9","active":true}
Instalación
Instalar las dependencias.
Importe el proyecto a su IDE.
Ejecute la prueba y arranque gradle en el proyecto.
Importe la colección y el entorno a su cartero, ubíquelo en el directorio repositorio-ejercicio-one-globallogic-cl\src\main\resources\postman
Ahora pruebe todos los puntos finales.
Autores
Patricio Castillo
Licencia
MIT
