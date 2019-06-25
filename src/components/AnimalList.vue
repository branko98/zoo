<template>
<div>
    <form @submit.prevent="addAnimal">
        <div>
            <label for="firstName">Vrsta</label>
            <input type="text" id="vrsta" v-model="newAnimal.vrsta"/>
        </div>
        <div>
            <label for="firstName">Ime</label>
            <input type="text" id="ime" v-model="newAnimal.ime"/>
        </div>
        <div>
            <label for="firstName">Datum rodjenja</label>
            <input type="text" id="datumRodjenja" v-model="newAnimal.datumRodjenja"/>
        </div>
       <button type="submit">Add animal</button>
    </form>
    <ul>
        <li v-for="(animal, index) in animals" :key="index">
            {{ animal.vrsta }} - {{ animal.ime}} - {{ animal.datumRodjenja || 'Nepoznat'}}
            <button @click="removeAnimal(index)">Remove</button>
            <button @click="moveToTop(index)">Move to top</button>
        </li>
    </ul>
</div>
</template>

<script>
export default {
    data() {
        return {
             newAnimal: {
                vrsta: '',
                ime: '',
                datumRodjenja: '',
            },

            animals: [
                { vrsta:'vrsta', ime:'Ime', datumRodjenja: '10.05.2009'},
                { vrsta:'vrstaa', ime:'Imee', datumRodjenja: '18.05.2010'},
                { vrsta:'vrstaaa', ime:'Imeee'},
                { vrsta:'vrstaaaa', ime:'Imeeee', datumRodjenja: '16.05.2001'},
                { vrsta:'vrstaaaaa', ime:'Imeeeee', datumRodjenja: '15.05.2004'},
            ]
        }
    },

    methods: {
        removeAnimal(index) {
            this.animals.splice(index, 1)      
        },

        moveToTop(index) {
        this.animals.unshift(this.animals[index])  
        this.animals.splice((index+1),1)
        },

        addAnimal(){
            this.animals.push({ ...this.newAnimal })
        }
    }
}
</script>
