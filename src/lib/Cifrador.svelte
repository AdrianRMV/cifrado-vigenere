<script>
    let visible = false;
    let desifrado = false;

    const alphabet = [
        'A',
        'B',
        'C',
        'D',
        'E',
        'F',
        'G',
        'H',
        'I',
        'J',
        'K',
        'L',
        'M',
        'N',
        'O',
        'P',
        'Q',
        'R',
        'S',
        'T',
        'U',
        'V',
        'W',
        'X',
        'Y',
        'Z',
    ];

    let message = '';
    let messageDesifrado = '';

    let key = '';
    let key_array_numbers = [];

    let cifrado = '';
    let cifrado_array_numbers = [];

    function cifrarVigenere() {
        let message_array = [...message.toUpperCase()]; // ['H', 'E', 'L', 'L', 'O']
        let key_array = [...key.toUpperCase()]; // ['L', 'O', 'L', 'L', 'A']
        let message_number = []; // Arreglo donde iran los numeros de las posiciones de la letra en el alfabeto
        let key_number = []; // Arreglo donde iran los numeros de las posiciones de la letra en el alfabeto | Ejemplo: (7, 11, 12, 20) |
        let suma_mensaje_clases = []; // Arregle de la suma de numeros entre el mensaje y la clave
        let mensaje_cifrado = [];

        // Busca la letra en el alfabeto y agrega al arreglo el numero en la posicion donde se encontro esa letra:
        // Ejemplo-> "B" = 1
        message_array.forEach((elemento) => {
            message_number.push(alphabet.indexOf(elemento));
        });

        // Busca la letra en el alfabeto y agrega al arreglo el numero en la posicion donde se encontro esa letra:
        // Ejemplo-> "B" = 1
        key_array.forEach((elemento) => {
            key_number.push(alphabet.indexOf(elemento));
        });

        key_array_numbers = key_number; // Pasa al var global

        console.log('Mensaje numeros: ' + message_number);
        console.log('Clave numeros: ' + key_number);

        // Ciclo que recorrera el largo del arreglo de la llave,
        // para asi saber exactamente el numero de caracteres que tiene, tanto nuestro mensaje como nuestra llave
        for (let index = 0; index < key_number.length; index++) {
            // Variable que alamacena el valor que tenga el arreglo de llave en la posicion actual del ciclo
            const element = key_number[index];

            // Variable que alamacena el valor que tenga el arreglo de mensaje en la posicion actual del ciclo
            const element2 = message_number[index];

            // Variable que suma los dos elementos y los empuja a un arreglo nuevo
            const sum = element + element2;

            suma_mensaje_clases.push(sum);
        }

        console.log('Suma de Msg y Clave: ' + suma_mensaje_clases);

        // Cifra el mensaje con lus numeros ya sumados previamente
        for (let index = 0; index < suma_mensaje_clases.length; index++) {
            // Se le agrega en la posicion del index al mensaje cifrado lo que esta en el alfabeto con ese numero -> Ejemplo: 0 = "A"
            mensaje_cifrado[index] = alphabet[suma_mensaje_clases[index]];
        }

        visible = true;
        cifrado_array_numbers = mensaje_cifrado;
        cifrado = mensaje_cifrado.join('');
        console.log('Mensaje cifrado: ' + mensaje_cifrado);
    }

    function desifrarVigenere() {
        let cifrado_numer = [];

        let mensaje_desifrado = [];

        // Busca la letra en el alfabeto y agrega al arreglo el numero en la posicion donde se encontro esa letra:
        // Ejemplo-> "A" = 0
        cifrado_array_numbers.forEach((elemento) => {
            cifrado_numer.push(alphabet.indexOf(elemento));
        });

        for (let index = 0; index < key_array_numbers.length; index++) {
            // Variable que alamacena el valor que tenga el arreglo de llave en la posicion actual del ciclo
            let elementoDesifrado = key_array_numbers[index];

            // Variable que alamacena el valor que tenga el arreglo de mensaje en la posicion actual del ciclo
            let elementoDesifrado2 = cifrado_numer[index];

            // Variable que suma los dos elementos y los empuja a un arreglo nuevo
            const desifrado = elementoDesifrado2 - elementoDesifrado;

            mensaje_desifrado.push(desifrado);
        }

        // Desifrar el mensaje con lus numeros ya sumados previamente
        for (let index = 0; index < mensaje_desifrado.length; index++) {
            // Se le agrega en la posicion del index al mensaje cifrado lo que esta en el alfabeto con ese numero -> Ejemplo: 0 = "A"
            mensaje_desifrado[index] = alphabet[mensaje_desifrado[index]];
        }
        messageDesifrado = mensaje_desifrado.join('');
        desifrado = true;
    }

    function repeat() {
        message = '';
        key = '';
        visible = false;
        desifrado = false;
    }
</script>

<svelte:head>
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" />
    <link
        href="https://fonts.googleapis.com/css2?family=Lato:wght@300;400&display=swap"
        rel="stylesheet"
    />
    <link
        rel="stylesheet"
        href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200"
    />
</svelte:head>

<main>
    <div class="form">
        {#if !visible}
            <div class="input-group">
                <label for="message"> Mensaje a cifrar: </label>
                <input id="message" type="text" bind:value={message} />
            </div>
            <div class="input-group">
                <label for="key"> CLAVE: </label>
                <input id="key" type="text" bind:value={key} />
            </div>
            <button on:click={cifrarVigenere}>Cifrar!</button>
        {/if}
        {#if visible}
            {#if !desifrado}
                <p>Tu mensaje cifrado es: {cifrado}</p>
                <button on:click={desifrarVigenere}>Desifrar!</button>
            {/if}

            {#if desifrado}
                <h2>Tu mensaje original era: {messageDesifrado}</h2>
            {/if}
            <button on:click={repeat} class="repeat">
                <span class="material-symbols-outlined">restart_alt </span>
            </button>
        {/if}
    </div>
    <div class="footer">
        <span>
            <i
                ><a
                    href="https://github.com/AdrianRMV"
                    rel="noreferrer"
                    target="_blank"
                    title="Github profile">Created by Adrian Ramirez</a
                ></i
            >
        </span>
    </div>
</main>

<style>
    * {
        font-family: 'Lato', sans-serif;
        font-weight: 400;
    }
    .footer {
        margin-top: 30px;
    }
    .repeat {
        width: 30%;
        display: flex;
        justify-content: center;
        margin: 1em auto 0 auto;
    }
    .material-symbols-outlined {
        font-variation-settings: 'FILL' 0, 'wght' 400, 'GRAD' 0, 'opsz' 48;
    }
    .form {
        display: flex;
        flex-direction: column;
    }
    .input-group {
        display: flex;
        margin-bottom: 20px;
    }
    label {
        width: 30%;
    }
    button {
        margin-top: 20px;
        widows: max-content;
    }
</style>
