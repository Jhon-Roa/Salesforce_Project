# Documentación Técnica de Salesforce - ConstruFurgo

## Introducción

Se debe crear una organización de salesforce para la empresa construfurgo, entonces se creo una con las siguientes credenciales: 

- Dirección de la organización: https://orgfarm-7f237ed705-dev-ed.develop.my.salesforce.com/
- Nombre de usuario: roajhon98213@agentforce.com
- Contraseña: 33102108A

## Configuración General

### Información general

Se solicito ingresar la siguiente información:

| Razón social                              | ConstruFurgo S.A.S.                                          |
| ----------------------------------------- | ------------------------------------------------------------ |
| Número de Identificación Tributaria (NIT) | 901456789-2                                                  |
| Domicilio Principal                       | Av. Boyacá #12-33, Bogotá, Colombia.                         |
| Capital Social                            | $5,000,000 USD                                               |
| Tipo de Empresa                           | Sociedad por Acciones Simplificada (S.A.S.)                  |
| Objeto Social                             | Diseño, fabricación, comercialización y mantenimiento de furgones industriales. |
| Representante Legal                       | Juan Pérez López                                             |
| Registro Mercantil                        | Matrícula 456789 en la Cámara de Comercio de Bogotá.         |
| Correo Oficia                             | contacto@construfurgo.com                                    |

Los datos anteriores fueron agregados en sus campos correspondientes en company information:

- Se cambio la configuración de ubicación de la compañía ya que debido a la dirección esta se encuentra en Colombia.
- Los datos que no fue posible añadir en company information se añadieron en custom settings
- Me hubiera gustado agregar como campo lookup a contacto el representante legal, pero no era posible

![](./images/Salesforce_CompanyInformation.png)
![](./images/Extra_Company_Information.png)

### Jerarquía de roles y permisos

Se creo la jerarquía de roles y servicios como se pedía en los requerimientos y se borro la que estaba configurada de manera predeterminada:

![Rol_SetUp](./images/Rol_SetUp.png)

### Creación de permisos

Para la creación de permisos se creara una combinación entre profiles y permission sets, creando permisos de forma modular que se puedan usar en varios usuarios. se necesitan crear dos perfiles, debido a que soporte técnico sera asignado a salesforce administrator (nosotros), el role de CEO tiene permiso sobre todos los usuarios, por ende solo quedaría dos profiles por crear (SalesManager, ProcurumentSpecialist). Finalmente el profile correspondiente al gerente de producción no es necesario debido a que debido a los cambios realizados este rol fue eliminado.

#### Creación de permission sets:

**ver y editar productos productos:** 
![](./images/Ver_Productos.png)


**Manejo de proveedores:** Hay un objecto llamado seller en salesforce el cual se encuentra conectado a productos y sera el que usaremos para la gestion de proveedores
![](./images/Ver_Sellers.png)


**Manejo de oportunidades:** 
    ![](./images/Ver_Oportunidades.png)


**Manejo de oportunidades:** El objeto estandar **Orders** sera utilizado para el manejo de ordenes    ![](./images/Ver_Ordenes.png)


**Manejo de leads:** ![](./images/Ver_Leads.png)

**Manejo de Accounts:** Se otorga acesso al objeto de accounts ya que estos son los clientes junto a contacts
![	](./images/Ver_Accounts.png)
    

**Manejo de contactos:** ![](./images/Ver_Contactos.png)

**Visibilidad y creación de reportes:** Esto es algo que va a ser necesario en varios de los profiles que vamos a crear, por ende voy a crear un permission set que sera asignado a todos 
![](./images/Ver_Reportes.png)
![](./images/Ver_DashBoards.png)

#### Creacion de permission set groups:

Una vez configurado inicialmente los permission sets estos se asignan a permission set groups los cuales van a corresponder a un rol en el trabajo, cabe destacar que **esta forma de realizar el acceso a permisos fue sacado de lo aprendido en la documentación de SalesForce.**

- Al crear un permission set group podemos silenciar ciertos permisos de los permission sets que no nos interese que tenga el permission set group (los permisos en salesforce funcionan de tal manera que el mas permisivo es el que manda, por ende si este permiso se encuentra en el perfil o en otro grupo este no sera visible)

**Gerente de ventas:** Este profile se creara segun las necesides encontradas al momento de plantear el proyecto. Las cuales son las siguientes:

- Administración de clientes, oportunidades de negocio y crecimiento del mercado. 

![](./images/Gerente_Ventas_Set_Group.png)

**Gerente de Compras:**

- Manejo de proveedores y optimización de entregas.

![](./images/Gerente_Compras_Set_Group.png)

#### Creación de profiles:

Debido a que la version developer de SalesForce tiene un limite de 4 licencias SalesForce, el usuario encargado es el mismo SystemAdministrator (nosotros), por ende se crearan 3 profiles: ConstruFurgo - CEO, SalesManager y ProcurementSpecialist.

- A los perfiles en SalesForce es recomendable darles el minimo acceso clonando el perfil de MinimunAcess y a través de este asignarle permission sets y permission set groups.

**Construfurgo - CEO:** Originalmente pensaba dejar a este usuario con el rol de SystemAdministrator, pero tome la decision de crearle un rol que le diera acceso principalmente a todas las aplicaciones de ConstruFurgo.

A traves de el perfil de CEO se le dio acceso al usuario a la modificacion y visualizacion de reportes y dashboards
![](./images/CEO_Profile.png)

**SalesManager**:  Se le dio al usuario acceso a los dashboards, como parte de los requerimientos
![](./images/SalesManager_Profile.png)

**ProcurementSpecialist:**
![](./images/ProcurementSpecialist_Profile.png)


### Creación de usuarios

#### CEO:
![](./images/Usuario_Ceo.png)

**Usuario:** carlosperez@construfurgo.tv

**Contraseña:** 9MVeLqWF

#### SalesManager:
![](./images/Usuario_SalesManager.png)

**Usuario:** maría.gómez@construfurgo.tv

**Contraseña:** MIoxHcy3

#### ProcurementSpecialist.
![](./images/Usuario_ProcurementSpecialist.png)

**Usuario:** anamartinez@construfurgo.tv	

**Contraseña:** hKnP3ZGA

### Asignacion de permission set groups a usuarios:

Asignamos estos a sus usuarios correspondientes, que en estos casos serian el gerente de ventas y el gerente de compras y al ceo le damos los dos permission sets para que tengan acesso a lo que pueden hacer los usuarios

- Para agregar usuarios a un permission set group es posible filtrarlos, pero en este caso la muestra es pequeñá, por ende no fue necesario

![](./images/Asignacion_GerenteVentas.png)
![](./images/Asignacion_GerenteCompras.png)