<template>
    <ul>
        <li v-for="(animal, index) in animals" :key="index">
            {{ animal.vrsta }} - {{ animal.ime}} - {{ animal.datumRodjenja }}
        </li>
    </ul>
</template>

<script>
export default {
    data() {
        return {
            animals: [
                { vrsta:'vrsta', ime:'Ime', datumRodjenja: '10.05.2009'},
                { vrsta:'vrstaa', ime:'Imee', datumRodjenja: '18.05.2010'},
                { vrsta:'vrstaaa', ime:'Imeee', datumRodjenja: '13.05.2011'},
                { vrsta:'vrstaaaa', ime:'Imeeee', datumRodjenja: '16.05.2001'},
                { vrsta:'vrstaaaaa', ime:'Imeeeee', datumRodjenja: '15.05.2004'},
            ]
        }
    }
}
</script>
