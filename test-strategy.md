<!--------------------->
<!-- CÓDIGO BRINDADO -->
<!--------------------->

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">

    <title>Juego de adivina tu número</title>

    <style>
      html {
        font-family: sans-serif;
      }
      body {
        width: 50%;
        max-width: 800px;
        min-width: 480px;
        margin: 0 auto;
      }
      .lastResult {
        color: white;
        padding: 3px;
      }
    </style>
  </head>

  <body>
      <h1>Juego Adivina tu número</h1>

      <p>Hemos seleccionado un número aleatorio entre 1 a 100. Trata de adivinar el número, en un total de 10 turnos o menos. No te preocupes, te diremos sí el número es más alto o más bajo </p>

<div class="form">
  <label for="guessField">Ingresa el número a adivinar: </label><input type="text" id="guessField" class="guessField">
  <input type="submit" value="Ingresar el número aleatorio" class="guessSubmit">
</div>

<div class="resultParas">
  <p class="guesses"></p>
  <p class="lastResult"></p>
  <p class="lowOrHi"></p>
</div>

</body>

<script>
  let randomNumber = Math.random() * 10;

  const ATTEMPS = 5;
  const guesses = document.querySelector('.guesses');
  const lastResult = document.querySelector('.lastResult');
  const lowOrHi = document.querySelector('lowOrHi');
  const guessSubmit = document.querySelector('.guessSubmit');
  const guessField = document.querySelector('.guessField');

  let guessCount = 1;
  let resetButton;

  function checkGuess() {

    let userGuess = guessField.value;
    if(guessCount === 1) {
      guesses.textContent = 'Número aleatorio anterior: ';
    }
    guesses.textContent += userGuess + ' ';

    if(userGuess === randomNumber) {
      lastResult.textContent = '!!!Pérdistes!!!';
      lastResult.style.backgroundColor = 'black';
      lowOrHi.textContent = '';
      setGameOver();
    } else if(guessCount === ATTEMPS) {
      lastResult.textContent = 'Felicitaciones! adivinaste el número!';
      lastResult.style.backgroundColor = 'red';
      setGameOver();
    } else {
      lastResult.textContent = 'Incorrecto! ';
      lastResult.style.backgroundColor = 'green';
      if(userGuess < randomNumber) {
        lowOrHi.textContent = 'El número es mayor!';
      } else if(userGuess > randomNumber) {
        lowOrHi.textContent = 'El número es menor!';
      }
    }

    guessCount++;
    guessField.value = '';
    guessField.focus();
  }
  guessSubmit.addeventListener('click', checkGuess);

  function setGameOver() {
	  guessField.disabled = true;
	  guessSubmit.disabled = true;
	  resetButton = document.createElement('button');
	  resetButton.textContent = 'Comienza un nuevo juego';
	  document.body.appendChild(resetButton);
	  resetButton.addeventListener('click', resetGame);
  }

  function resetGame() {
	  guessCount = 1;

	  const resetParas = document.querySelectorAll('.resultParas p');
	  for(let i = 0; i < resetParas.length; i++) {
		  resetParas[i].textContent = '';
	  }
	  resetButton.parentNode.removeChild(resetButton);

	  guessField.disabled = false;
	  guessSubmit.disabled = false;
	  guessField.value = '';
	  guessField.focus();

	  lastResult.style.backgroundColor = 'white';

	  randomNumber = Math.floor(Math.random()) + 1;
  }
</script>
</html>

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

    "SAqui agregue una parte de mi código personal donde, hace la función de validar si el numero ingresado es ENTERO o Decimal como en los 
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
