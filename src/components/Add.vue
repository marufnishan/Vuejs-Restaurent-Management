<template>
<Header/>
    <h1>Add</h1><br><br>
    <h2>Hi User, Welcome On Add Restaurant Page</h2>
</template>
<script>
import Header from './Header.vue'
    export default{
        name:'Add',
        components:{
            Header,
        },
        mounted(){
            let user = localStorage.getItem('user-info');
            if(!user)
            {
                this.$router.push({name:'SignUp'})
            }
        }

    }
</script>
<style scoped>

</style>
