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
        </tr>
        <tr v-for="item in restaurants" :key="item.id">
            <td>{{item.id}}</td>
            <td>{{item.name}}</td>
            <td>{{item.address}}</td>
            <td>{{item.contact}}</td>
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
        components:{
            Header,
        },
        async mounted(){
            let user = localStorage.getItem('user-info');
            this.name=JSON.parse(user).name
            if(!user)
            {
                this.$router.push({name:'SignUp'})
            }
            let result = await axios.get("http://localhost:3000/restaurant")
            this.restaurants=result.data;
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
</style>
