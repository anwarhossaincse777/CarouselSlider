<script setup>
import image1 from '../assets/images/image1.jpg'
import image2 from '../assets/images/image2.jpg'
import image3 from '../assets/images/image3.jpg'
import image4 from '../assets/images/image4.jpg'
import {reactive, ref} from "vue";

const activeIndex = ref(0)

const images = reactive(
    [
      {
        image: image1,
        title:"First slide label",
        text:"Some representative placeholder content for the first slide."
      },
      {
        image: image2,
        title:"Second slide label",
        text:"Some representative placeholder content for the first slide."
      },
      {
        image: image3,
        title:"Third slide label",
        text:"Some representative placeholder content for the first slide.",
      },
      {
        image: image4,
        title:"Fourth slide label",
        text:"Some representative placeholder content for the first slide.",
      },
    ]
)

const previousImage = (index) => {
  let length = images.length;
  if (index > 0) {
    activeIndex.value = index - 1;
  }else {
    activeIndex.value = length - 1;
  }

}
const nextImage = (index) => {
  let length = images.length - 1;
  if (index < length) {
    activeIndex.value = index + 1;
  } else {
    activeIndex.value = 0;
  }
}

</script>


<template>
  <div id="carouselExampleIndicators" class="carousel slide" data-bs-ride="carousel">
    <div class="carousel-indicators">
      <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="0" class="active" aria-current="true" aria-label="Slide 1"></button>
      <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="1" aria-label="Slide 2"></button>
      <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="2" aria-label="Slide 3"></button>
    </div>

    <template v-for="(image,index) in images" :key="index">
      <div class="carousel-inner">
        <div class="carousel-item active">
          <img :src="image.image" alt=""  :style="{width:'100%',height:'400px'}" v-show="index===activeIndex">
          <div class="carousel-caption d-none d-md-block">
            <h5>{{image.title}}</h5>
            <p>{{image.text}}</p>
          </div>
        </div>
      </div>

      <button @click="previousImage(index)" v-show="index===activeIndex" class="carousel-control-prev" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Previous</span>
      </button>
      <button @click="nextImage(index)" v-show="index===activeIndex" class="carousel-control-next" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Next</span>
      </button>
    </template>
  </div>
</template>




<style scoped>

</style>