# 🤖 Framework de Automatización de Pruebas — Matias De Arriba

Framework completo de testing automatizado desarrollado como Trabajo Final Integrador. Combina pruebas de UI con Selenium WebDriver, pruebas de API con Requests, patrón de diseño Page Object Model, y generación de reportes HTML con capturas de pantalla automáticas.

---

## 📋 Tabla de Contenidos

- [Propósito del Proyecto](#propósito-del-proyecto)
- [Tecnologías Utilizadas](#tecnologías-utilizadas)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [Instalación](#instalación)
- [Ejecución de Pruebas](#ejecución-de-pruebas)
- [Reportes](#reportes)
- [Casos de Prueba](#casos-de-prueba)

---

## 🎯 Propósito del Proyecto

Este proyecto implementa un framework de automatización de pruebas end-to-end que cubre:

- **Pruebas de UI**: automatización de flujos completos sobre [SauceDemo](https://www.saucedemo.com/) usando Selenium WebDriver con patrón POM
- **Pruebas de API**: validación de endpoints sobre [ReqRes](https://reqres.in/) usando la biblioteca Requests
- **Reportes visuales**: generación automática de reportes HTML con estado de cada test y capturas de pantalla en caso de fallo
- **Datos externos**: parametrización de tests mediante archivos CSV y JSON

---

## 🛠️ Tecnologías Utilizadas

| Tecnología | Versión | Uso |
|---|---|---|
| Python | 3.x | Lenguaje principal |
| Pytest | Latest | Framework de testing |
| Selenium WebDriver | 4.x | Automatización de UI |
| Requests | Latest | Pruebas de API |
| pytest-html | Latest | Reportes HTML |
| Git / GitHub | — | Control de versiones |

---

## 📁 Estructura del Proyecto

```
Proyecto-Final-Automation-Testing-Matias-De-Arriba/
│
├── page/                   # Page Objects (patrón POM)
│   ├── login_page.py       # Página de login
│   ├── inventory_page.py   # Página de productos
│   └── cart_page.py        # Página del carrito
│
├── tests/                  # Casos de prueba
│   ├── test_ui.py          # Tests de interfaz (Selenium)
│   └── test_api.py         # Tests de API (Requests)
│
├── utils/                  # Utilidades reutilizables
│   ├── data_reader.py      # Lectura de datos externos (CSV/JSON)
│   └── logger.py           # Configuración de logging
│
├── data/                   # Datos de prueba
│   ├── users.csv           # Credenciales de usuario
│   └── test_data.json      # Datos adicionales para tests
│
├── logs/                   # Archivos de log generados
│
├── reports/                # Reportes e imágenes generados
│   └── screenshots/        # Capturas automáticas en fallos
│
├── conftest.py             # Fixtures y hooks globales de Pytest
├── pytest.ini              # Configuración de Pytest
└── README.md               # Este archivo
```

---

## ⚙️ Instalación

### Requisitos previos

- Python 3.8 o superior
- Google Chrome instalado
- ChromeDriver compatible con tu versión de Chrome (o usar `webdriver-manager`)

### Pasos

**1. Clonar el repositorio**
```bash
git clone https://github.com/MatiasDeArriba/Proyecto-Final-Automation-Testing-Matias-De-Arriba.git
cd Proyecto-Final-Automation-Testing-Matias-De-Arriba
```

**2. Crear y activar entorno virtual** (recomendado)
```bash
python -m venv venv

# Windows
venv\Scripts\activate

# Linux / macOS
source venv/bin/activate
```

**3. Instalar dependencias**
```bash
pip install pytest selenium requests pytest-html
```

---

## ▶️ Ejecución de Pruebas

### Ejecutar todos los tests
```bash
pytest
```
Esto genera automáticamente el reporte en `report.html` según la configuración de `pytest.ini`.

### Ejecutar solo tests de UI
```bash
pytest tests/test_ui.py -v
```

### Ejecutar solo tests de API
```bash
pytest tests/test_api.py -v
```

### Ejecutar un test específico
```bash
pytest tests/test_ui.py::TestLogin::test_login_valido -v
```

---

## 📊 Reportes

### Reporte HTML

Al ejecutar `pytest`, se genera automáticamente el archivo `report.html` en la raíz del proyecto.

Para abrirlo:
```bash
# Windows
start report.html

# macOS
open report.html

# Linux
xdg-open report.html
```

El reporte muestra:
- Listado de todos los tests ejecutados
- Estado de cada test (PASSED / FAILED)
- Duración de ejecución
- Capturas de pantalla embebidas para los tests fallidos

### Capturas de Pantalla

Cuando un test de UI falla, el framework captura automáticamente una screenshot y la guarda en:

```
reports/screenshots/<nombre_del_test>.png
```

También queda embebida en el reporte HTML para consulta inmediata.

### Logs

Durante la ejecución se generan logs detallados en la carpeta `logs/`, útiles para depuración.

---

## 🧪 Casos de Prueba

### UI — SauceDemo (Selenium)

| # | Caso de Prueba | Tipo |
|---|---|---|
| 1 | Login con credenciales válidas | Positivo |
| 2 | Login con credenciales inválidas | Negativo |
| 3 | Navegación al inventario de productos | Positivo |
| 4 | Agregar producto al carrito | Positivo |
| 5 | Completar flujo de checkout | Positivo |

### API — ReqRes (Requests)

| # | Endpoint | Método | Validación |
|---|---|---|---|
| 1 | `/api/users` | GET | Status 200 + estructura JSON |
| 2 | `/api/users` | POST | Status 201 + datos creados |
| 3 | `/api/users/2` | DELETE | Status 204 |

---

## 👤 Autor

**Matias De Arriba**  
Trabajo Final Integrador — Curso de QA Automation
