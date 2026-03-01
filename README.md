# API Gestión de Equipos Médicos

- **Estudiante:** Pedro Luis Zamora Martinez
- **Curso:** Backend 2 - Java  

---

## 📌 Descripción del Proyecto

Esta API simula un sistema de gestión de equipos médicos utilizados en entornos hospitalarios.  
Permite realizar operaciones CRUD (Crear, Leer, Actualizar y Eliminar) sobre los equipos registrados.

El objetivo es demostrar el diseño de un modelo de datos complejo, la implementación de pruebas mediante Postman y la documentación profesional del ciclo de vida del recurso.

---

## 🌐 URL Base de la API

- **URL:** `https://698782d48bacd1d773ed9c2a.mockapi.io/medical-equipment`

---

## 1. Modelo de Datos

Se configuró el recurso de **Equipos Médicos** con la siguiente estructura de datos.

```json
[
  {
    "name": "Monitor de Signos Vitales Dash 4000",
    "description": "Monitor multiparamétrico para cuidados intensivos y urgencias.",
    "specification": {
      "parameters": ["ECG", "SpO2", "NIBP", "Temp"],
      "screen": "10.4 inch LCD"
    },
    "maintenanceLogs": [
      {
        "date": "2024-01-15",
        "type": "Calibración anual",
        "technician": "Ing. Biomédico Ramos"
      }
    ],
    "isOperational": true,
    "id": "1"
  }
]
```

---

## 2. Bitácora de Operaciones CRUD

### A. Obtener todos los registros (`GET`)

- **Endpoint:** `/medical-equipment`
- **Status Code:** `200 OK`
- **Respuesta de Postman:**

```json
[
    {
        "name": "Monitor de Signos Vitales Dash 4000",
        "description": "Monitor multiparamétrico para cuidados intensivos y urgencias.",
        "specification": {
            "parameters": ["ECG", "SpO2", "NIBP", "Temp"],
            "screen": "10.4 inch LCD"
        },
        "maintenanceLogs": [
            {
                "date": "2024-01-15",
                "type": "Calibración anual",
                "technician": "Ing. Biomédico Ramos"
            }
        ],
        "isOperational": true,
        "id": "1"
    },
    {
        "name": "Desfibrilador Externo Automático (DEA) G5",
        "description": "Dispositivo de respuesta rápida con instrucciones de voz.",
        "specification": {
            "energy": "Bifásica",
            "batteryLife": "4 years",
            "ipRating": "IP55"
        },
        "maintenanceLogs": [
            {
                "date": "2023-11-20",
                "type": "Cambio de parches/electrodos",
                "technician": "Soporte Técnico"
            }
        ],
        "isOperational": true,
        "id": "2"
    },
    {
        "name": "Ventilador Mecánico Puritan Bennett 980",
        "description": "Sistema de ventilación asistida para pacientes neonatales y adultos.",
        "specification": {
            "modes": ["AC", "SIMV", "SPONT"],
            "oxygenInlet": "High Pressure"
        },
        "maintenanceLogs": [],
        "isOperational": false,
        "id": "3"
    },
    {
        "name": "Bomba de Infusión Volumétrica Alaris",
        "description": "Sistema de administración de fluidos y medicamentos de alta precisión.",
        "specification": {
            "flowRate": "0.1-999 ml/hr",
            "accuracy": "±5%"
        },
        "maintenanceLogs": [
            {
                "date": "2024-02-05",
                "type": "Limpieza interna y test de flujo",
                "technician": "Laura Méndez"
            }
        ],
        "isOperational": true,
        "id": "4"
    },
    {
        "name": "Máquina de Anestesia Avance CS2",
        "description": "Estación de trabajo integrada para quirófanos de alta complejidad.",
        "specification": {
            "vaporizers": 2,
            "gasTypes": ["O2", "Air", "N2O"],
            "ventilator": "SmartVent"
        },
        "maintenanceLogs": [],
        "isOperational": true,
        "id": "5"
    }
]
```

---

### B. Creación de un nuevo registro (`POST`)

- **Endpoint:** `/medical-equipment`
- **Status Code:** `201 Created`
- **Cuerpo enviado en Postman:**

```json
{
    "name": "Electrocardiógrafo MAC 2000",
    "description": "Equipo de ECG de 12 derivaciones con análisis interpretativo.",
    "specification": {
        "channels": 12,
        "connectivity": "LAN/Wi-Fi",
        "storage": "200 ECGs"
    },
    "maintenanceLogs": [
        {
            "date": "2023-09-12",
            "type": "Reemplazo de cable de paciente",
            "technician": "Ing. Carlos Daza"
        }
    ],
    "isOperational": false
}
```

