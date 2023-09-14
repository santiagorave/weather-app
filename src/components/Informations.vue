<template>
  <section class="informations">
    <h3>Additional Information</h3>
    <article>
      <div class="row">
          <div class="info" >
            <article class="front" :class="{sunsetS:(hour>=19 && hour<=20), sunriseS:(hour>=5 && hour<=7), nightS:hour>=21 || hour<=4,dayS:(hour>=8 && hour<=18) }">
            <section>
              <img src="/src/assets/img/temperature.png" alt="temperature" />
              <small>Feels Like </small>
            </section>
            <span v-if="temp=='C' || temp==''">{{ infoWeather.current?.feelslike_c }} °C</span>
            <span v-else>{{ infoWeather.current?.feelslike_f }} °F</span>
            <p>Similar to the actual temperature.</p>
            </article>
            <article class="back" :class="{sunsetS:(hour>=19 && hour<=20), sunriseS:(hour>=5 && hour<=7), nightS:hour>=21 || hour<=4,dayS:(hour>=8 && hour<=18) }">
            <aside v-if="infoWeather.current?.feelslike_c<0">
              <img src="/src/assets/img/coat.png" alt="coat">
              <p>Winter clothes needed</p>
              <small>Bring an extra set of clothes</small>
            </aside>
            <aside v-else-if="infoWeather.current?.feelslike_c<17">
              <img src="/src/assets/img/hoodie.png" alt="hoodie">
              <p>No extra layers needed</p>
              <small>Sweaters, hoodies, etc...</small>
            </aside>
            <aside v-else-if="infoWeather.current?.feelslike_c<23">
              <img src="/src/assets/img/tshirt.png" alt="tshirt">
              <p>Cool weather</p>
              <small>T-shirts</small>
            </aside>
               <aside v-else>
              <img src="/src/assets/img/shorts.png" alt="shorts">
              <p>Summer weather</p>
              <small>Shorts, light clothing</small>
            </aside>
            </article>
          </div>
          <div class="info">
            <article class="front" :class="{sunsetS:(hour>=19 && hour<=20), sunriseS:(hour>=5 && hour<=7), nightS:hour>=21 || hour<=4,dayS:(hour>=8 && hour<=18) }">
            <section>
              <img src="/src/assets/img/uv.png" alt="uv" />
              <small>UV Index</small>
            </section>
            <span>{{ infoWeather.current?.uv }}</span>
            </article>
            <article class="back" :class="{sunsetS:(hour>=19 && hour<=20), sunriseS:(hour>=5 && hour<=7), nightS:hour>=21 || hour<=4,dayS:(hour>=8 && hour<=18) }">
            <small>{{getUVIndexLevel(infoWeather.current?.uv)}}</small>  
               <aside v-if="infoWeather.current?.uv<3">
              <p>No sun protection needed</p>
              </aside>
              <aside v-else-if="infoWeather.current?.uv<=6">
                <img  src="/src/assets/img/sun-block.png" alt="sun-protection">
                <p>Sun protection needed during the day</p>
              </aside>
              <aside v-else-if="infoWeather.current?.uv<8">
                <img src="/src/assets/img/sun-block.png" alt="sun-protection">
                <p>Extra protection needed. wear protective clothing, a wide-brimmed hat, and sunglasses.</p>
              </aside>
              <aside v-else-if="infoWeather.current?.uv<11">
                <img src="/src/assets/img/sun-block.png" alt="sun-protection">
                <p>Extra protection needed. Be careful outside</p>
              </aside>
            </article>
             
          </div>
      </div>
      <div class="row">
          <div class="info">
          <article :class="{sunsetS:(hour>=19 && hour<=20), sunriseS:(hour>=5 && hour<=7), nightS:hour>=21 || hour<=4,dayS:(hour>=8 && hour<=18) }" class="front">
            <section>
              <img src="/src/assets/img/humidity.png" alt="humidity" />
              <small>Precipitation</small>
            </section>
            <span>{{ infoWeather.current?.precip_mm }} mm</span>
          </article>
          <article class="back" :class="{sunsetS:(hour>=19 && hour<=20), sunriseS:(hour>=5 && hour<=7), nightS:hour>=21 || hour<=4,dayS:(hour>=8 && hour<=18) }">
              <aside v-if="infoWeather.current?.precip_mm==0">
                 <h4>No Rain</h4>
                 <p>No unbrella needed</p>
                </aside>
              <aside v-else-if="infoWeather.current?.precip_mm>0 && infoWeather.current?.precip_mm<=0.5 ">
              <h4>Slight Rain</h4>
              <i class="fa-solid fa-umbrella"></i>
              <p>You may need an umbrella</p>
              </aside>
              <aside v-else-if="infoWeather.current?.precip_mm>0.5 && infoWeather.current?.precip_mm<=4.0 ">
              <h4>Moderate Rain</h4> 
              <i class="fa-solid fa-umbrella"></i>
              <p>You need an umbrella</p>


              </aside>
              <aside v-else-if="infoWeather.current?.precip_mm>4.0 && infoWeather.current?.precip_mm<=8.0 ">
              <h4>Heavy Rain</h4> 
              <i class="fa-solid fa-umbrella"></i>
              <p>You really need an umbrella</p>

              </aside>
              <aside v-else-if="infoWeather.current?.precip_mm>8.0">
               <h4>Very Heavy Rain</h4>
              <i class="fa-solid fa-umbrella"></i>
              <p>You really need an umbrella</p>
                </aside>
          </article>
          </div>

          <div class="info">
            <article class="front" :class="{sunsetS:(hour>=19 && hour<=20), sunriseS:(hour>=5 && hour<=7), nightS:hour>=21 || hour<=4,dayS:(hour>=8 && hour<=18) }">
            <section>
              <img src="/src/assets/img/wind.png" alt="wind" />
              <small>Wind</small>
            </section>
            <span>{{ infoWeather.current?.wind_kph }} km/h</span>
            </article>
            <article class="back" :class="{sunsetS:(hour>=19 && hour<=20), sunriseS:(hour>=5 && hour<=7), nightS:hour>=21 || hour<=4,dayS:(hour>=8 && hour<=18) }">
            </article>

          </div>

      </div>
    </article>
      <!-- <section class="history">
        <h3>History</h3>
        <ul>
          <li v-for="city in historyCities" :key="city">
           
           <aside  style="color:black">{{city}}</aside> 
          </li>
        </ul>
      </section> -->

  </section>

