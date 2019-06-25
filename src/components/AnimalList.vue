<template>
<div>
    <form @submit.prevent="addAnimal">
        <div>
            <label for="vrsta">Vrsta</label>
            <input type="text" id="vrsta" v-model="newAnimal.vrsta"/>
        </div>
        <div>
            <label for="ime">Ime</label>
            <input type="text" id="ime" v-model="newAnimal.ime"/>
        </div>
        <div>
            <label for="datumRodjenja">Datum rodjenja</label>
            <input type="text" id="datumRodjenja" v-model="newAnimal.datumRodjenja"/>
        </div>
        <select id="podvrsta" v-model="newAnimal.podvrsta">
            <option v-for="(vrsta, index) in vrste"  :key="index"  >{{ vrsta }}</option>
        </select>
       <button type="submit">Add animal</button>
    </form>
    <ul>
        <li v-for="(animal, index) in animals" :key="index">
            {{ animal.vrsta }} - {{ animal.ime}} - {{ animal.datumRodjenja || 'Nepoznat'}} - {{ animal.podvrsta || 'Nepoznata'}}
            
            <button @click="removeAnimal(index)">Remove</button>
            <button @click="moveToTop(index)">Move to top</button>
        </li>
    </ul>
    <ul>
        <li v-for="(vrsta, index) in vrste" :key="index">
            {{ vrsta }}
            <button @click="pokaziVrstu(vrsta)">Pokazi</button>
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
                podvrsta: '',
            },

            animals: [
                { vrsta:'vrsta', ime:'Ime', datumRodjenja: '10.05.2009'},
                { vrsta:'vrstaa', ime:'Imee', datumRodjenja: '18.05.2010'},
                { vrsta:'vrstaaa', ime:'Imeee'},
                { vrsta:'vrstaaaa', ime:'Imeeee', datumRodjenja: '16.05.2001'},
                { vrsta:'vrstaaaaa', ime:'Imeeeee', datumRodjenja: '15.05.2004'},
            ],
            vrste: [
                "zmija",
                "ptica",
                "vuk"
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
        },

        pokaziVrstu(vrsta) {
            let animalsInSector = this.animals.filter(animal => animal.podvrsta === vrsta).map(animal => animal.ime)
            console.log(animalsInSector.join(','))
            alert(animalsInSector.join(','));
        }
    }
}
</script>
