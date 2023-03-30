<!---------------------------------------->
<!-- ERRORES ENCONTRADOS Y SOLUCIONADOS -->
<!---------------------------------------->

Linea 48:
Math.random() * 10;

    "Se encontraba mal escrito la función para que tire el numero aleatorio entre 1 y 100"
    "Cambio: Math.floor(Math.random() * 100) + 1;"

Linea 50:
const ATTEMPS = 5;

    "Se encontraba mal ingresado la cantidad de oportunidades que teníamos, ya que eran 10 y tenían escritas 5"
    "Cambio: const ATTEMPS = 10; "

Linea 53:
    const lowOrHi = document.querySelector('lowOrHi');

    "Se encontraba mal escrito la clase, porque debería llevar un punto (.) antes de la palabra."
    "Cambio: const lowOrHi = document.querySelector('.lowOrHi'); "

Linea 70:
    lastResult.style.backgroundColor = 'black';

    "Se encontraba mal ingresado el color que se solicita, ya que para PERDISTE se solicitaba el color ROJO y estaba con color NEGRO"
    "Cambio: lastResult.style.backgroundColor = 'red';"

Linea 75:
    lastResult.style.backgroundColor = 'red';

    "Se encontraba mal ingresado el color que se solicita, ya que para PERDISTE se solicitaba el color VERDE y estaba con color ROJO"
    "Cambio: lastResult.style.backgroundColor = 'green';"

Linea 79:
    lastResult.style.backgroundColor = 'green';

    "Se encontraba mal ingresado el color que se solicita, ya que para PERDISTE se solicitaba el color NEGRO y estaba con color VERDE"
    "Cambio: lastResult.style.backgroundColor = 'black';"

Linea 91:
    guessSubmit.addeventListener('click', checkGuess);

    "Se encontraba mal escrito lo que es el método addeventListener, ya que para que funcione tiene que llevar la mayúscula en Event"
    "Cambio: guessSubmit.addEventListener('click', checkGuess);"

Linea 99:
    resetButton.addeventListener('click', resetGame);

    "Se encontraba mal escrito lo que es el método addeventListener, ya que para que funcione tiene que llevar la mayúscula en Event"
    "Cambio: resetButton.addeventListener('click', resetGame);"


<!---------------------------------------------------------------------->
<!-- MEJORAS DE MI PERSONA, PARA EL FUNCIONAMIENTO Y MEJORAS VISUALES -->
<!---------------------------------------------------------------------->

Linea 66:
    guesses.textContent += userGuess + ' ';;

    "Quite la linea de código donde agregaba los numero ingresados, ya que mas abajo la volvería a agregar en otra función"

Linea 69:
    lastResult.textContent = '!!!Perdiste!!!';

    "Le agregue unas lineas de texto que cuando se pierde y sale el mensaje de PERDISTE se muestre cual era el numero random"
    "Cambio: lastResult.textContent = '!!!Perdiste!!! El número era ' + randomNumber + '.';"

Linea 86:

    "Aqui agregue una parte de mi código personal donde, hace la función de validar si el numero ingresado es ENTERO o Decimal como en los 
    CASOS DE USO, que decían en el GITHUB, donde tenia que salir una alarma que era numero decimal."
    
    
    // Validar si es un número entero
    if (Number.isInteger(Number(userGuess))) {
        guesses.textContent += userGuess + ', ';
      } 
      
      else {
        guessCount--;
        // El número ingresado no es un entero
        Swal.fire({
            icon: 'error',
            title: 'Por favor ingresa un número entero',
            text: 'Ingresaste el número '+ userGuess + ' y es un número decimal.',
          })
      }

    -> En el if hace la validación si el numero ingresado es entero.
        Si sí es entero el numero se agrega a la cola de texto donde se muestran los números ingresado, aquí es donde coloque la linea de código
        de la linea 66 que quite, donde solo se mostraran los números enteros ingresado.

    -> En el Else pues hice el llamado a lo que era sweetalert2, es una herramienta para hacer alertas emergentes pero con mejor estilo visual,
       donde el error que mostraba era si el numero ingresado era decimal, salia el error mostrando el mensaje con el numero ingresado.

       * NOTA: Al momento de ingresar un numero ENTERO se agrega lo que es la cola en userGuess y se le resta a los intentos hechos.
                Si se ingresara un numero decimal, sale la alerta y no se coloca ni en la cola de numero ingresado ni se sumaria a lo que son
                los intentos.
