# Examen práctico take-home – Junior Full Stack

## Duración
3 a 4 horas

## Tecnologías
- NestJS
- React
- MySQL
- Git

## Nivel esperado
Junior full-stack. No se requiere experiencia avanzada en NestJS, Docker ni despliegue. El objetivo es evaluar la capacidad para construir una solución funcional, ordenada y documentada.

---

## Objetivo
Desarrollar una aplicación web para gestionar un catálogo de productos de una tienda.

La solución debe incluir:
- Backend en NestJS
- Frontend en React
- Base de datos MySQL
- Control de versiones con Git
- Código limpio y legible
- Validaciones y manejo básico de errores

---

## Caso de uso
Una pequeña tienda necesita administrar su inventario de productos. La aplicación debe permitir:

- Ver la lista de productos
- Consultar un producto por ID
- Crear un producto
- Actualizar un producto
- Eliminar un producto
- Buscar productos por nombre o SKU
- Filtrar productos por categoría

---

## Requisitos funcionales
La aplicación debe permitir lo siguiente:

1. Registrar productos con los campos mínimos requeridos.
2. Listar todos los productos.
3. Consultar un producto específico.
4. Actualizar información de un producto.
5. Eliminar un producto.
6. Validar entradas:
   - nombre obligatorio
   - SKU único
   - precio mayor a 0
   - stock mayor o igual a 0
7. Mostrar errores claros si la validación falla o si el recurso no existe.
8. Mostrar una interfaz sencilla para consumir la API desde React.

---

## Entregable
Debe entregar un repositorio funcional con:
- backend
- frontend
- base de datos local configurada con MySQL
- README con instrucciones de ejecución
- historial de commits en Git

---

## Requisitos obligatorios

### Backend
- Crear un proyecto NestJS.
- Conectar a MySQL.
- Crear al menos estas entidades:
  - Category
  - Product
- Implementar CRUD completo de productos.
- Implementar validaciones con class-validator o equivalente.
- Manejar errores con mensajes claros.
- Exponer endpoints REST.
- Permitir búsqueda y filtro por categoría.

### Frontend
- Crear una interfaz en React para:
  - listar productos
  - agregar producto
  - editar producto
  - eliminar producto
  - buscar productos
- Consumir la API con fetch o axios.
- Mostrar estados de carga, éxito y error.
- Validar formularios del lado del cliente.

### Base de datos
- Usar MySQL local.
- Configurar credenciales mediante variables de entorno.
- Crear esquema con migración o script inicial.

### Git
- Tener un repositorio Git.
- Realizar commits con mensajes claros.
- Mantener un historial limpio y legible.

### Documentación
- Incluir README con:
  - descripción del proyecto
  - instalación
  - configuración de base de datos
  - comandos para ejecutar backend y frontend
  - endpoints principales
  - instrucciones de uso

---

## Requisitos opcionales
Estos no son obligatorios, pero suman valor:

- Paginación
- Ordenamiento por precio o nombre
- Mensajes tipo toast o alertas
- Eliminación lógica en lugar de física
- Tests básicos de servicio o controlador
- Filtros por precio mínimo o máximo
- Mejoras de UX con diseño simple
- Validación de existencia de categoría antes de crear un producto

---

## Modelo de datos sugerido

### Tabla: categories
- id: bigint/int, PK, autoincremental
- name: varchar(100), obligatorio, único
- createdAt: datetime
- updatedAt: datetime

### Tabla: products
- id: bigint/int, PK, autoincremental
- name: varchar(150), obligatorio
- sku: varchar(100), obligatorio, único
- description: text, opcional
- price: decimal(10,2), obligatorio, mayor que 0
- stock: int, obligatorio, mayor o igual a 0
- categoryId: int, FK, obligatorio
- isActive: boolean, default true
- createdAt: datetime
- updatedAt: datetime

> Puedes simplificar y usar solo una tabla products si lo prefieres, pero el uso de categorías demuestra mejor la modelación.

---

## Endpoints sugeridos

### Categorías
- GET /categories
- GET /categories/:id
- POST /categories
- PATCH /categories/:id
- DELETE /categories/:id

### Productos
- GET /products
- GET /products/:id
- GET /products?search=...&categoryId=...
- POST /products
- PATCH /products/:id
- DELETE /products/:id

### Ejemplo de payload
Crear producto:
```json
{
  "name": "Laptop Lenovo",
  "sku": "LEN-001",
  "description": "Laptop 14 pulgadas",
  "price": 899.99,
  "stock": 15,
  "categoryId": 1
}
```

Actualizar producto:
```json
{
  "price": 949.99,
  "stock": 10
}
```

---

## Criterios de aceptación
La solución será considerada correcta si:

- El backend funciona y se conecta a MySQL.
- El CRUD de productos funciona correctamente.
- Se validan campos y reglas de negocio.
- El frontend permite listar, crear, editar y eliminar productos.
- La búsqueda por nombre o SKU funciona.
- El sistema devuelve mensajes de error claros.
- El README incluye instrucciones de ejecución.
- El repositorio tiene historial de Git.
- El código está organizado y es legible.
- La solución no requiere Docker ni despliegue avanzado.

---

## Instrucciones de ejecución

### Requisitos mínimos
- Node.js 18+
- npm o yarn
- MySQL 8
- Git

### Pasos recomendados
1. Clonar repositorio
2. Crear base de datos
3. Configurar variables de entorno
4. Instalar dependencias del backend
5. Ejecutar migraciones o sincronizar schema
6. Iniciar backend
7. Instalar dependencias del frontend
8. Iniciar frontend
9. Probar las rutas principales

### Ejemplo de comandos
```bash
npm install
npm run start:dev
npm install
npm run dev
```

> Las instrucciones exactas pueden variar según el proyecto, pero el README debe dejarlo claro.

---

## Evaluación
La prueba se evaluará principalmente en:
- funcionalidad
- calidad del código
- validaciones
- manejo de errores
- experiencia de uso
- claridad de documentación
- uso de Git

---

## Versión corta para enviar al candidato
> Crear una aplicación full-stack para gestionar un catálogo de productos de una tienda. El backend debe estar desarrollado en NestJS, conectarse a MySQL y exponer un CRUD para productos y categorías. El frontend debe estar desarrollado en React y consumir la API para listar, crear, editar y eliminar productos. Debe incluir validaciones, manejo de errores, búsqueda por nombre/SKU y una interfaz simple. Debe entregarse con Git y un README con instrucciones para ejecutar el proyecto. La prueba tiene una duración de 3 a 4 horas y no requiere conocimientos avanzados de NestJS, Docker ni despliegue.

---

## Contacto del evaluador
Si necesitas presentar esta prueba a un candidato, puedes usar este documento tal cual o adaptarlo al tono de la empresa.
