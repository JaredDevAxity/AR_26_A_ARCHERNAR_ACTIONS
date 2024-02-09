# REUZABLE WORKFLOWS

La reutilización de flujos de trabajo evita la duplicación. Esto hace que los flujos de trabajo sean más fáciles de mantener y le permite crear nuevos flujos de trabajo más rápidamente basándose en el trabajo de otros, tal como lo hace con las acciones. La reutilización de flujos de trabajo también promueve las mejores prácticas al ayudarle a utilizar flujos de trabajo que están bien diseñados, que ya han sido probados y cuya eficacia ha demostrado.

# Configurar workflow

Dependiendo del workflow que se implemente este requerirá pasarle parámetros para su correcto funcionamiento.

# Uso ALNILAM-Java

- `node-version`: La versión de Node que se va a configurar.
- `java-version`: La versión de Java que se va a configurar.
- `run-path`: Ruta base donde está ubicado el arquetipo Java.
- `name-service`: Nombre del servicio que fue creado por medio del generador.

## Configuración básica ALNILAM-Java

Dentro del repositorio del proyecto crear los siguientes **Secrets**:

- `SECRET MS_TEAMS_WEBHOOK_URI`: Secreto que hace referencia a la URL del chat de teams por donde se enviará los mensajes de estado del flujo de trabajo.
- `SECRET SONAR_PROJECT_KEY`: Secreto que contiene el nombre el nombre en sonarqube.
- `SECRET SONAR_HOST_URL`: Secreto con la URL del sonarqube.
- `SECRET sONAR_TOKEN`: Secreto con la información del token.
- `SECRET DOCKERHUB_TOKEN`: Token de la cuenta de dockerhub.

## Ejemplo de uso

Crear un archivo YML dentro de la siguiente ruta del proyecto ./.gitghub/workflows/<nombre_del_archivo>.yml

```
    name: Java SpringBoot CI
    run-name: Construyendo ALNILAM

    on:
    push:
        branches:
        - main

    jobs:
        ALNILAM:
            uses: JaredDevAxity/AR_26_A_ARCHERNAR_ACTIONS/.github/workflows/compileALNILAM.yml@main
            with:
                node-version: '18'
                java-version: '11'
                run-path: '.'
                name-service: 'office'
            secrets: inherit

```

> Si la carpeta donde se encuentra el arquetipo no esta en la raiz, la propiedad **run-path** sería algo como lo siguiente: **backend/** -> de está forma se haría referencia a donde el workflow trabajará.

# Uso MINTAKA-Net

- `node-version`: La versión de Node que se va a configurar.
- `run-path`: Ruta base donde está ubicado el arquetipo Net.

> Por defecto este arquitipo funcina con NetCore 6

## Configuración básica MINTAKA-Net

Dentro del repositorio del proyecto crear los siguientes **Secrets**:

- `SECRET MS_TEAMS_WEBHOOK_URI`: Secreto que hace referencia a la URL del chat de teams por donde se enviará los mensajes de estado del flujo de trabajo.
- `SECRET SONAR_PROJECT_KEY`: Secreto que contiene el nombre el nombre en sonarqube.
- `SECRET SONAR_HOST_URL`: Secreto con la URL del sonarqube.
- `SECRET SONAR_TOKEN`: Secreto con la información del token.

## Ejemplo de uso

Crear un archivo YML dentro de la siguiente ruta del proyecto ./.gitghub/workflows/<nombre_del_archivo>.yml

```
    name: NetCore CI
    run-name: Construyendo MINTAKA

    on:
    push:
        branches:
        - main

    jobs:
        ALNILAM:
            uses: JaredDevAxity/AR_26_A_ARCHERNAR_ACTIONS/.github/workflows/MINTAKA_Net.yml@main
            with:
                node-version: '20'
                run-path: '.'
            secrets: inherit

```

> Si la carpeta donde se encuentra el arquetipo no esta en la raiz, la propiedad **run-path** sería algo como lo siguiente: **backend/** -> de está forma se haría referencia a donde el workflow trabajará.