- **Respuesta de Postman:**

```json
{
    "name": "Electrocardiógrafo MAC 2000",
    "description": "Equipo de ECG de 12 derivaciones con análisis interpretativo.",
    "specification": {
        "channels": 12,
        "connectivity": "LAN/Wi-Fi",
        "storage": "200 ECGs"
    },
    "maintenanceLogs": [
        {
            "date": "2023-09-12",
            "type": "Reemplazo de cable de paciente",
            "technician": "Ing. Carlos Daza"
        }
    ],
    "isOperational": false,
    "id": "6"
}
```

---

### C. Búsqueda de registro individual (`GET`)

- **Endpoint:** `/medical-equipment/1`
- **Status Code:** `200 OK`
- **Respuesta de Postman:**

```json
{
    "name": "Monitor de Signos Vitales Dash 4000",
    "description": "Monitor multiparamétrico para cuidados intensivos y urgencias.",
    "specification": {
        "parameters": ["ECG", "SpO2", "NIBP", "Temp"],
        "screen": "10.4 inch LCD"
    },
    "maintenanceLogs": [
        {
            "date": "2024-01-15",
            "type": "Calibración anual",
            "technician": "Ing. Biomédico Ramos"
        }
    ],
    "isOperational": true,
    "id": "1"
}
```

---

### D. Actualización de un registro (`PUT`)

- **Endpoint:** `/medical-equipment/2`
- **Status Code:** `200 OK`
- **Modificación:** Se actualizó la fecha de mantenimiento del registro con `ID` 2 (de `2023-11-20` a `2023-08-15`).
- **Cuerpo enviado en Postman:**

```json
{
    "name": "Desfibrilador Externo Automático (DEA) G5",
    "description": "Dispositivo de respuesta rápida con instrucciones de voz.",
    "specification": {
        "energy": "Bifásica",
        "batteryLife": "4 years",
        "ipRating": "IP55"
    },
    "maintenanceLogs": [
        {
            "date": "2023-08-15",
            "type": "Cambio de parches/electrodos",
            "technician": "Soporte Técnico"
        }
    ],
    "isOperational": true
}
```

- **Respuesta de Postman:**

```json
{
    "name": "Desfibrilador Externo Automático (DEA) G5",
    "description": "Dispositivo de respuesta rápida con instrucciones de voz.",
    "specification": {
        "energy": "Bifásica",
        "batteryLife": "4 years",
        "ipRating": "IP55"
    },
    "maintenanceLogs": [
        {
            "date": "2023-08-15",
            "type": "Cambio de parches/electrodos",
            "technician": "Soporte Técnico"
        }
    ],
    "isOperational": true,
    "id": "2"
}
```

---

### E. Eliminación de un registro (`DELETE`)

- **Endpoint:** `/medical-equipment/2`
- **Status Code:** `200 OK`
- **Respuesta de Postman:**

```json
{
    "name": "Desfibrilador Externo Automático (DEA) G5",
    "description": "Dispositivo de respuesta rápida con instrucciones de voz.",
    "specification": {
        "energy": "Bifásica",
        "batteryLife": "4 years",
        "ipRating": "IP55"
    },
    "maintenanceLogs": [
        {
            "date": "2023-08-15",
            "type": "Cambio de parches/electrodos",
            "technician": "Soporte Técnico"
        }
    ],
    "isOperational": true,
    "id": "2"
}
```

---

### F. Validación de recurso inexistente (`GET`)

- **Endpoint:** `/medical-equipment/99`
- **Status Code:** `404 Not Found`
- **Respuesta de Postman:**

```json
"Not found"
```

---

## 3. Resumen de Endpoints y Códigos HTTP

| Acción       | Método | Endpoint               | Código HTTP   |
|--------------|--------|------------------------|---------------|
| Listar todo  | GET    | /medical-equipment     | 200 OK        |
| Crear        | POST   | /medical-equipment     | 201 Created   |
| Ver por ID   | GET    | /medical-equipment/1   | 200 OK        |
| Actualizar   | PUT    | /medical-equipment/2   | 200 OK        |
| Borrar       | DELETE | /medical-equipment/2   | 200 OK        |
| Error        | GET    | /medical-equipment/99  | 404 Not Found |
