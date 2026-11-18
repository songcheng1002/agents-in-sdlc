---
title: "Lección 12 - Desplegar el sitio con GitHub Pages"
description: "Usa la aplicación GitHub Copilot para configurar un flujo de trabajo de Pages, revisar su pull request y verificar que Space Quiz está disponible."
authors:
  - jamesmontemagno
lastUpdated: 2026-10-12
---

Publica Space Quiz en GitHub Pages para que todo el mundo pueda acceder. Copilot puede preparar el flujo de trabajo y guiarte durante el despliegue, pero tú eres responsable de revisar los cambios y confirmar que el sitio está disponible.

En esta lección:

- pedirás a Copilot que configure un despliegue en GitHub Pages.
- revisarás el flujo de trabajo y el pull request antes de fusionarlo.
- seguirás el despliegue y verificarás el sitio publicado.

## Escenario

Space Quiz ya está en un repositorio de GitHub, pero aún hace falta una forma sencilla de probarlo. Publicar el sitio de un solo archivo con GitHub Pages permite acceder a él desde una URL pública sin añadir un servidor ni una dependencia del entorno de ejecución.

## Pide a Copilot que prepare el despliegue

> [!WARNING]
> Crear un pull request puede confirmar y subir código. Revisa la configuración de aprobación y el repositorio de destino antes de enviar este prompt. Si está seleccionada la opción **Approve all**, no esperes otro mensaje de confirmación.

En la sesión de la aplicación Copilot para `space-quiz`, envía este prompt:

```plaintext
Prepara un despliegue en GitHub Pages para este repositorio. Crea un flujo de trabajo de GitHub Actions que compile el sitio web si es necesario y lo despliegue en GitHub Pages cuando los cambios lleguen a la rama predeterminada. Añade un README que describa la aplicación y cómo ejecutarla en local si aún no existe. Crea un pull request con estos cambios e indica su enlace y cualquier configuración o permiso de Pages necesario. No lo fusiones, no habilites la fusión automática, no cambies la configuración de Pages ni despliegues el sitio. Detente y espera a que lo revise.
```

## Revisa el flujo de trabajo y el pull request

1. Confirma que el README solo se añade si el repositorio aún no tiene uno.
2. Revisa los cambios del pull request, incluidos los pasos de compilación y despliegue, los desencadenadores y los permisos del flujo de trabajo.
3. Confirma que el flujo de trabajo despliega desde la rama predeterminada, no desde un pull request que aún no se ha fusionado.
4. Solicita las correcciones necesarias y revisa el diff actualizado. Espera a que se superen las comprobaciones obligatorias del pull request antes de autorizar la fusión.

## Autoriza la fusión y el despliegue

> [!WARNING]
> El siguiente prompt autoriza al agente a fusionar el pull request revisado, cambiar la configuración de Pages del repositorio y publicar el sitio. Envíalo solo después de revisar los cambios y confirmar el repositorio y el pull request. Según la configuración de aprobación, estas acciones podrían realizarse sin otro mensaje de confirmación.

Sustituye `<PR_NUMBER>` por el número del pull request que has revisado y envía este prompt por separado:

```plaintext
He revisado el pull request <PR_NUMBER> de este repositorio y autorizo su fusión y despliegue. Habilita GitHub Pages mediante GitHub Actions, fusiona ese pull request solo cuando se superen las comprobaciones obligatorias y supervisa el despliegue hasta que se complete correctamente. Indica la URL final del sitio publicado. Si no tienes permiso para habilitar Pages o fusionar, dime exactamente qué debo aprobar o hacer; no informes de que se ha completado correctamente hasta que el sitio esté publicado.
```

![Diagrama de tres etapas: un pull request de space-quiz fusionado; una ejecución correcta de GitHub Actions Deploy website con los pasos Build website, Upload artifact y Deploy to Pages; y Space Quiz disponible en yourname.github.io/space-quiz/.](../../../_images/first-steps-app-pages-deploy.svg)

## Verifica el despliegue

1. Sigue la ejecución del despliegue de GitHub Actions hasta que se complete correctamente.
2. Abre la URL indicada y confirma que Space Quiz se carga.

Si el agente no puede habilitar Pages o fusionar el pull request, sigue las instrucciones concretas que te proporcione. No des la tarea por terminada hasta que el despliegue se complete correctamente y el sitio esté disponible.

## Resumen y siguientes pasos

Space Quiz ya está disponible como sitio web y has verificado el despliegue en lugar de confiar únicamente en el informe del agente. Continúa con [Lección 13: Revisión y siguientes pasos][next-lesson].

[next-lesson]: ../13-review/
