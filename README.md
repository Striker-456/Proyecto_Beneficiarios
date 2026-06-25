1.Hechos
<img width="1918" height="955" alt="Captura de pantalla 2026-06-24 193753" src="https://github.com/user-attachments/assets/98be6531-a0a4-4eea-8315-6eaaae2660ea" />Este proyecto es una aplicación web desarrollada con Next.js y MySQL que permite gestionar la información de beneficiarios de convocatorias educativas en Bogotá. La aplicación está construida bajo el patrón de arquitectura MVC (Modelo-Vista-Controlador).

   Es la vista principal del sistema. Gestiona la tabla de hechos, que concentra toda la información de los beneficiarios por convocatoria. Permite crear, consultar, editar y eliminar registros que relacionan variables como localidad, institución educativa, núcleo básico del conocimiento, modalidad, sector, zona del colegio, puntaje Saber 11, sexo, edad, grupo étnico, condición de víctima del conflicto armado, discapacidad, nivel Sisbén y cantidad de beneficiarios. Cada campo se presenta mediante listas desplegables que se llenan automáticamente desde los catálogos de la base de datos, garantizando la integridad referencial de los datos.

2. Localidades 
<img width="1910" height="951" alt="image" src="https://github.com/user-attachments/assets/0546880d-2848-4548-baa3-b8a0aaf0d915" />
Gestiona el catálogo de localidades de Bogotá. Permite consultar todas las localidades registradas, agregar nuevas, modificar su código o nombre, y eliminar registros existentes. Es una de las tablas de referencia que alimenta los formularios de la vista de Hechos.

3.Discapacidad 
<img width="1909" height="954" alt="image" src="https://github.com/user-attachments/assets/f6c76c98-0e3e-43ae-ac68-3313732c36a2" />
Gestiona el catálogo de tipos de discapacidad registrados en el sistema. Permite visualizar todos los tipos existentes, agregar nuevas categorías, editarlas y eliminarlas. Al igual que Localidades, es una tabla de referencia utilizada en el registro de hechos para clasificar a los beneficiarios según su condición.






