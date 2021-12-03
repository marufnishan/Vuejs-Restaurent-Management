<template>
<Header/>
    <h1>Add</h1><br><br>
    <h2>Hi User, Welcome On Add Restaurant Page</h2>
    <form class="add">
        <input type="text" placeholder="Enter Name .." v-model="restaurant.name" name="name">
        <input type="text" placeholder="Enter Address .." v-model="restaurant.address" name="address">
        <input type="text" placeholder="Enter Contact .." v-model="restaurant.contact" name="contact">
        <button type="button" v-on:click="addRestaurant">Add New Restaurant</button>
    </form>
</template>
<script>
import axios from 'axios'
import Header from './Header.vue'
    export default{
        name:'Add',
        components:{
            Header,
        },
        data(){
            return{
                restaurant:{
                    name:'',
                    address:'',
                    contact:''
                },
            }
        },
        methods:{
            
                async addRestaurant(){
                    console.warn("addRestaurant",this.restaurant.name,this.restaurant.address,this.restaurant.contact)
                    let result = await axios.post("http://localhost:3000/restaurant",{
                    name:this.restaurant.name,
                    address:this.restaurant.address,
                    contact:this.restaurant.contact
                });
                console.warn(result);
                }
        }
    }
</script>
<style scoped>

</style>
