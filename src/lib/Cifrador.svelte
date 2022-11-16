<script>
    const charConverter = {
        A: 0,
        B: 1,
        C: 2,
        D: 3,
        E: 4,
        F: 5,
        G: 6,
        H: 7,
        I: 8,
        J: 9,
        K: 10,
        L: 11,
        M: 12,
        N: 13,
        O: 14,
        P: 15,
        Q: 16,
        R: 17,
        S: 18,
        T: 19,
        U: 20,
        V: 21,
        W: 22,
        X: 23,
        Y: 24,
        Z: 25,
    };

    const CLAVE = 'LOREM';
    const CLAVE_CHAR = [...CLAVE];

    let CLAVE_NUMBERS = [];

    for (const prop in charConverter) {
        // console.log(`charConverter.${prop} = ${charConverter[prop]}`);
        // console.log(charConverter[charConverter[prop]])

        console.log(charConverter[prop]);
        console.log(CLAVE_CHAR[charConverter[prop]]);

        if (CLAVE_CHAR[charConverter[prop]] == charConverter[prop]){
            CLAVE_NUMBERS.push(charConverter[prop]);
            console.log(CLAVE_NUMBERS);
        }
    }

</script>

<main>
    {CLAVE_CHAR}
</main>
