# Ansible Demos

## Wildfly



## OpenScap 

### Manual Scanning

#### Paquetes a instalar

~~~
sudo yum install -y httpd openscap-scanner openscap-utils scap-security-guide

~~~

#### scap-security-guide
una vez instalados los paquetes, las guias de seguridad y politicas pueden ser encontradas en:

~~~
/usr/share/xml/scap/ssg/content
~~~

### Ansible Scanning

1. Poblar el inventario con los hosts destino
2. Tener acceso un un usuario privilegiado en este caso se usa root
3. Variables
    - scanns_home: ruta donde se almacenaran los escaneos en el hostcontroller
    - oscap_profile: Perfil de escaneo "PCI-DSS"
    - oscap_policy: Politica de escaneo con OS destino

- Ejecucion del playbook

~~~

ansible-playbook scap_scan.yml

~~~

- Ejecucion en Ansible Automation Platform

El playbook usa el modulo de fetch y guarda los escaneos en la ruta dada en la variable `scanns_home`, se debe de modificar los parametros para poder almacenar los archivos de forma local.

Modificar los parametros en AAP

Activar `Expose host paths for Container Groups`
Ajustes -> trabajos -> configuracion de las tareas 

- Añadir en `Ajustes -> trabajos -> configuracion de las tareas -> Rutas a exponer para los trabajos aislados` , el path donde se guardaran los escaneos 

- En el host cambiar el usuario y grupo a awx al path expuesto 
