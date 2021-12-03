<template>
<Header/>
    <h1>Home</h1>
    <h2>Hello {{name}} , Welcome On Home Page</h2>
    <table border="1">
        <tr>
            <td>ID</td>
            <td>Name</td>
            <td>Address</td>
            <td>Contact</td>
            <td>Actions</td>
        </tr>
        <tr v-for="item in restaurants" :key="item.id">
            <td>{{item.id}}</td>
            <td>{{item.name}}</td>
            <td>{{item.address}}</td>
            <td>{{item.contact}}</td>
            <td>
                <router-link :to="'/update/'+item.id">Update</router-link>
                <button v-on:click="deleteRestaurant(item.id)">Delete</button>
            </td>
        </tr>
    </table>
</template>
<script>
import axios from 'axios'
import Header from './Header.vue'
    export default{
        name:'Home',
        data(){
            return{
                name:'',
                restaurants:[]
            }
        },
        methods:{
            async deleteRestaurant(id){
                let result = await axios.delete("http://localhost:3000/restaurant/"+id);
                if(result.status==200)
                {
                    alert("Successfully Delete");
                    this.loadData();
                }
            },
            async loadData()
            {
                let user = localStorage.getItem('user-info');
                this.name=JSON.parse(user).name
                if(!user)
                {
                    this.$router.push({name:'SignUp'})
                }
                let result = await axios.get("http://localhost:3000/restaurant")
                this.restaurants=result.data;
            }
        },
        components:{
            Header,
        },
        mounted(){
            this.loadData();
        }

    }
</script>
<style scoped>
    td{
        width: 160px;
        height: 40px;
    }
    table{
        margin: auto;
    }
    table a{
        text-decoration: none;
        color: green;
        padding: 5px;
        border: 1px solid skyblue;
    }
    table button{
        margin: 10px;
        cursor: pointer;
        color: red;
    }
</style>
