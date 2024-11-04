EQUIPO 16 - VASQUEZ ARAGON ROBERTO CARLOS, VARGAS GOMEZ ALAN - CAPTCHA DE VERIFICACION

- Descarga del Proyecto: Primero, baja el archivo comprimido en formato ZIP desde el repositorio.

- Importar el Proyecto en NetBeans: Abre NetBeans, dirígete al menú "File" y selecciona "Import Project." Luego, elige "From ZIP...". Verás una ventana emergente; en el campo "ZIP File," haz clic en "Browse" y localiza el archivo ZIP descargado. Para finalizar, haz clic en "Import."

- Limpieza y Construcción del Proyecto: Una vez importado el proyecto, haz clic derecho sobre su nombre en el panel de proyectos y selecciona "Clean and Build." Este proceso generará un archivo .JAR. Para confirmar su ubicación, revisa el apartado "Output" en la parte inferior de NetBeans, y anota la ruta donde se guardó.

- Agregar el Componente a la Paleta: En NetBeans, ve al menú "Tools" y selecciona "Palette." A continuación, elige "Swing/AWT Components." En la ventana que se abrirá, selecciona "Add from JAR..." y localiza el archivo .JAR generado. Haz clic en "Next," selecciona el componente "Conectar" y luego nuevamente en "Next."

- Configurar la Paleta: Ahora, elige la categoría donde deseas que el nuevo componente aparezca en la Palette y haz clic en "Finish." Si todo se ha hecho correctamente, el componente debería estar visible en la sección "Palette" cuando crees un nuevo JForm.

- NOTA: Para un correcto funcinoamiento es necesario agregar a la libreria el archivo Absolute layout
  ![Imagen7](https://github.com/user-attachments/assets/eb949a33-f3ce-429c-aba6-4fbe8b0170e7)

	![Imagen6](https://github.com/user-attachments/assets/c92b9416-7f99-4d37-a367-c2aca99e143b)



PANORAMA GENERAL DEL CODIGO:
1.	Constructor de la Clase: El constructor Captcha() inicializa los componentes del formulario y oculta el elemento lblDone.
   
2.	Boton btnCambiarActionPerformed:
 - Cambia el panel actual (captcha visible) a uno aleatorio de la lista captchas.
 - Utiliza una estructura do-while para asegurarse de que el panel seleccionado sea diferente al actual.
 - Oculta el panel actual y muestra el panel seleccionado.
3.  Boton btnVerificarActionPerformed:
  - Verifica si el usuario ha seleccionado los botones correctos en el captcha.
  - Identifica cuatro botones (por ejemplo, button1, button6, button7, y button9 o dependiendo el panel) como los correctos.
  - Si solo están seleccionados estos botones correctos y no hay otros seleccionados, muestra un mensaje de éxito.
  - Si la selección es incorrecta, pide al usuario que lo intente nuevamente.
4. Boton chkVerificarActionPerformed:
  - Controla la acción del componente chkVerificar (por ejemplo, una casilla de verificación).
  - Al seleccionar chkVerificar, cambia la visibilidad de lblVerify y lblDone.
  - Inicia un temporizador de 2 segundos que oculta panelInicio y muestra panelMotocicletas1.
																									
FUNCIONAMIENTO DE LOS BOTONES

CASILLA PARA INICIAR EL CAPTCHA - Boton chkVerificarActionPerformed 

private void chkVerificarActionPerformed(java.awt.event.ActionEvent evt) { 

    if (chkVerificar.isSelected()) {
        // Oculta el lblVerify y muestra el lblDone
        lblVerify.setVisible(false);
        lblDone.setVisible(true);
        // Crea un temporizador para cambiar de panel después de 2 segundos
        Timer timer = new Timer(2000, new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                // Oculta el panelInicio y muestra el panelMotocicletas1
                panelInicio.setVisible(false);
                panelMotocicletas1.setVisible(true);
            }
        });
        // Configura el temporizador para que se ejecute solo una vez
        timer.setRepeats(false);
        timer.start(); // Inicia el temporizador
    }
    
}


