<template>
    <article class="selection">
        <input type="radio" name="temperature" @change="changeTemp" id="celcius" value="C">
        <label for="celcius">Celcius</label>
        <input type="radio" name="temperature" @change="changeTemp" id="Fahrenheit" value="F" >
        <label for="celcius">Fahrenheit</label>
    </article>
</template>

<script>
export default {
  props: {
    temp: String,
  },
    methods:{
        changeTemp(e) {
            console.log(e.target.value)
            this.$emit('tempType',e.target.value);
        }
    }
}
</script>
<style scoped>
    .selection{
        display: flex;
        justify-content: end;
        padding-right: 7vw;
        column-gap: 1vw;
    }
</style>