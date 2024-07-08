<template>
<h1>Car List</h1>

<ul>
    <li v-for="car in carList" :key="car.id">{{car.make}} {{car.model}}</li>
</ul>

<input v-model="make" type="text" placeholder="Make">
<input v-model="model" type="text" placeholder="Model">

<p>{{error}}</p>

<button v-on:click="addCar">Add Car</button>
<button v-on:click="reset ">Reset List</button>
</template>


<script>

let carid = 0;

export default {
    name: "CarList",
    data(){
        return {
            carList : [],
            make : "",
            model : "",
            error : ""
        }
    } , 
    methods: {
        addCar() {

            this.error = ""

            if(this.make && this.model){
                const newItem = {
                    id : carid++ ,
                    make : this.make , 
                    model : this.model
                }
                this.carList.push(newItem)
            } else {
                this.error = "Enter make and model car"
            }

            this.make = ""
            this.model = ""
            
        } , 
        reset(){
            this.carList = [];
        }
    }
}
</script>


<style scoped>
h1 {
    margin: 20px;
    font-size: 55px;
}

ul {
    font-size: 1.5em;
    line-height: 30px;
}

li{
    cursor: pointer;
}
li:hover{
    color: hsla(0, 0%, 0%, 0.65);
}

input {
    padding: 10px 20px;
    font-size: 1.5em;
    border: 1px solid black;
    border-radius: 10px;
    display: block;
    margin: 20px
}

p{
    margin: 20px;
}

button {
    margin-inline: 20px;
    padding: 10px 30px;
    font-size: 20px;
    border: none;
    border-radius: 10px;
    background-color: black;
    color: white;
    cursor: pointer;
}
</style>
