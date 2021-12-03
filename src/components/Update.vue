<template>
<Header/>
    <h1>Update</h1><br><br>
    <h2>Hi User, Welcome On Update Restaurant Page</h2>
</template>
<script>
import Header from './Header.vue'
    export default{
        name:'Update',
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
