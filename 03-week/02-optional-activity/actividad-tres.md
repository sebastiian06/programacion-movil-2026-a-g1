# Actividad 3 – Documentación de Requerimientos  
Proyecto: Accesorios D&M

---

# 1. Actores del Sistema

| Actor | Descripción |
|-------|------------|
| Cliente | Persona que navega en la app/web para consultar y comprar accesorios. |
| Administrador | Persona encargada de gestionar productos y visualizar pedidos. |
| Sistema de Autenticación | Servicio interno que valida credenciales y gestiona sesiones. |

---

# 2. Requerimientos Funcionales (RF)

| ID | Requerimiento Funcional | Criterio de Aceptación (GWT) |
|----|--------------------------|-------------------------------|
| RF-01 | El sistema debe permitir el registro de usuarios. | Given datos válidos, When el usuario se registra, Then la cuenta se crea correctamente. |
| RF-02 | El sistema debe permitir inicio de sesión. | Given credenciales válidas, When el usuario inicia sesión, Then accede al sistema. |
| RF-03 | El sistema debe mostrar el catálogo de productos. | Given usuario autenticado, When accede al catálogo, Then visualiza la lista de productos. |
| RF-04 | El sistema debe mostrar el detalle de un producto. | Given producto seleccionado, When entra al detalle, Then visualiza precio, descripción e imagen. |
| RF-05 | El sistema debe permitir agregar productos al carrito. | Given producto disponible, When selecciona agregar, Then se añade al carrito. |
| RF-06 | El sistema debe permitir visualizar el carrito de compras. | Given productos agregados, When accede al carrito, Then visualiza productos y total. |
| RF-07 | El sistema debe permitir confirmar un pedido. | Given carrito con productos, When confirma compra, Then se genera un pedido registrado. |
| RF-08 | El administrador debe poder agregar productos. | Given datos válidos, When el admin registra producto, Then aparece en catálogo. |
| RF-09 | El administrador debe poder editar productos. | Given producto existente, When lo modifica, Then se actualiza correctamente. |
| RF-10 | El usuario debe poder consultar su historial de pedidos. | Given usuario con pedidos previos, When accede al historial, Then visualiza sus compras anteriores. |

---

# 3. Requerimientos No Funcionales (RNF)

| ID | Requerimiento No Funcional |
|----|----------------------------|
| RNF-01 | El sistema debe responder en menos de 3 segundos en operaciones principales. |
| RNF-02 | El sistema debe manejar autenticación segura mediante tokens (JWT o similar). |
| RNF-03 | La aplicación debe ser compatible con dispositivos Android versión 8 o superior. |
| RNF-04 | La interfaz debe ser intuitiva y permitir completar una compra en máximo 5 pasos. |
| RNF-05 | Los datos sensibles deben almacenarse de forma segura (contraseñas encriptadas). |
| RNF-06 | El sistema debe permitir al menos 50 usuarios concurrentes sin fallos. |

---

# 4. Reglas de Negocio (RB)

| ID | Regla de Negocio |
|----|------------------|
| RB-01 | Un usuario debe estar registrado para poder realizar una compra. |
| RB-02 | No se puede confirmar un pedido si el carrito está vacío. |
| RB-03 | El precio del producto no puede ser negativo ni igual a cero. |
| RB-04 | Solo el administrador puede crear o editar productos. |
| RB-05 | Un pedido confirmado no puede modificarse. |

---

# 5. Casos de Uso

---

## CU-01 – Registro de Usuario

**Actor principal:** Cliente  
**Descripción:** Permite a un usuario crear una cuenta en el sistema.

### Flujo Principal
1. El usuario accede a la pantalla de registro.
2. Ingresa nombre, correo y contraseña.
3. El sistema valida los datos.
4. El sistema crea la cuenta.
5. El sistema confirma registro exitoso.

### Flujos Alternos
- 3a. Datos incompletos → El sistema muestra mensaje de error.
- 3b. Correo ya registrado → El sistema informa que el usuario ya existe.

### Requerimientos asociados
RF-01

---

## CU-02 – Comprar Producto

**Actor principal:** Cliente  
**Descripción:** Permite al usuario seleccionar productos y generar un pedido.

### Flujo Principal
1. El usuario inicia sesión.
2. Visualiza catálogo.
3. Selecciona un producto.
4. Lo agrega al carrito.
5. Accede al carrito.
6. Confirma el pedido.
7. El sistema genera el pedido.

### Flujos Alternos
- 4a. Producto sin stock → El sistema informa que no está disponible.
- 6a. Carrito vacío → No permite confirmar pedido.

### Requerimientos asociados
RF-02, RF-03, RF-04, RF-05, RF-06, RF-07

---

## CU-03 – Gestión de Productos

**Actor principal:** Administrador  
**Descripción:** Permite al administrador crear o modificar productos.

### Flujo Principal
1. El administrador inicia sesión.
2. Accede al panel administrativo.
3. Registra o edita producto.
4. El sistema valida datos.
5. El sistema guarda cambios.
6. El producto aparece actualizado en catálogo.

### Flujos Alternos
- 4a. Datos inválidos → El sistema muestra error.
- 1a. Usuario no autorizado → El sistema bloquea acceso.

### Requerimientos asociados
RF-08, RF-09

---

# 6. Trazabilidad RF ↔ Casos de Uso

| Requerimiento | Caso de Uso |
|--------------|------------|
| RF-01 | CU-01 |
| RF-02 | CU-02 |
| RF-03 | CU-02 |
| RF-04 | CU-02 |
| RF-05 | CU-02 |
| RF-06 | CU-02 |
| RF-07 | CU-02 |
| RF-08 | CU-03 |
| RF-09 | CU-03 |
| RF-10 | (Puede implementarse en futura ampliación de CU-02 o nuevo CU) |

---

# Conclusión

La documentación de requerimientos del proyecto Accesorios D&M permite establecer una base clara y verificable para el desarrollo, evitando ambigüedades. Se definieron actores, requerimientos funcionales y no funcionales, reglas de negocio, casos de uso completos y su trazabilidad, garantizando alineación entre análisis y futura implementación.