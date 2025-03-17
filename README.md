# Documentación Técnica de Salesforce - ConstruFurgo

[TOC]

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
![](./images/Ver_Accounts.png)
    

**Manejo de contactos:** ![](./images/Ver_Contactos.png)



### Creación de usuarios

#### CEO:
![](./images/Usuario_Ceo.png)

**Usuario:** carlosperez@construfurgo.tv

**Contraseña:** 9MVeLqWF