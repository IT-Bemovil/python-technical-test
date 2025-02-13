# Prueba Técnica: Django - Python

## 📌 Objetivo

El objetivo de esta prueba es evaluar las habilidades del desarrollador en **Python y Django**, aplicando conocimientos en **algoritmos, optimización, validaciones, estructuras de datos y buenas prácticas en el desarrollo de APIs**.

---

## 📌 Primera Parte: Validación de Tarjetas de Crédito

### 📌 Requerimientos

Se debe desarrollar una API en **Django** y **Django REST Framework (DRF)** que permita validar si un número de tarjeta de crédito es válido o no. Para ello, se deben cumplir los siguientes criterios:

### 1️⃣ Identificación del Tipo de Tarjeta

- **Visa**: Empieza con `4` y tiene **16** dígitos.
- **Mastercard**: Empieza con `51-55` o `2221-2720` y tiene **16** dígitos.
- **American Express**: Empieza con `34` o `37` y tiene **15** dígitos.
- **Discover**: Empieza con `6011`, `644-649`, `65` y tiene **16** dígitos.

### 2️⃣ Validación de una tarjeta

Se debe implementar un **algoritmo** para verificar si un número de tarjeta es válido.

### 3️⃣ Optimización del Algoritmo

- **Primera versión**: Implementar una solución básica.
- **Segunda versión**: Optimizar usando **estructuras de datos como hash maps o árboles de búsqueda** para mejorar la eficiencia.

### 4️⃣ Creación de la API REST

Implementar un **endpoint **`` `/api/validate-card/` que reciba un número de tarjeta y devuelva:

```json
{
    "card_type": "Visa",
    "is_valid": true,
    "execution_time": {
        "before_optimization": "0.0023s",
        "after_optimization": "0.0009s"
    }
}
```

### 5️⃣ Pruebas Unitarias

- **Validar la correcta identificación del tipo de tarjeta**.
- **Probar los endpoints de la API**.

---

## 📌 Segunda Parte: Consultas en Base de Datos

### 1️⃣ Modelos de Base de Datos

#### Modelo `Transaction`

| Campo              | Tipo de Dato                       | Restricciones                              |
| ------------------ | ---------------------------------- | ------------------------------------------ |
| `id`               | `AutoField`                        | Clave primaria                             |
| `card_number`      | `CharField(16)`                    | Número enmascarado (`****-****-****-1234`) |
| `transaction_date` | `DateTimeField`                    | Fecha de la transacción                    |
| `amount`           | `DecimalField`                     | Monto de la transacción                    |
| `status`           | `CharField(10)`                    | Estado: `approved`, `declined`, `pending`  |
| `created_at`       | `DateTimeField(auto_now_add=True)` | -                                          |

#### Modelo `User`

| Campo        | Tipo de Dato                       | Restricciones      |
| ------------ | ---------------------------------- | ------------------ |
| `id`         | `AutoField`                        | Clave primaria     |
| `name`       | `CharField(100)`                   | Nombre del usuario |
| `email`      | `EmailField`                       | Único              |
| `phone`      | `CharField(15)`                    | Teléfono           |
| `created_at` | `DateTimeField(auto_now_add=True)` | -                  |

Cada transacción está asociada a un usuario (`ForeignKey`).

---

### 2️⃣ Poblar la Base de Datos

Se debe implementar un **script en Django** (`management command`) para poblar la base de datos con datos ficticios usando **Faker**:

- **100 usuarios.**
- **100,000 transacciones generadas aleatoriamente con diferentes estados (**``**, **``**, **``**).**
- **Números de tarjeta enmascarados (**``**).**

---

### 3️⃣ Consultas Avanzadas

#### 1️⃣ Total de Transacciones Aprobadas por Usuario

Debe retornar:

```json
[
    {
        "user": "Juan Pérez",
        "total_transactions": 35,
        "total_amount": 3200.50
    }
]
```

#### 2️⃣ Las 5 Tarjetas Más Utilizadas

Debe retornar:

```json
[
    {
        "card_number": "****-****-****-1234",
        "transaction_count": 2500
    }
]
```

#### 3️⃣ Total de Transacciones por Día en el Último Mes

Debe retornar:

```json
[
    {
        "date": "2024-01-01",
        "total_transactions": 1000,
        "total_amount": 25000.00
    }
]
```

---

### 4️⃣ Creación de API para Consultas

| Método | Endpoint                            | Función                                      |
| ------ | ----------------------------------- | -------------------------------------------- |
| `GET`  | `/api/users/approved-transactions/` | Total de transacciones aprobadas por usuario |
| `GET`  | `/api/cards/top-used/`              | Top 5 tarjetas más usadas                    |
| `GET`  | `/api/transactions/daily-stats/`    | Total de transacciones por día               |

---

### 📌 Consideraciones Adicionales

📢 Se recomienda tener en cuenta **el Zen de Python**, priorizando código limpio, legible y simple.  
📢 Se valorará el uso de los principios **SOLID** para un diseño bien estructurado y mantenible.  
📢 Es importante aplicar la filosofía **DRY** (*Don't Repeat Yourself*) para evitar redundancias en el código.
📢 **¡Buena suerte y a programar!** 🚀😃

