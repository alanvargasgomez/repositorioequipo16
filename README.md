EQUIPO 16 - VASQUEZ ARAGON ROBERTO CARLOS, VARGAS GOMEZ ALAN - CAPTCHA DE VERIFICACION

Descripción General del Proyecto

Este proyecto es un sistema CAPTCHA hecho en Java que usa una serie de ventanas (JFrame) para desafiar al usuario con diferentes pruebas visuales. El objetivo es asegurar que el usuario es un humano y no un robot. Cada prueba pide al usuario seleccionar imágenes que cumplen con una categoría específica, como “motos” o “semáforos”. Si el usuario acierta, se le permite pasar; si no, debe intentarlo de nuevo.

Estructura del Proyecto

	1.	Clases de CAPTCHA:
	•	CaptchaMoto y CaptchaMoto2: Estas clases representan pruebas donde el usuario tiene que identificar imágenes de motos. Cada clase puede tener un diseño de interfaz o un conjunto de imágenes diferente.
	•	CaptchaSemaforo y CaptchaSemaforo2: Estas clases son similares a las de motos, pero en este caso el usuario debe seleccionar imágenes de semáforos.
	2.	Clase Principal (Principal.java):
	•	Es la ventana inicial que se abre cuando ejecutas el programa.
	•	Tiene un checkbox de verificación (chkVerificar). Al seleccionarlo, el sistema espera un par de segundos y luego abre una de las ventanas de CAPTCHA (por ejemplo, CaptchaMoto o CaptchaSemaforo), donde el usuario debe realizar la selección de imágenes correcta.
	3.	Recursos de Imágenes:
	•	En las carpetas motos y semaforos, se almacenan imágenes correspondientes a cada categoría.
	•	Estas imágenes son las que se muestran en las ventanas de CAPTCHA, y el usuario debe elegir las que cumplen con la categoría indicada.

Cómo Funciona el Sistema CAPTCHA

	1.	Ventana Inicial (Principal.java):
	•	Al abrir el programa, se muestra la ventana principal con el checkbox de verificación.
	•	Cuando el usuario marca el checkbox, el programa oculta la imagen inicial y, después de un breve retraso, abre una ventana de prueba CAPTCHA (por ejemplo, CaptchaMoto).
	2.	Ventanas de Prueba (CaptchaMoto, CaptchaMoto2, CaptchaSemaforo, CaptchaSemaforo2):
	•	Cada ventana muestra una cuadrícula de imágenes (por ejemplo, 3x3).
	•	El usuario debe seleccionar las imágenes que corresponden a la categoría indicada, como “motos” o “semáforos”.
	•	Cuando el usuario hace clic en el botón de verificación, el programa verifica si la selección es correcta:
	•	Si es correcta: Muestra un mensaje que dice “¡Felicidades, no eres un robot!” y permite continuar.
	•	Si es incorrecta: Informa al usuario y le permite intentar nuevamente.

Flujo de Uso

	1.	El usuario abre el programa y ve la ventana principal con un checkbox de verificación.
	2.	Marca el checkbox, lo cual oculta la primera imagen y muestra una segunda imagen de verificación.
	3.	Después de 2 segundos, se abre una ventana de prueba CAPTCHA donde debe seleccionar imágenes que cumplan con la categoría indicada.
	4.	Verificación:
	•	El usuario selecciona las imágenes que cree correctas y hace clic en el botón de verificación.
	•	El programa revisa la selección:
	•	Si está bien, muestra un mensaje de éxito.
	•	Si está mal, le pide que intente de nuevo.

Objetivo y Uso

Este sistema CAPTCHA tiene como objetivo asegurarse de que el usuario es humano mediante pruebas visuales. Es un proyecto ideal para quienes buscan aprender sobre:

	•	La creación de interfaces gráficas en Java con Swing.
	•	El manejo de eventos de usuario (como clics en checkbox y botones).
	•	La carga y manipulación de imágenes en Java.
