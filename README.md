# metrica-andina-reto
Proyecto para Metrica Andina

RETO TÉCNICO
============
 
Situación
=========
Se requiere implementar la funcionalidad SUMAR mediante un servicio REST, que consiste en:
1. Recibir sólo dos números y sumarlos. (ejemplo: http:///xxxxxxxx:yy/zzzzzz/sumar/10/20 )
2. Almacenar los números y el resultado en una base de datos.
3. Devolver un json como respuesta.
 
Arquitectura Solicitada
=======================
1. 01 nginx como puerta de entrada (reverse proxy)
2. 01 backend, en el lenguaje que tú escojas. (sug. java,node)
3. 01 base de datos, la que tú escojas (sug. postgres)
4. Contenedores (sug. Docker, Podman)
5. Una librería de log (log4j, slf4j, otra dependiendo del lenguaje escogido)
 
Problemática
============
1. Generar un bashero/yml que realice la compilación del backend de forma automática, ejecutando los test unitarios.
2. Generar un DockerFile, que permita construir el build de una imagen de Nginx como reverse-proxy.
3. Generar un DockerFile, que permita construir el build de una imagen con en backend.
4. Generar un DockerFile, que permita construir el build de una imagen personalizada con la base de datos.
5. Generar un bashero/yml que realice la construcción automática de las imágenes mediante los archivos DockerFile respectivos.
6. Generar un bashero/yml que permita ejecutar las imágenes de Nginx y el Backend conectando 
    a) Nginx ---> Backend ----> Base Datos
7. Continuous Integration  : Realizar el despliegue mediante un toolchain de ALM por ejemplo Github/Gitlab/Bitbucket + Jenkins/Bamboo + Sonarqube
8. Continuous Delivery     : Implementar Docker Registry en local o Cloud Provider (AWS, Azure, GCP, Ibm Cloud, Ali Cloud) para las imágenes de docker, Artifactory, Nexus Sonatype
8. Continuous Deployment   : Realizar un Pipeline (Jenkins, vía código) / Plan (vía código *Bamboo Specs*) para el deploy automático
9. ChatOps - Al construir correctamente o presentarse error el pipeline/plan debe enviar un mensaje a un grupo de Telegram/Slack creado para informar sobre los builds del proyecto. Al momento de la prueba agregaremos un número/email para comprobar la configuración.
10. AgileOps: Integrar el stack ELK o Graylog+Grafana a la solución, mostrando un "Visualization"/"Dashboard" con la cantidad de peticiones por minuto.
11. SRE: Integrar una tool de monitoreo de contenedores (por ejemplo: Portainer) a la solución.
 
Consideraciones
===============
1. Subir los archivos solicitados a Github/Gitlab/Bitbucket en un repositorio en modo público, de manera que todos los archivos puedan ser descargados para su revisión.
2. Considerar al menos un test unitario para el backend.
3. Considerar el build automático del backend mediante un gestor de dependencias (maven, gradle, etc...)
4. Para la base de datos, considerar solo una tabla simple (sumando01, sumando02, resultado)
5. Considerar la cláusula HEALTCHECK dentro del Dockerfile del backend
6. En caso tuvieras problemas con la instalación de docker puedes usar: "https://labs.play-with-docker.com" y recuerda guardar los archivos en tu propio repositorio
7. En caso usaras kubernetes, puedes usar "https://labs.play-with-k8s.com" y recuerda guardar los archivos en tu propio repositorio
 
Sugerencias
===========
1. Puedes usar Springboot o Micronaut.io, con los cuales tendrás el backend en custión de minutos.
2. En caso algún punto te resulte complicado puedes avanzar con los demás.
3. El Backend debe poder ser multiréplicas, ten cuidado de no exponer el puerto como external.
 
Plus (Opcional)
===============
Puedes añadir cualquiera de los siguientes puntos:
1. Realizar el aprovisionamiento de la infraestructura mediante código: Ansible, CloudFormation, Terraform, Cheff, Puppet (otro)
2. Realizar el despliegue sobre Kubernetes, Docker Swarm, Openshift
3. Implementar Idempotencia del servicio: Buscar si dos números ya fueron sumados previamente en la bd y devolver el resultado de la BD (verbo PUT)
4. Incluir integración con JMeter para realizar pruebas de estrés al backend.
5. Crear una cuenta trial en Microfocus e integrar al ALM Fortify SCA.
6. Crear una cuenta trial en Blazemeters/Saucelabs e integrar al ALM las pruebas de estrés.
7. Realizar el auto tag del respositorio, en caso la construcción (CDelivery) sea exitoso.
8. Realizar el auto incremento de la versión en el archivo de propiedades correspondiente (json, pom.xml, etc) y realizar el push de ese cambio.
9. Integrar configuraciones en cortocircuito, al backend. Por ejemplo si el CodeCoverage es menor del 70% el pipeline debe abortar.
10. Integrar tests mediante el lenguaje Gherkins (Scenario, features) y mostrar resultados en la tool de IC (Por ejemplo Plugin Serenity BDD)
 
Quedo al pendiente ante cualquier duda, confío en que tendrás éxito en el mismo.
 
Saludos.
