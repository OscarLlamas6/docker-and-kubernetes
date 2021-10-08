# Introducción a Contenedores con Docker y Kubernetes


# Contenido 

- [Docker](#docker) 
- [Kubernetes](#kubernetes) 

# Docker

<div style="text-align: justify"><b> ¿Qué es un contenedor?</b></div><br/>  

• Es una unidad ejecutable de software  
• Encapsula todo lo necesario para ejecutarse.  
• Puede ser ejecutar en cualquier lado (Desktop, cloud, etc.)  
• Virtualización a nivel de sistema operativo.  
• Aisla procesos y controla los recursos asignados a esos procesos.  
• Pequeños, rápidos y portables 

<br/>
<div style="text-align: justify"><b> Casos de uso para contenedores </b></div><br/>

• Entornos cloud.  
• Aplicaciones de propósito general.  
• Cargas de trabajo.  
• Microservicios.  
• DevOps.
• Entornos híbridos y multi-cloud.

<br/>
<div style="text-align: justify"><b> ¿Qué es Docker? </b></div><br/>

• Plataforma de software para la creación y ejecución de contenedores.  
• Lanzada en 2013.  
• Comunidad open-source.  
• Docker CLI, es una herramienta de software para utilizar Docker con linea de comandos.

<br/>
<div style="text-align: justify"><b> Comandos Docker básicos </b></div><br/>

| Comando   |  Descripción    | 
|----------|:-------------:|
| build    |  Crea imagenes para contenedores a partir de un archivo (Dockerfile). | 
| run      |    Ejecuta un contenedor.   |  
| push     | Almacena una imagen a un registro de contenedores. (Ej. Dockerhub) |  
| pull     | Descarga una imagen desde un registro de contenedores. |

<br/>
<div style="text-align: justify"><b> Dockerfile e Imagenes Docker </b></div><br/>

• Un Dockerfile es un archivo de texto usado como plantilla con cada paso necesario para la construcción de imagenes Docker.  
• Una imagen es un archivo inmutable que contiene todo lo necesario para correr una aplicación.  
• Una imagen es una plantilla para contenedores.

---

# Kubernetes


<div style="text-align: justify"><b> Orquestación de contenedores </b></div><br/>

• Administra el ciclo de vida de los contendores.  
• Adecuado para entornos grandes y dinámicos.  
• Disponibilidad y escalabilidad.  
• Actualizaciones continuas.

<br/>
<div style="text-align: justify"><b> ¿Qué es Kubernetes? </b></div><br/>

<div style="text-align: justify"> Kubernetes es una plataforma portable y extensible de código abierto para administrar cargas de trabajo y servicios. Kubernetes facilita la automatización y la configuración declarativa. Tiene un ecosistema grande y en rápido crecimiento. El soporte, las herramientas y los servicios para Kubernetes están ampliamente disponibles. </div><br/>

<br/>
<div style="text-align: justify"><h2><b> Arquitectura de Kubernetes </b></h2></div><br/>

- Componentes de Kubernetes
<p align="center" >
  <img src="https://i.ibb.co/kx6bsx1/image.png" width="500" height="300" />
</p>


<br/>
<div style="text-align: justify"><h2><b> Kubernetes API Server </b></h2></div><br/>
<p align="center" >
  <img src="https://i.ibb.co/mbLTdD3/image.png" width="300" height="135" />
</p>

• Expone la API de Kubernetes.  
• Utilizada para todas las comunicaciones dentro del cluster.

<br/>
<div style="text-align: justify"><h2><b> etcd </b></h2></div><br/>
<p align="center" >
  <img src="https://i.ibb.co/MhVcRR7/image.png" width="160" height="175" />
</p>

• Almacenamiento de clave-valor de alta disponibilidad.  
• Contiene la información del cluster.  
• Fuente de confiabilidad para el estado en un clúster de Kubernetes.

<br/>
<div style="text-align: justify"><h2><b> Kubernetes scheduler</b></h2></div><br/>
<p align="center" >
  <img src="https://i.ibb.co/NjLKKJ5/image.png" width="300" height="150" />
</p>

• Asigna Pods recién creados a los Nodos.  
• Determina dónde deben ejecutarse las cargas de trabajo.

<br/>
<div style="text-align: justify"><h2><b> Kubernetes controller manager</b></h2></div><br/>
<p align="center" >
  <img src="https://i.ibb.co/LgbWCRP/image.png" width="300" height="150" />
</p>

• Ejecuta todos los procesos del controlador.  
• Los controladores monitorean el estado del clúster.  
• Los controladores garantizan que el estado real coincida con el estado deseado.

<br/>
<div style="text-align: justify"><h2><b> Cloud controller manager</b></h2></div><br/>
<p align="center" >
  <img src="https://i.ibb.co/4tB4tkr/image.png" width="300" height="150" />
</p>

• Ejecuta controladores que interactúan con proveedores de nube subyacentes.  
• Vincula los clústeres a la API de un proveedor de nube

<br/>
<div style="text-align: justify"><h2><b> Nodos </b></h2></div><br/>
<p align="center" >
  <img src="https://i.ibb.co/jwhsKT0/image.png" width="150" height="175" />
</p>

• Un nodo es una máquinas de trabajo en Kubernetes.  
• Puede ser una máquina física o virtual.
• Gestionado por el plano de control.  
• Contiene los servicios necesarios para ejecutar aplicaciones.

<br/>
<div style="text-align: justify"><h3><b> Kubelet </b></h3></div><br/>

• Se comunica con el servidor API de Kubernetes.  
• Se asegura de que los Pods y sus contenedores asociados se estén ejecutando.  
• Reporta al plano de control sobre el estado de los Pods.

<br/>
<div style="text-align: justify"><h3><b> Container runtime </b></h3></div><br/>

• Descarga imagens y ejecuta contenedores.  
• Kubernetes implementa una interfaz para que este componente sea conectable.

<br/>
<div style="text-align: justify"><h3><b> Kubernetes proxy </b></h3></div><br/>

• Proxy de red que se ejecuta en cada nodo de un clúster.  
• Mantiene las reglas de red que permiten la comunicación con los Pods que se ejecutan en los Nodos.

<br/>
<div style="text-align: justify"><h3><b> Controllers </b></h3></div><br/>

• Monitorea el estado de un cluster.  
• Toma medidas para asegurarse de que el estado real coincida con el estado deseado.  
• Se comunica con el API Server de Kubernetes para realizar dichas medidas.  
• Realuza un seguimiento de los objetos de Kubernetes y se asegura de que se logre el estado deseado.

<br/>
<div style="text-align: justify"><h2><b> Objetos en Kubernetes </b></h2></div><br/>

• Son entidades persistentes en Kubernete. Esto quiere decir que cuando creamos un objeto, Kubernetes se encargará continuamente de trabajar para asegurar que nuestro objeto exista en el sistema hasta que se modifique o se elimine dicho objeto.  
• Definen el estado deseado de la carga de trabajo (clúster).  
• Algunos ejemplo de objetos en Kubernetes son Pods, Namespaces, Deployments, Config Maps y Volumes.  
• Trabajan junto al API Server de Kubernetes mediante kubectl CLI o librerias.  

<br/>
<div style="text-align: justify"><h3><b> Partes pricipales de un objeto en Kubernetes </b></h3></div>


<div style="text-align: justify"><h4><b> - Especificación de objeto (Spec): </b></h4></div>

• Proporcionada por el usuario.  
• Establece el estado deseado para el objeto.  

<div style="text-align: justify"><h4><b> - Estado del objeto (Status): </b></h4></div>

• Proporcionada por Kubernetes.  
• Describe el estado actual del objeto.  
• El objetivo es que el estado deseado coincida con el estado actual.

<br/>
<div style="text-align: justify"><h3><b> Espacios de Nombre (Namespaces) </b></h3></div><br/>

• Virtualización de un clúster físico.  
• Distinción de clústers por grupo, proyecto, etc.  
• Proporcionar un ámbito para los nombres de los objetos.

- Namespaces en Kubernetes
<p align="center" >
  <img src="https://i.ibb.co/dbmXrZF/image.png" width="500" height="300" />
</p>

<br/>
<div style="text-align: justify"><h3><b> Nombres </b></h3></div><br/>

• Cada objeto tiene un nombre.  
• Los nombres son únicos para un tipo de recurso dentro de un espacio de nombres.  

- Nombres de objetos en Kubernetes
<p align="center" >
  <img src="https://i.ibb.co/SspkLjv/namespaces.png" width="500" height="300" />
</p>

<br/>
<div style="text-align: justify"><h3><b> Etiquetas (Labels) </b></h3></div>

• Proporciona atributos a un objeto sin especificar ninguna singularidad.  
• Pares llave-valor adjuntos a un objeto.  
• Destinados a la identificación de objetos.  
• No son únicos.  
• Usados para organizar y agrupar objectos en Kubernetes.

<br/>
<div style="text-align: justify"><h3><b> Selectores </b></h3></div>

• Identifican y agrupan un conjunto de objetos.

- Labels y selectores en Kubernetes.
<p align="center" >
  <img src="https://i.ibb.co/K70cx48/image.png" width="500" height="300" />
</p>