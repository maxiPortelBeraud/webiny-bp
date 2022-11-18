# webiny-bp
boilerplate webiny


Requisitos

- Instalar Node>14 
- yarn 1.22.0 || >= 2 
- Cuenta AWS y Credenciales de usuario
- El proceso de instalación requiere 4GB de ram

----------------------------------------

Pasos hechos: 

- npx create-webiny-project my-new-project

- Configuramos = Server AWS en Sao pablo, / DynamoDB (No elastic server)


-----------------------------------------------------
Pasos a hacer:

- git clone https://github.com/maxiPortelBeraud/webiny-bp

- yarn install

- crear archivo .env
con este contenido:
---------------------------------------------------------------------------------------
# The region into which your project will be deployed.
AWS_REGION=sa-east-1

# Set secrets provider.
# See https://www.pulumi.com/docs/intro/concepts/secrets/#changing-the-secrets-provider-for-a-stack.
PULUMI_SECRETS_PROVIDER=passphrase

# Used with "passphrase" secrets provider.
# See https://www.pulumi.com/docs/reference/cli/environment-variables/.
PULUMI_CONFIG_PASSPHRASE=4ba14c8cfaf1d593a3c7875e43d85d63

# Enable debugging mode.
DEBUG=true


---------------------------------------------------------------------------------------

Configurar credenciales AWS
https://www.webiny.com/docs/infrastructure/aws/configure-aws-credentials

-Para crear su cuenta de AWS y configurar sus credenciales de IAM, primero debemos navegar a la página de la consola de AWS : https://aws.amazon.com/es/console/
-A continuación, haga clic en Create a new AWS account
-Ahora ingrese sus credenciales y cree su cuenta

-Una vez que esté registrado, inicie sesión y diríjase a la Consola de administración de AWS y seleccione 'IAM' en 'Security, Identity & Compliance'
-Haga click en 'IAM' y seleccione 'Usuarios' en 'Gestión de acceso'
-Haga click en Agregar usuario para crear la cuenta con las credenciales de IAM

-Aquí ingresa a un proceso de 5 pasos, y el primer paso es crear un nombre de usuario para las credenciales
- Elija el nombre de usuario y seleccione la casilla de verificación Acceso programático antes de pasar al siguiente paso.
-En el siguiente paso, defina el nivel de acceso para el nuevo usuario. Seleccione 'Adjuntar políticas existentes' de las tres opciones disponibles. Luego seleccione la política 'AdministratorAccess' marcando la casilla de verificación junto a ella. Cuando esté listo, haga clic en el botón Siguiente

-En caso de que no desee agregar ninguna etiqueta a su nuevo usuario, puede omitir este paso y hacer clic en el botón Siguiente

-Después de completar todos los pasos, verá una página a Revisar. Si todo es correcto, haga clic en el botón Crear usuario.

-Por último, recibirá un mensaje de éxito con su ID de clave de acceso y clave de acceso secreta. Debe copiar estas cadenas y mantenerlas seguras, ya que las necesita para el siguiente paso.   **Una vez que salga de esta pantalla, ya no podrá ver las credenciales. Si los pierde, deberá eliminar el usuario y crear uno nuevo.***

-Alternativamente, también puede definir una política detallada utilizando nuestra plantilla de CloudFormation  que creará un grupo de usuarios  con todas las políticas necesarias para su proyecto

- La creación del recurso tardará unos minutos. Después de completar, verá los registros con CREATE_COMPLETE

-------------------------------------------------------------------------------------------------------------------

Ahora que tiene el ID de la clave de acceso y la clave de acceso secreta, es hora de almacenarlos en su máquina de desarrollo.

Configuración de Windows

En máquinas con Windows, vaya a su carpeta de usuario. Eso es C:\Users\USERNAME\(reemplace USERNAMEcon su nombre de usuario real). Dentro crea una nueva carpeta llamada .aws, y dentro de la .awscarpeta crea un archivo llamado credentials. La ruta completa debería ser así: C:\Users\USERNAME\.aws\credentials.

Ahora que tenemos nuestro credentialsarchivo, edítelo y complételo así:

[default]
aws_access_key_id = PEGUE_LLAVE_ID_DE_ACCESO_AQUI
aws_secret_access_key = PEGUE_LLAVE_DE_ACCESO_SECRETA_AQUI

La palabra default dentro de los corchetes es el nombre de tu perfil. Si no configura explícitamente un nombre de perfil, AWS CLI y SDK utilizan el perfil.

-----------------------------------------------------------------------------------------------------------

-yarn webiny deploy
