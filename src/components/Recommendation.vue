<template>
  <article class="recommendation">
    <h3>Weather Clothing Guide</h3>
    <section
      class="recommendations"
      :class="{
        sunsetS: hour >= 19 && hour <= 20,
        sunriseS: hour >= 5 && hour <= 7,
        nightS: hour >= 21 || hour <= 4,
        dayS: hour >= 8 && hour <= 18,
      }"
    >
      <section v-if="infoWeather.current?.temp_c >= 23" >
        <article>
          <h3>Accessories</h3>
          <figure>
            <div><img src="../assets/img/Accessories/cap.png" alt="cap" /></div>
            <div>
              <img
                src="../assets/img/Accessories/sunglasses.png"
                alt="sunglasses"
              />
            </div>
            <div>
              <img src="../assets/img/Accessories/sunhat.png" alt="sunhat" />
            </div>
          </figure>
        </article>
        <article>
          <h3>Top</h3>
          <figure>
            <div><img src="../assets/img/Top/tshirt.png" alt="tshirt" /></div>
            <div><img src="../assets/img/Top/polo-shirt.png" alt="polo" /></div>
            <div>
              <img src="../assets/img/Top/hawaiian-shirt.png" alt="half-shirt" />
            </div>
          </figure>
        </article>
        <article>
          <h3>Bottoms</h3>
          <figure>
            <div>
              <img src="../assets/img/Bottoms/shorts(1).png" alt="shorts1" />
            </div>
            <div>
              <img src="../assets/img/Bottoms/shorts(3).png" alt="shorts3" />
            </div>
            <div>
              <img src="../assets/img/Bottoms/shorts(2).png" alt="shorts2" />
            </div>
          </figure>
        </article>
        <article>
          <h3>Shoes</h3>
          <figure>
            <div><img src="../assets/img/shoes/sandals.png" alt="shorts3" /></div>
            <div>
              <img src="../assets/img/shoes/sandals (2).png" alt="shorts2" />
            </div>
            <div>
              <img src="../assets/img/shoes/flip-flops.png" alt="shorts1" />
            </div>
          </figure>
        </article>
      </section>
      <section
        v-else-if="
          infoWeather.current?.temp_c >= 19 && infoWeather.current?.temp_c < 23
        "
      >
        <article>
          <h3>Accessories</h3>
          <figure>
            <div>
              <img
                src="../assets/img/Accessories/cap (1).png"
                alt="accesories1"
              />
            </div>
            <div>
              <img
                src="../assets/img/Accessories/sunglasses.png"
                alt="accesories2"
              />
            </div>
            <div>
              <img
                src="../assets/img/Accessories/sunhat(1).png"
                alt="accesories3"
              />
            </div>
          </figure>
        </article>
        <article>
          <h3>Top</h3>
          <figure>
            <div><img src="../assets/img/Top/sleeves.png" alt="top1" /></div>
            <div><img src="../assets/img/Top/shirt (1).png" alt="top2" /></div>
            <div>
              <img src="../assets/img/Top/shirt (2).png" alt="top3t" />
            </div>
          </figure>
        </article>
        <article>
          <h3>Bottoms</h3>
          <figure>
            <div>
              <img src="../assets/img/Bottoms/pants (1).png" alt="bottoms1" />
            </div>
            <div>
              <img src="../assets/img/Bottoms/trousers.png" alt="bottoms2" />
            </div>
            <div>
              <img src="../assets/img/Bottoms/loose-pants.png" alt="bottoms3" />
            </div>
          </figure>
        </article>
        <article>
          <h3>Shoes</h3>
          <figure>
            <div><img src="../assets/img/shoes/sneakers.png" alt="shoes1" /></div>
            <div>
              <img src="../assets/img/shoes/sneakers (1).png" alt="shoes2" />
            </div>
            <div>
              <img src="../assets/img/shoes/sneakers (2).png" alt="shoes3" />
            </div>
          </figure>
        </article>
      </section>
      <section
        v-else-if="
          infoWeather.current?.temp_c >= 11 && infoWeather.current?.temp_c < 19
        "
      >
        <article>
          <h3>Accessories</h3>
          <figure>
            <div>
              <img src="../assets/img/Accessories/cap.png" alt="accesories1" />
            </div>
            <div>
              <img
                src="../assets/img/Accessories/sunglasses.png"
                alt="accesories2"
              />
            </div>
            <div>
              <img src="../assets/img/Accessories/bucket.png" alt="accesories3" />
            </div>
          </figure>
        </article>
        <article>
          <h3>Top</h3>
          <figure>
            <div><img src="../assets/img/Top/coat (3).png" alt="top1" /></div>
            <div><img src="../assets/img/Top/cardigan.png" alt="top2" /></div>
            <div>
              <img src="../assets/img/Top/cardigan (1).png" alt="top3t" />
            </div>
          </figure>
        </article>
        <article>
          <h3>Bottoms</h3>
          <figure>
            <div>
              <img src="../assets/img/Bottoms/pants (3).png" alt="bottoms3" />
            </div>
            <div>
              <img src="../assets/img/Bottoms/jeans.png" alt="bottoms1" />
            </div>
            <div>
              <img src="../assets/img/Bottoms/loose-pants.png" alt="bottoms2" />
            </div>
          </figure>
        </article>
        <article>
          <h3>Shoes</h3>
          <figure>
            <div><img src="../assets/img/shoes/sneakers.png" alt="shoes1" /></div>
            <div>
              <img src="../assets/img/shoes/sneakers (1).png" alt="shoes2" />
            </div>
            <div>
              <img src="../assets/img/shoes/sneakers (2).png" alt="shoes3" />
            </div>
          </figure>
        </article>
      </section>
      <section
        v-else-if="
          infoWeather.current?.temp_c >= 5 && infoWeather.current?.temp_c < 11
        "
      >
        <article>
          <h3>Accessories</h3>
          <figure>
            <div>
              <img src="../assets/img/Accessories/beanie.png" alt="accesories1" />
            </div>
            <div>
              <img src="../assets/img/Accessories/scarf.png" alt="accesories2" />
            </div>
            <div>
              <img src="../assets/img/Accessories/socks.png" alt="accesories3" />
            </div>
          </figure>
        </article>
        <article>
          <h3>Top</h3>
          <figure>
            <div><img src="../assets/img/Top/sweater.png" alt="top1" /></div>
            <div><img src="../assets/img/Top/sweater(1).png" alt="top2" /></div>
            <div>
              <img src="../assets/img/Top/sweater(2).png" alt="top3t" />
            </div>
          </figure>
        </article>
        <article>
          <h3>Bottoms</h3>
          <figure>
            <div>
              <img src="../assets/img/Bottoms/trousers.png" alt="bottoms1" />
            </div>
            <div>
              <img src="../assets/img/Bottoms/pants (3).png" alt="bottoms2" />
            </div>
            <div>
              <img src="../assets/img/Bottoms/pants (4).png" alt="bottoms3" />
            </div>
          </figure>
        </article>
        <article>
          <h3>Shoes</h3>
          <figure>
            <div>
              <img src="../assets/img/shoes/sneakers (2).png" alt="shoes1" />
            </div>
            <div><img src="../assets/img/shoes/boots(1).png" alt="shoes2" /></div>
            <div>
              <img src="../assets/img/shoes/sneakers (1).png" alt="shoes3" />
            </div>
          </figure>
        </article>
      </section>
      <section v-else-if="infoWeather.current?.temp_c < 5">
        <article>
          <h3>Accessories</h3>
          <figure>
            <div>
              <img
                src="../assets/img/Accessories/winter-hat.png"
                alt="accesories1"
              />
            </div>
            <div>
              <img src="../assets/img/Accessories/glove.png" alt="accesories2" />
            </div>
            <div>
              <img
                src="../assets/img/Accessories/earmuffs.png"
                alt="accesories3"
              />
            </div>
          </figure>
        </article>
        <article>
          <h3>Top</h3>
          <figure>
            <div><img src="../assets/img/Top/coat.png" alt="top1" /></div>
            <div><img src="../assets/img/Top/coat (1).png" alt="top2" /></div>
            <div>
              <img src="../assets/img/Top/coat (2).png" alt="top3t" />
            </div>
          </figure>
        </article>
        <article>
          <h3>Bottoms</h3>
          <figure>
            <div>
              <img src="../assets/img/Bottoms/winter.png" alt="bottoms1" />
            </div>
            <div>
              <img src="../assets/img/Bottoms/winter(1).png" alt="bottoms2" />
            </div>
            <div>
              <img src="../assets/img/Bottoms/winter(2).png" alt="bottoms3" />
            </div>
          </figure>
        </article>
        <article>
          <h3>Shoes</h3>
          <figure>
            <div><img src="../assets/img/shoes/boots.png" alt="shoes1" /></div>
            <div><img src="../assets/img/shoes/boots(1).png" alt="shoes2" /></div>
            <div><img src="../assets/img/shoes/boots(2).png" alt="shoes3" /></div>
          </figure>
        </article>
      </section>
    </section>
  </article>
</template>

<script>
export default {
  name: "Recommendation",
  props: {
    infoWeather: Object,
    hour:Number,
    temp:String,
  },
};
</script>

<style>

.recommendation {
  display: flex;
  flex-direction: column;
  row-gap: 2vh;
}

.recommendation h3 {
 font-size: 24px;
}

.recommendations {
  display: flex;
  flex-direction: column;
  row-gap: 2vh;
  border-radius: 20px;
  padding: 5%;  
  color: whitesmoke;
}

.recommendations > section {
  display: flex;
  flex-direction: column;
  row-gap: 3vh;
}

.recommendations article {
  display: flex;
  flex-direction: column;
  row-gap: 3vh;
}

.recommendations > section figure {
  display: flex;
  justify-content: space-around;
}

.recommendations > section img {
  width: 100%;
}

.recommendations div {
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 20px;
  width: 20%;
  padding: 3%;
}
.sunsetS {
  background-color: #c38154;
}
.dayS {
  background-color: #50afe9;
}
.nightS {
  background-color: #526d82;
}
.sunriseS {
  background-color: #c4d7b2;
}
</style>