</template>

<script>
export default {
  name: "Informations",
  props:{
    infoWeather:Object,
    hour:Number,
    temp:String,
    historyCities:Array
  },
  data() {
    return {
      uvIndexLevel: "",
    };
  },
  methods: {
    getUVIndexLevel(uvIndex) {
      if (uvIndex < 3) {
        return "Low";
      } else if (uvIndex < 6) {
        return "Moderate";
      } else if (uvIndex < 8) {
        return "High";
      } else if (uvIndex < 11) {
        return "Very High";
      } else {
        return "Extreme";
      }
    },
  },
  computed: {
    getTemperatureMessage() {
      const temperatureDifference =
        this.infoWeather.current?.feelslike_c -
        this.infoWeather.current?.temp_c;
      if (temperatureDifference >= 10) {
        return "Significantly different from the actual temperature";
      } else if (temperatureDifference >= 5) {
        return "There's a noticeable difference in temperature";
      } else if (temperatureDifference >= 2) {
        return "Little bit different from the actual temperature";
      } else {
        return "Similar to the actual temperature";
      }
    },
    currentTemperature() {
      return this.infoWeather.current?.temp_c;
    },
  },
};
</script>

<style scoped>
.informations {
  display: flex;
  flex-direction: column;
  row-gap: 2vh;
  color: white;
  font-size: 20px;
}

.informations > article {
  display: flex;
  flex-direction: column;
  row-gap: 2vh;
}

.row {
  display: flex;
  column-gap: 2vh;
}

.informations h3 {
  color: black;
  font-size: 24px;
}

.info {
  display: flex;
  flex-direction: column;
  row-gap: 2vh;
  justify-content: space-evenly;
  align-items: center;
  border-radius: 20px;
  position: relative;
  width: 34vh;
  height: 27vh;
  text-align: center;
  perspective: 150vh;

}

.info:hover .front {
  transform: rotateY(180deg);

}
.info:hover .back {
  transform: rotateY(0deg);

}

.back {
  transform: rotateY(-180deg);
  padding: 5px;

}
.back aside {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  row-gap: 3vh;
}



.back aside i {
  font-size: 50px;
}

.back > aside > img {
  width: 70px;
  height: 70px;
}

.front,.back {
  position: absolute;
  backface-visibility: hidden;
  transition: .8s ease;
   width: 34vh;
  height: 27vh;
  border-radius: 20px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  row-gap: 3vh;



}

.info > section {
  display: flex;
  align-items: center;
  column-gap: 2vh;
}

.info small {
  font-size: 18px;
}

.info span {
  font-weight: 700;
  font-size: 45px;
}

.info p {
  font-size: 16px;
}

.info img {
  width: 4vh;
  height: 4vh;
}

.sunsetS{
  background-color: #C38154;


}
.dayS {
   background-color: #50afe9; 

}
.nightS{
background-color: #526D82;
}
.sunriseS{
background-color: #C4D7B2;
}
</style>

