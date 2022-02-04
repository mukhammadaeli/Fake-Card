<template>
    <div class="wrapper">
        <div class="container">
            <div class="cards">
                <div class="card" v-for="data in posts" v-bind:key="data.id">
                    <div>
                        <h3>{{ data.title }}</h3>
                    </div>
                    <div>
                        <p>{{ data.body }}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import axios from 'axios'

    export default {
        data(){
            return {
                posts:[]
            }
        },
        mounted() {
            const self=this;

            axios.get('https://jsonplaceholder.typicode.com/posts')
            
            .then(function(res){

            self.posts=res.data;
                console.log(res.data)
            })

            .catch(function(error){
                console.log(error);
            })
        }
    }
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;400;500;600;700;800;900&display=swap');

*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Poppins', sans-serif;
}

 .wrapper{
     width: 100%;
     height: 100%;
}

.container{
    max-width: 1280px;
    padding: 20px 40px;
    margin: 0 auto;
}

.cards{
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
}

.card{
    margin: 10px 0;
    padding: 15px 30px;
    max-width: 320px;
    height: 280px;
    width: 100%;
    border: 2px solid #808080;
    border-radius: 8px;
    cursor: pointer;
}

h3{
    font-size: 18px;
    margin-bottom: 15px;
}

p{
    font-size: 14px;
}
</style>