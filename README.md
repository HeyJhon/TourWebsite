# Hello Tour
Con la ayuda de la biblioteca Annojs podemos generar una visita guiada o tour para nuestros sitios web, de esta manera le indicamos a nuestros usuarios el step by step de la aplicación.

Documentación completa de Annojs: http://iamdanfox.github.io/anno.js/

1.- Importa a tus referencias  anno.js, anno.css y jquery.

NOTA: El script anno.js que viene adjunto se modificó para que al final del tour te de la opción de no volver a mostrar los mensajes, el script de la pagina originalmente no te da esta opción.

2.- Para usarlo solo hay que crear una instancia de tipo Anno con un array de propiedades para cada step que vamos a mostrar.

  var tour = new Anno([{
                    target: '#txtBuscar',
                    position: 'center-right',
                    content: "Te presentamos el campo de Busqueda.",
                    buttons: [AnnoButton.NextButton]
                },
                {
                    target: '#txtBuscar',
                    position: 'center-right',
                    content: "Comienza a buscar",
                    buttons: [AnnoButton.BackButton, AnnoButton.DoneButton, AnnoButton.NotAgainButton]
                }])
		
NOTA: AnnoButton.NotAgainButton es un botón personalizado que no existe originalmente en la biblioteca, con este logramos que no se vuelva a mostrar nunca más el tour.

3.- La  variable tourName se crea y se almacena en el localStorage del navegador en el momento que se le dé clic al botón No volver a mostrar. Mientras esa variable sea null seguiremos mostrando el tour.

$(document).ready(function () {                
				tourName = "tourCatalogo";
                    if (localStorage.getItem(tourName) == null) {
                        tour.show();
                    }
                });
		
NOTA: Para cada tour se recomienda asignar a tourName un nombre único para poder controlar el no volver a mostrar.
