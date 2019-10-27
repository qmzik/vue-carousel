<template>
  <div class="carousel">
    <transition :name="`carousel-${swipeDirection}`">
      <img v-hammer:swipe="swipeImage"
          :key="currentImgIndex"
          :src="images[currentImgIndex].src"
          :alt="images[currentImgIndex].name"
          class="carousel__img"
      >
    </transition>
  </div>
</template>

<script>
const LEFT_DIRECTION = "left";
const RIGHT_DIRECTION = "right";

export default {
  name: 'Carousel',
  props: {
    images: {
      type: Array
    }
  },
  data() {
    return {
      currentImgIndex: 0,
      swipeDirection: ''
    }
  },
  methods: {
    swipeImage(event) {
      const hammerLeft = 2;
      const hammerRight = 4;

      if (event.direction === hammerRight) {
          this.swipeDirection = RIGHT_DIRECTION;
          this.swipeToPrevious();
      } else if (event.direction === hammerLeft) {
          this.swipeDirection = LEFT_DIRECTION;
          this.swipeToNext();
      }
    },
    swipeToNext() {
      if (this.currentImgIndex < this.images.length - 1) {
          this.currentImgIndex++;
      } else {
          this.currentImgIndex = 0;
      }
    },
    swipeToPrevious() {
      if (this.currentImgIndex > 0) {
          this.currentImgIndex--;
      } else {
          this.currentImgIndex = this.images.length - 1;
      }
    },
    selectCurrentImg(index) {
      if (index < this.currentImgIndex) {
          this.swipeDirection = RIGHT_DIRECTION;
      } else {
          this.swipeDirection = LEFT_DIRECTION;
      }
      this.currentImgIndex = index;
    }
  }
}
</script>

<style scoped>
.carousel {
    position: relative;
    overflow: hidden;
    height: 100%;
}

.carousel__img {
    width: 100%;
}

.carousel-left-enter-active,
.carousel-left-leave-active,
.carousel-right-enter-active,
.carousel-right-leave-active {
    transition: transform 0.5s;
}

.carousel-left-leave-active,
.carousel-right-leave-active {
    position: absolute;
}

.carousel-left-enter {
    transform: translateX(100%);
}

.carousel-left-enter-to,
.carousel-right-enter-to {
    transform: translateX(0);
}

.carousel-right-enter {
    transform: translateX(-100%);
}

.carousel-left-leave-to {
    transform: translateX(-100%);
}

.carousel-right-leave-to {
    transform: translateX(100%);
}
</style>
