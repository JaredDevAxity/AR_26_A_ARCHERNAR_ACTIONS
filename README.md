# ARCHERNAR

ARCHERNAR es un repositorio creado para proveer **GITHUB Actions**, estos fueron creados y configurados para facilitar su implementación en repositorios externos.

## Requisitos

- SECRET SONAR_TOKEN
- SECRET SONAR_URL
- SECRET MS_TEAMS_WEBHOOK_URI

## Uso de los GITHUB ACTIONS

Crear un directorio como se muestra en la siguiente imagen.

![Audience](/assets/dirAction.png)

Navega hasta la carpeta workflows y crea un archivo <nombre_archivo.yml>

![Audience](/assets/fileName.png)

Dentro del archivo, crear el código base para la implementación del Action como se muestra a continuación:

```
name: Angular CI
run-name: Construyendo TITAN

on:
  pull_request:
    types: [opened, synchronize]

jobs:
  Build-TITAN:
    uses: JaredDevAxity/AR_26_A_ARCHERNAR_ACTIONS/.github/workflows/compileTitan.yml@main
    with:
      node-version: '16'
      projectKey: 'Test_CREA_Sonar_Archernar'
    secrets: inherit
```

En la línea uses hacer referencia al **Action** a utilizar.

![Audience](/assets/actionName.png)

Puede consultar el archivo para saber que parámetros son requeridos para su correcto funcionamiento.
En el caso anterior usa el archivo compileTitan.yml, este archivo requiere de dos parametros:

- node-version
- projectKey -> Esté es el nombre del proyecto en SonarQube

![Audience](/assets/reuzableAction.png)

## Crear Incoming Webhooks

Como requisito se pide una URL que haga referencia al canal de teams por donde llegará el mensaje de éxito o si ocurrió un error en el GITHUB Action implementado.

1. Abra el canal en el que desea agregar el webhook y seleccione +.

![Audience](/assets/crearWebhooks.png)

2. Seleccione Obtener más aplicaciones.

![Audience](/assets/obtenerWebhook.png)

3. Buscar por **Incoming Webhook** y seleccionar **Agregar**.

![Audience](/assets/agregarIncomingWebhook.png)

4. Seleccione **Agregar a un equipo**, busque el canal al que desea agregarlo y de clic en **Configurar un connector**.

![Audience](/assets/agregarWebhookEquipo.png)

5. Agregue un nombre al Incoming Webhook y seleccione **Crear**.

![Audience](/assets/configurarWebhook.png)

6. Se le proporcionará una URL, guarde este misma en algun archivo o en el portapapeles. La URL proporcionada se tiene que guardar en los **secretos** del repositorio y seleccione **Listo**.

![Audience](/assets/finalizarWebhook.png)

Para comprobar que fue agregado correctamente el Incoming Webhook en el canal debe de mostrarse el siguiente mensaje:

![Audience](/assets/comprobarWebhook.png)
