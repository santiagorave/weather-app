<template>
    <div id="header">
        <header>
            <h1>Sky Forecast</h1>
            <form >
                <input v-model="searchCity" placeholder="City..." type="search">
                <button @click="handleSearch" type="submit" class="search"><i class="fa-solid fa-magnifying-glass"></i></button>
            </form>
        </header>
    </div>
</template>

<script>

export default {
    name:'Header', 
    data(){
        return {
            searchCity:''
        }
    },
    methods:{
        handleSearch(e) {
            e.preventDefault();
            // console.log(this.searchCity);
            this.$emit('city',this.searchCity)
        }
    }
}
</script>

<style scoped>
#header{
    display: flex;
    padding: 2%;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
    border-bottom: #f4eaea solid;

}
header{
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 90%;
}
h1{
    color:dodgerblue;

}
form{
    display: flex;
    align-items: center;
    padding-right:10vw ;
    
}
input{
    flex-grow: 1;
    padding: 8px;
    border: 1px solid #ccc;
    border-right: none;
    border-top-right-radius: 0;
    border-top-left-radius: 5px;
    border-bottom-right-radius: 0;
    border-bottom-left-radius: 5px;
    width: 30vw;
}

input:focus {
    /* : red; */
    outline-color: dodgerblue;
}
button{
    padding: 8px;
    background-color: white;
    border: 1px solid #ccc;
    border-left: none;
    border-top-left-radius: 0;
    border-top-right-radius: 5px;
    border-bottom-left-radius: 0;
    border-bottom-right-radius: 5px;
    cursor: pointer;
}
button i {
  color: black;
}

</style>
