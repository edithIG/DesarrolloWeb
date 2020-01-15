# Desarrollo Web

¿A donde van los datos?
Se explicara que sucede con los datos cuando se envia un formulario


# Arquitectura cliente/servidor
La web se basa en una arquitectura cliente/servidor:
* Cliente: Generalmente un navegador web(Envia una solicitud a un servidor(APACHE,TOMCAT...) utilizando un protocolo HTTP)
* El servidor: Responde a la solicitud utilizando el mismo protocolo

En el lado del cliente un formulario HTML no es mas que una forma conveniente y facil de usar para configurar una solicitud HTTP para enviar datos a un servidor.Esto permite al usuario proporcionar informacion que se entregara en la solicitud HTTP.

# En el lado del cliente:definir como enviar los datos

El <form> elemento que define como se enviaran los datos.Todos sus atributos estan diseñados para permitirle configurar la solicitud que se enviara cuando un usuario presione un boton de envio. Los dos atributos mas importantes son action y method.
  
* El action: Define donde se envían los datos.Su valor debe ser URL relativa o absoluta válida. Si no se proporciona este atributo, los datos se enviaran a la URL de la pagina que contiene el formulario; La pagina actual.

EJEMPLOS:

* En este ejemplo, los datos se envían a una URL absoluta https://example.com

<form action ="https://example.com">

* Aqui, usamos una URL relativa: los datos se envían a una URL diferente en el servidor.

<form action="/somewhere_else">
  
* Cuando se especifica sin atributos, como se muestra a continuacion, los <form> datos se envian a la misma pagina en la que esta presente el formulario.

<form>
  
* Muchas paginas antiguas usan la siguiente notacion para indicar que los datos deben enviarse a la misma pagina que conteine el formulario; esto era necesario porque hasta HTML5, el *action 
atributo era obligatorio.Esto ya no es necesario.

<form action="#">
  
Los nombres y valores de los controles de formulario sin archivo se envian al servidor como name=value pares unidos con simbolos de union.El *action* valor debe ser un archivo en el servidor que pueda manejar los datos entrantes, lo que incluye garantizar la validacion del lado del servidor. El servidor luego responde, generalmente manejando los datos y cargando la URL definida por el *action* atributo.


# El method atributo

El *method* define como se envian los datos. El protocolo HTTP proporciona varias formas de realizar una solicitud; Los datos de formulario HTML se pueden transmitir a traves de diferentes formas.

Los metodos de solicitud HTTP mas comunes son el *GET* metodo y *post* metodo.

Para comprender la diferencia entre esos dos métodos.Retrocedamos y examinemos como funciona HTTP. Cada vez que desea acceder a un recurso en la web, el navegador envia una solicitud a una URL. Una solicitud HTTP consta de dos partes: un *encabezado* que contiene un conjunto de metadatos globales sobre las capacidades del navegador y un cuerpo que puede contener la informacion necesaria para que el servidor procese la solicitud especifica.


* El metodo GET
El get es el metodo utilizado por el navegador para pedirle al servidor que envie un recurso dado: "Hola servidor, quiero obtner este recurso". En este caso, el navegador envia un cuerpo vacio. Debido a que el cuerpo esta vacio, si se envia un formulario utilizando este metodo, los datos enviados al servidor se agrgan a la URL.


* El metodo POST
El metodo es un poco diferente. Es el método que utiliza al navegador para comunicarse con el servidor cuando solicita una respuesta que tenga en cuenta los datos proporcionados en el cuerpo de la solicitud HTTP : "Hola servidor, eche un vistazo a estos datos y enviame un resultado apropiado". Si se envia un formulario utlizando este metodo, los datos se agrega al cuerpo de la solicitud HTTP

# Ver solicitudes HTTP
Las solicitudes HTTP nunca se muestran al usuario( si desea verlas, debe usar herramientas(Chrome Developer Tools)

Lo unico que se muestra al usuario es la URL llamda. Como se menciono anteriormente con una solicitud GET el usuario vera los datos en su barra de URL, pero con una solicitud POST no lo hara, esto es importante por dos razones:

* Si necesita enviar una contraseña (o cualquier otro dato confidencial), nunca use el GETmétodo o corre el riesgo de mostrarlo en la barra de URL, lo cual sería muy inseguro.

* Si necesita enviar una gran cantidad de datos, POSTse prefiere el método porque algunos navegadores limitan el tamaño de las URL. Además, muchos servidores limitan la longitud de las URL que aceptan.

# En el lado del servidor: recuperar los datos
Cualquiera que sea el metodo HTTP que se elija, el servidor recibe una cadena que se analizara para obtener los datos como una lista de pares claves / valor. La forma en que accede a esta lista depedende de la plataforma de desarrollo que use y delos marcos especificos que pueda estar usando.

# Enviar archivos
Enviar archivos con formularios HTML es un caso especial. Los archivos son datos binarios o se consideran como tales, mientras que todos los demas datos son datos de texto. Debido a que HTTP es un prtocolo de texto, existen requisitos especiales para manejar datos binarios.

https://developer.mozilla.org/en-US/docs/Learn/Forms/Sending_and_retrieving_form_data




  
  