Se activa cuando el usuario interactúa con una casilla de verificación (checkbox) llamada chkVerificar.
Análisis Detallado
1.	Evento ActionPerformed:
o	Se ejecuta cuando el usuario marca o desmarca la casilla chkVerificar.

2.	Condicional if (chkVerificar.isSelected()):
o	Verifica si la casilla está marcada. Si es así, se ejecuta el bloque de código dentro del if.

3.	Oculta y muestra etiquetas:
o	lblVerify.setVisible(false); : Oculta una etiqueta llamada lblVerify.
o	lblDone.setVisible(true); : Muestra una etiqueta llamada lblDone.
o	Esto sugiere que al marcar la casilla, se cambia visualmente el estado de la interfaz, posiblemente indicando que se ha realizado alguna verificación.

4.	Timer y cambio de paneles:
o	Se crea un Timer con un retraso de 2000 milisegundos (2 segundos).
o	El Timer ejecuta una tarea una sola vez (setRepeats(false)).
o	Al finalizar el tiempo, la tarea oculta el panel panelInicio y muestra el panel panelMotocicletas1.
o	Esto indica que después de marcar la casilla y esperar 2 segundos, la aplicación cambia a una nueva pantalla o sección.


![Imagen1](https://github.com/user-attachments/assets/0d06a04a-7b10-40d3-94b7-a9116d6a86ba)
![Imagen2](https://github.com/user-attachments/assets/fa4571be-51fe-4c83-8864-89f2b0d72774)


PANEL DE SELECCION - Boton btnVerificar4ActionPerformed

private void btnVerificar4ActionPerformed(java.awt.event.ActionEvent evt) {                                              

    // Definir los botones correctos
    JToggleButton[] correctButtons = { button38, button40, button43, button45 };
    
    // Listar todos los botones
    JToggleButton[] allButtons = { button37, button38, button39, button40, button41, button42, button43, button44, button45 };

    // Contar cuántos botones correctos están seleccionados
    int correctCount = 0;
    for (JToggleButton button : correctButtons) {
        if (button.isSelected()) {
            correctCount++;
        }
    }

    // Verificar si exactamente los 4 botones correctos están seleccionados
    if (correctCount == 4) {
        boolean onlyCorrectSelected = true;

        // Asegurarse de que no haya otros botones seleccionados
        for (JToggleButton button : allButtons) {
            if (button.isSelected() && !Arrays.asList(correctButtons).contains(button)) {
                onlyCorrectSelected = false;
                break;
            }
        }

        if (onlyCorrectSelected) {
            JOptionPane.showMessageDialog(null, "¡Felicidades, no eres un robot!");
            
            // Cerrar la ventana actual
            JFrame frame = (JFrame) SwingUtilities.getWindowAncestor(this);
            if (frame != null) {
                frame.dispose();
            }
        } else {
            JOptionPane.showMessageDialog(null, "Vuelve a intentarlo");
        }
    } else {
        JOptionPane.showMessageDialog(null, "Vuelve a intentarlo");
    }
}

1. Identificación de Botones Correctos:
    - Define una matriz correctSelections que contiene el estado de selección de cuatro botones específicos (button38, button40, button43, y button45).
    - Estos botones representan la combinación correcta que el usuario debe seleccionar para "pasar" el captcha.
  
2. Lista de Todos los Botones:
    - Define un arreglo allButtons que contiene todos los botones disponibles en el captcha, lo que permite realizar una verificación exhaustiva de la selección del usuario.

3. Contar Botones Correctamente Seleccionados:
    - Luego, itera sobre la matriz correctSelections para contar cuántos de los botones correctos están seleccionados.
    - El objetivo es asegurar que los cuatro botones correctos hayan sido seleccionados.

 4. Verificación Completa de Selección Correcta:
    - Primero, verifica si correctCount es igual a 4, es decir, que los cuatro botones correctos están seleccionados.
    - Luego, recorre todos los botones (allButtons) para asegurarse de que no haya ningún otro botón seleccionado que no sea uno de los cuatro correctos.
    - Si encuentra algún botón seleccionado que no esté en la lista correcta, establece onlyCorrectSelected como false y sale del bucle.

5. Mostrar Mensajes de Éxito o Error:
    - Si onlyCorrectSelected sigue siendo true, significa que el usuario seleccionó exactamente los cuatro botones correctos y no seleccionó ningún otro. En este caso, muestra un mensaje de éxito y cierra la ventana actual.
    - Si no, muestra un mensaje pidiendo al usuario que lo intente de nuevo.

6. Mensaje de Error General: 
    - Si correctCount no es igual a 4, muestra un mensaje de error, indicando al usuario que intente nuevamente.


![Imagen3](https://github.com/user-attachments/assets/a306c669-cb3a-4ddf-8e24-2b0eaf0c70db)
![Imagen4](https://github.com/user-attachments/assets/c04c0f66-9318-4aae-953a-5e8258a91183)


BOTON DE CAMBIAR EN LOS PANELES DE SELECCION - btnCambiar4ActionPerformed


private void btnCambiar4ActionPerformed(java.awt.event.ActionEvent evt) {

    JPanel[] captchas = {panelMotocicletas2, panelMotocicletas1, panelSemaforo2};
    JPanel currentPanel = panelSemaforo1; // Panel inicial
    // Ocultar el panel actual
    currentPanel.setVisible(false);
    // Seleccionar un panel aleatorio diferente al actual
    Random random = new Random();
    JPanel selectedPanel;
    do {
        int randomIndex = random.nextInt(captchas.length);
        selectedPanel = captchas[randomIndex];
    } while (selectedPanel == currentPanel); // Asegurarse de que sea diferente
    
    // Actualizar el panel actual y mostrar el nuevo panel seleccionado
    selectedPanel.setVisible(true);
    currentPanel = selectedPanel; // Actualizar el panel actual a este nuevo
    
}            

1. Definición de los Paneles de Captcha:
    - Se crea un arreglo captchas que contiene tres paneles (panelMotocicletas2, panelMotocicletas1, y panelSemaforo2). Estos representan los posibles paneles de captcha que pueden ser visibles en la interfaz.
  
2. Asignación del Panel Actual:
    - Define currentPanel como el panel que actualmente está visible, en este caso panelSemaforo1.
    - Este panel será ocultado antes de mostrar uno nuevo.

3. Ocultar el Panel Actual:
    - Oculta currentPanel estableciendo su visibilidad en false. Esto asegura que el panel actual se oculte antes de mostrar el siguiente panel.
  
4. Selección Aleatoria de un Panel Distinto al Actual:
    - Se inicializa un objeto Random para generar números aleatorios.
    - Un bucle do-while selecciona aleatoriamente un índice de captchas para escoger un selectedPanel.
    - Si el selectedPanel es igual a currentPanel, el bucle continúa hasta seleccionar un panel diferente.
    - Esto garantiza que el nuevo panel seleccionado no sea el mismo que el que estaba visible.

5. Mostrar el Nuevo Panel y Actualizar currentPanel:
    - Establece la visibilidad de selectedPanel en true, mostrando así el nuevo panel en la interfaz.
    - Actualiza currentPanel para que el nuevo panel se convierta en el "actual" para la próxima vez que se ejecute el método, permitiendo futuras rotaciones aleatorias.


![Imagen5](https://github.com/user-attachments/assets/f3cf218e-ea25-4c67-adc5-9ab0028d033a)

VIDEO DEL FUNCIONAMIENTO


https://github.com/user-attachments/assets/100dd021-0af7-4537-b76e-4fad7a75409b



