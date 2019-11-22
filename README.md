# challenge

Se requiere configuracion de dependencias en Ruby y YAML

Se requiere de instalar los roles de ansible de los siguentes links

* [elastic.elasticsearch](https://galaxy.ansible.com/elastic/elasticsearch/) para Elasticsearch
* [ashokc.logstash](https://galaxy.ansible.com/ashokrbconfigc/logstash/) para Logstash
*	[sansible.kibana](https://galaxy.ansible.com/sansible/kibana) para Kibana

Ejecutar 
vagrant up --no-provision

para hacer el levantamiento de las maquinas 

ejecutar para la instalacion de roles 
ansible-playbook -v -i inventory.yml elk.yml

Los nodos estan limitados a 10% de uso del procesador que en total hasta lo momentos seria el 30% de utilizacion de manera total 
se puede cambiar esta variable en la linea numero 11 del Vagrantfile

en el inventory.yml se encuentra el listado de activos en el cual se le puede modificar la cantidad de memoria a usar actualmente esta 
en 4 GiB en total con todos los nodos ejecutandose

en la linea numero 28 del Vagrantfile se encuentra habilitado el GUI para el provider de VM virtualbox, se puede comertar o elimnar esa linea para evitar el consumo masivo de maquina; se activo para check de la vida de las VM
 
