<div align="center">

<img src="docs/img/banner.png" alt="ERP Automotriz" width="100%">

![Estado](https://img.shields.io/badge/estado-en%20desarrollo-f59e0b?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Tkinter](https://img.shields.io/badge/Interfaz-Tkinter-c2410c?style=for-the-badge)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)

</div>

---

## 📌 Descripción

ERP orientado a **integrar y automatizar** los procesos administrativos, operativos y financieros de un negocio de **repuestos y taller automotriz**: inventario de piezas, clientes y vehículos, órdenes de trabajo, facturación y reportes.

El sistema está diseñado inicialmente para una empresa del sector automotriz, con la posibilidad de adaptarse después a otros talleres.

## 🎯 Objetivo

Centralizar la información del negocio en una sola plataforma para **controlar el stock de repuestos**, reducir errores en la facturación y facilitar la toma de decisiones con reportes claros.

---

## 📋 Tabla de contenidos

- [Módulos](#-módulos)
- [Flujo del proceso](#-flujo-del-proceso)
- [Arquitectura](#️-arquitectura)
- [Modelo de base de datos](#️-modelo-de-base-de-datos)
- [Cómo ejecutar](#-cómo-ejecutar)
- [Estructura del proyecto](#️-estructura-del-proyecto)
- [Guion de la demostración](#-guion-de-la-demostración)
- [Equipo](#-equipo)

---

## 🧩 Módulos

<img src="docs/img/modulos.png" alt="Módulos del ERP" width="100%">

| Módulo | Qué hace | Tipo de sistema | Estado |
|:--|:--|:--:|:--:|
| 🔐 **Inicio de sesión** | Acceso con usuario y contraseña, bloqueo tras 3 intentos fallidos | — | ✅ |
| 📦 **Inventario de repuestos** | Catálogo de piezas (código, marca, compatibilidad), entradas de mercadería y alertas de stock bajo | TPS | 🛠️ |
| 🚗 **Clientes y vehículos** | Registro de clientes, sus vehículos (placa, marca, modelo, año, km) e historial de servicios | TPS | 🛠️ |
| 🧰 **Órdenes de trabajo** | Apertura de órdenes, asignación de mecánico, repuestos usados y estados *Abierta → En proceso → Terminada* | TPS | 🛠️ |
| 🧾 **Facturación** | Facturas de órdenes terminadas y ventas de mostrador, con IVA 15 % y forma de pago | TPS | 🛠️ |
| 📊 **Reportes** | Ventas, repuestos más vendidos, órdenes por estado y repuestos por reponer | MIS / DSS | ⏳ |

> ✅ Terminado · 🛠️ En desarrollo · ⏳ Pendiente

---

## 🔄 Flujo del proceso

<img src="docs/img/flujo.png" alt="Flujo del proceso" width="100%">

---

## 🏗️ Arquitectura

<img src="docs/img/arquitectura.png" alt="Arquitectura en capas" width="100%">

---

## 🗄️ Modelo de base de datos

```mermaid
erDiagram
    CLIENTE ||--o{ VEHICULO : "tiene"
    VEHICULO ||--o{ ORDEN_TRABAJO : "recibe"
    MECANICO ||--o{ ORDEN_TRABAJO : "atiende"
    ORDEN_TRABAJO ||--o{ DETALLE_ORDEN : "usa"
    REPUESTO ||--o{ DETALLE_ORDEN : "aparece en"
    CLIENTE ||--o{ FACTURA : "paga"
    ORDEN_TRABAJO |o--o| FACTURA : "se factura en"
    FACTURA ||--o{ DETALLE_FACTURA : "contiene"
    REPUESTO ||--o{ DETALLE_FACTURA : "se vende en"
    REPUESTO ||--o{ MOVIMIENTO_INVENTARIO
