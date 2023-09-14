<script setup>
import HelloWorld from './components/HelloWorld.vue'
import NavComponent from './components/NavBar.vue'
import FooterComponent from './components/Footer.vue'
import Header from './components/Header.vue'
import CurrentData from './services/Current.vue'
import ForecastVue from './components/Forecast.vue'
import Informations from './components/Informations.vue'
import TypeSelector from './components/TypeSelector.vue'
import Recommendation from './components/Recommendation.vue'
import { ref } from 'vue'
const infoWeather = ref({})
function sendData(weatherD){
infoWeather.value=weatherD;
}
const city = ref('');
const temp = ref('');
const hour = ref('');
const historyCities = ref([]);
function searchCity(cityReceived) {
  city.value=cityReceived;
  historyCities.value.push(cityReceived);
}
function tempHandler(temperature) {
temp.value=temperature;
}
function sendHour(hourR){
hour.value=hourR;
}
// function pushCity(city){
//   historyCities.value.push(city);
// console.log('arr',historyCities.value)
// }
</script>

<template>
    <Header @city="searchCity($event)"/>
    <section class="front">
      <TypeSelector @tempType="tempHandler"/>
      <CurrentData @arrayCities="pushCity" @dataWeather="sendData" @hourDay="sendHour" :temp="temp"  :city="city"/>
    </section>
    <section class="contents">
      <section class="left">
        <ForecastVue :hour="hour" :temp="temp" :city="city"/>
      </section>
      <section class="right">
        <Informations :historyCities="historyCities" :hour="hour" :temp="temp" :infoWeather="infoWeather"/>
        <Recommendation :hour="hour" :temp="temp" :infoWeather="infoWeather "/>
      </section>
    </section>
    <FooterComponent/>

</template>

<style scoped>
#app{
  align-items: center;
  justify-content: center;
}

.front {
  padding: 1%;
}

.contents {
  display: flex;
  justify-content: space-evenly;
  flex-wrap: wrap;
  row-gap: 3vh;
  padding-bottom: 5vh;
}

.right {
  display: flex;
  flex-direction: column;
  row-gap: 5vh;
}

</style>
