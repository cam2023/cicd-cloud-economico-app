# Plan de Recursos Tecnológicos (PRT) - Proyecto 11: CI/CD Cloud Económico para Apps Web

## 1. Información General del Proyecto
* **Nombre del Proyecto:** CI/CD Cloud Económico para Aplicaciones Web con GitHub Actions y Hosting Gratuito.
* **Entidad Receptora:** Dirección Nacional de Servicios Digitales Educativos (DNSDE).
* **Repositorio Central:** [GitHub Repository](https://github.com/cam2023/cicd-cloud-economico-app)

---

## 2. Estructura de Ramas y Repositorio
El repositorio sigue un modelo de control de versiones basado en ramas (*GitFlow reducido*):
* `main`: Rama de producción para versiones estables desplegadas.
* `dev`: Rama de integración para pruebas y validación previa.
* `feature/*`: Ramas de desarrollo para nuevas funcionalidades.

Estructura de directorios establecida en el sistema:
* `/src`: Código fuente de la aplicación web.
* `/tests`: Pruebas automatizadas del sistema.
* `/ci`: Workflows y automatizaciones de integración continua.
* **`/infra`**: Configuraciones de infraestructura, hosting y despliegue (Responsabilidad de Ingeniería Cloud).
* `/docs`: Documentación técnica y bitácoras del proyecto.

---

## 3. Infraestructura y Hosting Seleccionado
Para cumplir con el propósito de una pipeline de bajo costo y alineada a recursos educativos limitados, se ha seleccionado la siguiente plataforma de infraestructura:

* **Plataforma Seleccionada:** Vercel / (Capa Gratuita / *Free Tier*).
* **Justificación Técnica:** 
  * Integración nativa y fluida con GitHub Actions para automatizar los despliegues posteriores a cada *commit* o *merge*.
  * Optimización para el despliegue rápido de aplicaciones web institucionales de la DNSDE sin incurrir en costos operativos.
  * Soporte para dominios públicos temporales o personalizados para pruebas de aceptación y *health checks*.
* **Limitaciones del Free Tier consideradas:**
  * Restricciones de ancho de banda y minutos de cómputo mensuales.
  * Gestión de latencia inicial (*cold starts*) en servicios desplegados como contenedores o lambdas.

---

## 4. Estrategia de Gestión de Secretos y Seguridad
Para garantizar la seguridad de la infraestructura y cumplir con los estándares profesionales:
* No se incluirán contraseñas, tokens (`DEPLOY_TOKEN`) o claves de API directamente en el código fuente (*hardcoding*).
* Se utilizará el sistema cifrado de **GitHub Secrets** para almacenar las credenciales sensibles que consumirá GitHub Actions durante las fases de compilación y despliegue.
* Las variables de entorno de ejecución pública se administrarán directamente desde el panel de control del proveedor de hosting en la nube.