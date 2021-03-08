<template>
  <div class="container">
    <h3 class="regular">Have a look at our delicious delicacies..</h3>
    <div class="card-container">
      <div class="card" v-for="item in items" :key="item">
        <h4 class="bold">{{ item.name }}</h4>
        <div class="img-wrap">
          <img :src="item.image" />
        </div>
        <p class="regular">{{ item.description }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Inventory",
  data() {
    return {
      items: [
        {
          name: "Classic Glazed Doughnuts",
          image: "./images/donut.jpg",
          description:
            "Our original and the best recipe, the classic glazed doughnuts.",
        },
        {
          name: "Strawberry Doughnuts",
          image: "./images/pink.jpg",
          description:
            "What's better than doughnuts you ask? A doughnut with strawberries! ",
        },
        {
          name: "Oreo Doughnuts",
          image: "./images/oreo.jpg",
          description:
            "If there can be Oreo milkshakes, then how about Oreo doughnuts?",
        },
        {
          name: "Sprinkled Doughnuts",
          image: "./images/sprinkled.jpg",
          description:
            "Because sprinkles make everything better. Even the perfect doughnuts.",
        },
        {
          name: "Nutella Doughnuts",
          image: "./images/nutella.jpg",
          description:
            "Nutella filled dougnuts because calories is a foreign concept to us and we don't believe in it.",
        },
        {
          name: "Cinnamon Doughnuts",
          image: "./images/cinnamon.jpg",
          description:
            "A bit more Cinnamon, a bit more, just a tad bit more.",
        },
      ],
      
    };
  },
};
</script>

<style lang="scss" scoped>
.container {
  display: grid;
  place-items: center;

  .card-container {
    width: 90%;
    display: flex;
    flex-wrap: wrap;
  }
}

.card {
  display: flex;
  flex-direction: column;
  width: 380px;
  height: fit-content;
  max-height: 450px;
  margin: 15px;
  float: left;

  //   styling for Neumorphism
  border-radius: 14px;
  background: #f2f2f0;
  box-shadow: 6px 6px 8px #d3d3d1, -6px -6px 8px #ffffff;

  h4 {
    font-size: 24px;
    margin: 10px 0px 15px 15px;
    color: #d9695f;
  }

  img {
    width: 350px;
    max-width: 350px;
    height: auto;
    max-height: 300px;
    object-fit: cover;
    display: block;
    margin: 0 auto;
  }

  p {
    font-size: 18px;
    margin: 10px 15px;
  }
}
</style>
