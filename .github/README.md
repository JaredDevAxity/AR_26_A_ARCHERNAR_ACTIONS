# REUZABLE WORKFLOWS

La reutilización de flujos de trabajo evita la duplicación. Esto hace que los flujos de trabajo sean más fáciles de mantener y le permite crear nuevos flujos de trabajo más rápidamente basándose en el trabajo de otros, tal como lo hace con las acciones. La reutilización de flujos de trabajo también promueve las mejores prácticas al ayudarle a utilizar flujos de trabajo que están bien diseñados, que ya han sido probados y cuya eficacia ha demostrado.

## Configurar workflow

Dependiendo del workflow que se implemente este requerirá pasarle parámetros para su correcto funcionamiento.

## Uso ALNILAM-Java

- `node-version`: La versión de Node que se va a configurar.
- `java-version`: La versión de Java que se va a configurar.
- `path-base`: Ruta base donde está ubicado el arquetipo Java.
- `name-service`: Nombre del servicio que fue creado por medio del generador.

## Configuración básica ALNILAM-Java

Dentro del repositorio del proyecto generar los siguientes **Secrets**:

- `SECRET MS_TEAMS_WEBHOOK_URI`: Secreto que hace referencia a la URL del chat de teams por donde se enviará los mensajes de estado del flujo de trabajo.
- `SECRET DOCKERHUB_USERNAME`: Secreto del nombre de la cuenta de dockerhub.
- `SECRET DOCKERHUB_TOKEN`: Token de la cuenta de dockerhub.

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
            path-base: '.'
            name-service: 'office'
        secrets: inherit

```
