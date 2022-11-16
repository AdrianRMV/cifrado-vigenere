<script>
    const alphabet = ['A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z'];

    const message = "HELLO"; 
    const key = "LOLLA";


    const key_array = [...key]; // ['L', 'O', 'L', 'L', 'A']
    const message_array = [...message]; // ['H', 'E', 'L', 'L', 'O']

    const message_number = []; // Arreglo donde iran los numeros de las posiciones de la letra en el alfabeto
    const key_number = []; // Arreglo donde iran los numeros de las posiciones de la letra en el alfabeto | Ejemplo: (7, 11, 12, 20) |
    const suma_mensaje_clases = [];

    message_array.forEach((elemento)=>{
        message_number.push(alphabet.indexOf(elemento))
    });

    key_array.forEach((elemento)=>{
        key_number.push(alphabet.indexOf(elemento))
    });

    console.log(message_number);
    console.log(key_number);

    // Ciclo que recorrera el largo del arreglo de la llave, 
    // para asi saber exactamente el numero de caracteres que tiene, tanto nuestro mensaje como nuestra llave
    for (let index = 0; index < key_number.length; index++) {
        // Variable que alamacena el valor que tenga el arreglo de llave en la posicion actual del ciclo
        const element = key_number[index];

        // Variable que alamacena el valor que tenga el arreglo de mensaje en la posicion actual del ciclo
        const element2 = message_number[index];

        // Variable que suma los dos elementos y los empuja a un arreglo nuevo
        const sum = element + element2;

        suma_mensaje_clases.push(sum)
    }

    

</script>

<main>

</main>
