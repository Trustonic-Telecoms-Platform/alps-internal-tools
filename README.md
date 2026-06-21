# alps-internal-tools (DLC Validator Summary)

Herramienta técnica interna automatizada para la validación y auditoría del componente Device Lock Controller (DLC v2), configuraciones de CarrierConfig y parámetros críticos de seguridad en dispositivos Android.

## 🔒 Propósito y Alcance Operativo
Este repositorio y sus herramientas son de **uso exclusivo y confidencial del personal técnico y de seguridad de Trustonic**. 

Su uso está estrictamente restringido a la homologación, soporte técnico y aseguramiento de calidad en operaciones de aliados estratégicos como **América Móvil (AMX)**. El objetivo principal es agilizar los tiempos de certificación técnica y validar de forma estandarizada que la implementación del ecosistema de bloqueo DLC y las directivas de red por parte de los fabricantes (OEMs) cumplan rigurosamente con los requisitos de integración y seguridad antes de su despliegue comercial.

---

## 🔍 Componentes del Repositorio

| Archivo | Descripción |
| :--- | :--- |
| `DLC_Validator_Summary.bat` | Lanzador local ligero ejecutado por el ingeniero en entornos Windows. |
| `dlc_validator_summary_remote.cmd` | Script maestro que contiene la lógica centralizada y actualizada de validaciones ADB. |

---

## ⚙️ Flujo de Operación y Automatización
La arquitectura del validador está diseñada para garantizar homogeneidad en las pruebas sin requerir actualizaciones manuales de software:

1. **Bootstrap dinámico:** El archivo local `DLC_Validator_Summary.bat` actúa como un micro-lanzador. Al ejecutarse, realiza una petición web segura para descargar la versión más reciente del script maestro `dlc_validator_summary_remote.cmd` directamente desde la rama principal.
2. **Validación agilizada:** Esto garantiza que todo el personal de ingeniería ejecute siempre las mismas plantillas de diagnóstico actualizadas en tiempo real, mitigando discrepancias de versiones en laboratorio.

---

## 🛠️ Requisitos de Ejecución
* **Sistema Operativo de Diagnóstico:** Windows 10 / Windows 11.
* **Dependencias:** Acceso a la terminal a través de PowerShell y presencia de `ADB Platform Tools` configuradas en las variables de entorno (`PATH`) del sistema.
* **Dispositivo Objetivo:** Terminal Android con la funcionalidad **Depuración USB** activa.
* **Red:** Conexión a Internet activa en la máquina de diagnóstico para permitir el aprovisionamiento dinámico del script maestro.

---

## 📋 Métricas y Diagnósticos Evaluados
Al finalizar el escaneo automatizado, la herramienta consolida la información técnica en un archivo local llamado `DLC_Validator_Report.txt`, el cual diagnostica de forma precisa:
* Presencia, firma e integridad del paquete Device Lock Controller (DLC v2).
* Correcta carga y persistencia de las variables XML de **CarrierConfig**.
* Estado operativo de servicios internos, tareas en segundo plano (`AppOps`) y persistencia ante reinicios.
* Diagnóstico de variables de hardware y firmware: Estado del cargador de arranque (Bootloader) y estados del *Verified Boot*.

---

## ⚠️ Confidencialidad y Restricciones Legales
Este proyecto constituye propiedad intelectual protegida de **TRUSTONIC**. Queda estrictamente prohibida la redistribución, copia, publicación o modificación parcial o total de estas herramientas sin el consentimiento y autorización expresa del equipo de Arquitectura de Seguridad. Las pruebas deben ejecutarse exclusivamente sobre dispositivos de prueba autorizados en entornos controlados de laboratorio.

*© 2026 TRUSTONIC. Todos los derechos reservados. Uso Interno Únicamente.*
