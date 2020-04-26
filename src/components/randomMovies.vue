<template>


    <div class="row">
        <div class="column">

            <div class="gallery">
                <img class="movieImage" v-bind:src="moviesList.Search[0].Poster">
                <div class="title">{{moviesList.Search[0].Title}}</div>
            </div>

        </div>
        <div class="column">

            <div class="gallery">
                <img class="movieImage" v-bind:src="moviesList.Search[1].Poster">
                <div class="title">{{moviesList.Search[1].Title}}</div>
            </div>

        </div>
        <div class="column">

            <div class="gallery">
                <img class="movieImage" v-bind:src="moviesList.Search[2].Poster">
                <div class="title">{{moviesList.Search[2].Title}}</div>
            </div>

        </div>
        <div class="column">

            <div class="gallery">
                <img class="movieImage" v-bind:src="moviesList.Search[3].Poster">
                <div class="title">{{moviesList.Search[3].Title}}</div>
            </div>

        </div>
    </div>


</template>

<script>
    export default {
        name: "randomMovies",
        mounted:function(){
            this.loadRandom()
        },
        data(){
            return{
                searchKey:'',
                moviesList:[],
                randomkeywords:['Shaman','Lord','Capitan','Super','naruto'],
            }
        },

        methods:{

            searchMovies()
            {
                var url = 'http://www.omdbapi.com/?s=' + this.searchKey + '&apikey=8dc936a1&';
                fetch(url)
                    .then(response=>response.json())
                    .then(data=>{
                        this.moviesList=data;
                    })
            },

            loadRandom()
            {
                const randomElement = this.randomkeywords[Math.floor(Math.random() * this.randomkeywords.length)];
                var url = 'http://www.omdbapi.com/?s=' + randomElement + '&apikey=8dc936a1&';
                fetch(url)
                    .then(response=>response.json())
                    .then(data=>{
                        this.moviesList=data;
                    })
            }
        }
    };

</script>

<style scoped>
.gallery{
    margin:5px;
    float: left;
    border: 1px solid;
}
.movieImage{
    width: 100%;
    height: auto
}
.title{
    padding: 15px;
    text-align: center
}
.row {
    display: flex;
}

.column {
    flex: 10%;
    padding: 5px;
}
</style>