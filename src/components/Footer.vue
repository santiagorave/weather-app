<template>
  <footer>
    <article>
      <img src="../assets/img/logo.jpg" alt="logo">
      <p>
        Get the weather forecast in a beautiful and powerful website. See current
        and forecasted weather with a smart layout that updates as conditions
        change. And view precipitation, uv index, and temperature to see
        different conditions near you.
      </p>
    </article>
    <section>
      <small> Copyright &copy; 2023 Sky Forecast </small>
      <a href="#"> BACK TO TOP </a>
    </section>
  </footer>
</template>


<script>
export default {
  name: "Footer",
  setup() {
    return {};
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300;0,400;0,500;0,700;0,800;1,300;1,400;1,500;1,600;1,700;1,800&display=swap");

a {
  text-decoration: none;
}

p {
  line-height: 1.5;
}

footer {
  display: flex;
  flex-direction: column;
  height: 20%;
  background-color: white;
  color: rgb(69, 114, 159);
  row-gap: 3vh;
  justify-content: center;
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
  padding: 1%;
}

footer img {
  width: 13%;
}

footer > article {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  width: 100%;

}

footer > section {
  display: flex;
  flex-direction: column;
  align-items: center;
  row-gap: 1vh;
}

footer a,
footer span {
  font-weight: 800;
}

footer p {
  width: 40%;
}

footer a {
  color: rgb(69, 114, 159);
}
</style>