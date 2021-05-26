# Ansible Role: app_iiq
Ansible role to deploy IIQ with a Docker container

## Requirements

You must have Docker installed and configured to deploy IdentityIQ.  You also must have an instance of MySQL available for IdentityIQ to connect to.  We recommend using the role db_iiq_mysql, but any MySQL instance may be used.


## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    tomcat_log_volume_name: sandbox_iiq_tomcat_logs

Name of the docker volume for the tomcat logs.  Usually overriden in the format of <company name>_iiq_tomcat_logs

    tomcat_work_volume_name: sandbox_iiq_tomcat_work

Name of the docker volume for the tomcat work directory.  Usually overriden in the format of <company name>_iiq_tomcat_work

    tomcat_catalina_volume_name: sandbox_iiq_tomcat_catalina

Name of the dockder volume for the catalina volume.  Usually overriden in the format of <company name>_iiq_tomcat_catalina

    tomcat_temp_volume_name: sandbox_iiq_tomcat_temp

Name of the docker network to attach the generated containers to.  Usually overriden in the format of <company name>_iiq

    docker_build_context: ../

Location of the Docker build context.

    iiq_image_name: sandbox-iiq

Name of the docker image to build.  Usually overriden in the format of <company name>-iiq

    iiq_container_name: sandbox-iiq

Name of the generated docker container.  Usually overriden in the format of <company name>-iiq

    iiq_app_port: 8080

Exposed port for the IIQ Tomcat application.  

    iiq_data_dir : '{{ playbook_dir }}/iiqdata'

Folder location of the iiqdata directory to connect to the container

    java_opts: -Xmx2048m -Xms2048m -XX:+UseG1GC -Dsailpoint.debugPages=true -Duser.timezone=UTC

Java options for the Tomcat instance

    rebuild: false

Flag to determine if the docker image should be rebuilt.

    start_app: true

Flag to determine if the IIQ application should be started.  Useful if there are other orchestration activities to perform before starting the application.

    orchestrate: true

Flag to determine if orchastration activities should take place.  Useful if the role was initially ran with start_app false and now the app needs to be started

    deploy_ap: true 

Flag to determine if the accelerator pack is being installed.  

## Dependencies

None.

