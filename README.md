# 🚀 Guías de Prácticas Laravel - TaskBoard: Pasarela de Pagos

![Laravel](https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)

---

<p align="center">
  <img src="https://res.cloudinary.com/bcwlyire/image/upload/v1785118882/NUEVO-LOGO-UPED-A-COLOR-scaled_szoqws.jpg" alt="Logo UPED" width="300"/>
</p>

## 🏛️ Información Académica

- **Institución:** Universidad Pedagógica de El Salvador *Luis Alonso Aparicio*
- **Facultad:** Ingeniería
- **Asignatura:** Integración de Sistemas
- **Ciclo:** 02-2026
- **Docente:** Ing. Oscar Contreras
- **Proyecto Integrador:** TaskBoard - Pasarela de Pagos

---

## 📌 Descripción del Proyecto

Este repositorio contiene el trabajo de la **Semana 8** del proyecto **TaskBoard**, una plataforma de **Pasarela de Pagos** desarrollada en el framework **Laravel 11**.

Esta semana corresponde al **repaso integrador de la Unidad II** previo al Primer Examen Parcial: se consolidan en un solo proyecto limpio los tres bloques vistos hasta ahora —**Routing**, **Eloquent ORM** y **Blade**— dejando la aplicación completa y navegable de punta a punta.

1. **Routing:** rutas con nombre (`comercios.index`, `comercios.show`) y **Route Model Binding** en la vista de detalle.
2. **Eloquent:** relación `hasMany` / `belongsTo`, `withCount('transacciones')` y `load('transacciones')` para evitar el problema de consultas N+1, más un **seeder** que deja datos de prueba reproducibles.
3. **Blade:** layout maestro con estilos propios de la pasarela y tres componentes reutilizables (`<x-badge-estado>`, `<x-badge-actividad>` y `<x-resumen-actividad>`), que sustituyen los bloques `@if` repetidos dentro de las vistas.

Al terminar, `/comercios` y `/comercios/{id}` funcionan completamente con layout, componentes y datos reales.

---

## 📁 Estructura del Proyecto

A continuación se detalla la estructura principal del repositorio y del proyecto Laravel `taskboard`:

```text
taskboard/
├── app/
│   ├── Http/
│   │   └── Controllers/
│   │       └── ComercioController.php                # index() con withCount y show() con load()
│   └── Models/
│       ├── Comercio.php                              # hasMany(Transaccion)
│       ├── Transaccion.php                           # belongsTo(Comercio) + hasMany(EventoTransaccion)
│       └── EventoTransaccion.php                     # belongsTo(Transaccion)
├── config/                                           # Archivos de configuración general del sistema
├── database/
│   ├── migrations/
│   │   ├── create_comercios_table.php                # Comercios afiliados a la pasarela
│   │   ├── create_transacciones_table.php            # Monto, cliente y estado de cada transacción
│   │   └── create_eventos_transaccion_table.php      # Bitácora de cambios de estado
│   └── seeders/
│       └── ComercioSeeder.php                        # Datos de ejemplo usados en todas las guías
├── public/                                           # Punto de entrada de la aplicación (index.php) y assets
├── resources/
│   └── views/
│       ├── layouts/
│       │   └── app.blade.php                         # Layout maestro con estilos de la pasarela
│       ├── components/
│       │   ├── badge-estado.blade.php                # Etiqueta de color según el estado
│       │   ├── badge-actividad.blade.php             # "Activo" / "Sin actividad"
│       │   └── resumen-actividad.blade.php           # Mensaje según cantidad de transacciones
│       └── comercios/
│           ├── index.blade.php                       # Listado de comercios afiliados
│           └── show.blade.php                        # Detalle del comercio y sus transacciones
├── routes/
│   └── web.php                                       # Rutas con nombre y Route Model Binding
├── storage/                                          # Registros (logs), archivos cargados y caché de la app
├── vendor/                                           # Dependencias de PHP administradas por Composer
├── .env.example                                      # Variables de entorno de ejemplo
├── composer.json                                     # Configuración de Composer y paquetes
└── README.md                                         # Documentación principal del repositorio
```
