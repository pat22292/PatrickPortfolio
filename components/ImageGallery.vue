<template>
  <div class="container">
    <div
      v-for="image in images"
      :class="`img-galleries slide-` + image.id"
      :key="image.id"
      :style="{ 'background-image': 'url(' + image.location + ')' }"
      width="1"
      height="1"
    ></div>

    <div id="increase" @click.stop="debouncedMyFunction"></div>
    <div id="decrease" @click.stop="debouncedMyFunction2"></div>
  </div>
</template>
<script>
import { TweenMax, TimelineMax, Power0, RoughEase } from "gsap";
import { debounce } from "lodash";

export default {
  props: ["images"],
  data() {
    return {};
  },
  mounted() {
    var slides = document.querySelectorAll(".img-galleries");
    var supportsWheel = false;
    var tl = new TimelineMax({ paused: true });
    var tl2 = new TimelineMax({ paused: true });

    for (var i = slides.length; i > 1; i--) {
      tl.add("intro")
        .staggerFromTo(
          ".slide-" + i,
          1,
          { autoAlpha: 1 },
          { opacity: 0, ease: RoughEase.easeInOut },
          0.25
        )
        .fromTo(
          ".slide-" + (i - 1),
          0.25,
          { opacity: 0 },
          { autoAlpha: 1, ease: RoughEase.easeInOut },
          "intro",
          0.25
        )
        .addPause();
    }

    for (var j = slides.length; j > 1; j--) {
      tl2
        .add("intro-text")
        .staggerFromTo(
          ".text-" + j,
          0.5,
          { autoAlpha: 1 },
          { opacity: 0, ease: RoughEase.easeInOut },
          0.5
        )
        .fromTo(
          ".text-" + (j - 1),
          0.5,
          { opacity: 0 },
          { autoAlpha: 1, ease: RoughEase.easeInOut },
          "intro-text",
          0.5
        )

        .addPause();
    }
    function DoSomething(e) {
      if (e.type == "wheel") supportsWheel = true;
      else if (supportsWheel) return;

      var delta = (e.deltaY || -e.wheelDelta || e.detail) >> 10 || 1;
      if (delta == 1) {
        tl2.play();
        tl.play();
      } else {
        tl2.reverse();
        tl.reverse();
      }
    }

    document.addEventListener("wheel", DoSomething);
    document.addEventListener("mousewheel", DoSomething);
    document.addEventListener("DOMMouseScroll", DoSomething);
    document.addEventListener("touchstart", handleTouchStart, false);
    document.addEventListener("touchmove", handleTouchMove, false);

    var xDown = null;
    var yDown = null;

    function getTouches(evt) {
      return (
        evt.touches || // browser API
        evt.originalEvent.touches
      ); // jQuery
    }

    function handleTouchStart(evt) {
      const firstTouch = getTouches(evt)[0];
      xDown = firstTouch.clientX;
      yDown = firstTouch.clientY;
    }

    function handleTouchMove(evt) {
      if (!xDown || !yDown) {
        return;
      }

      var xUp = evt.touches[0].clientX;
      var yUp = evt.touches[0].clientY;

      var xDiff = xDown - xUp;
      var yDiff = yDown - yUp;

      if (Math.abs(xDiff) > Math.abs(yDiff)) {
        /*most significant*/
        if (xDiff > 0) {
          tl.play();
          tl2.play();
          // //  document.getElementById("prevBtn").click();
        } else {
          //  document.getElementById("nextBtn").click();
          tl.reverse();
          tl2.reverse();
        }
      } else {
        if (yDiff > 0) {
          //  document.getElementById("prevBtn").click();
          tl.reverse();
          tl2.reverse();
        } else {
          // document.getElementById("nextBtn").click();
          tl.play();
          tl2.play();
        }
      }
      /* reset values */
      xDown = null;
      yDown = null;
    }
  },

  methods: {
    Increase() {
      var itemCount = this.images.length;
      if (this.counter < itemCount) {
        this.counter += 1;
        this.nextslide += 1;
      }
    },
    Decrease() {
      if (this.counter != 1) {
        this.counter -= 1;
        this.nextslide -= 1;
      }
    },
  },

  updated() {},
  created() {
    (this.debouncedMyFunction = debounce(this.Increase, 200, {
      leading: true,
      trailing: false,
    })),
      (this.debouncedMyFunction2 = debounce(this.Decrease, 200, {
        leading: true,
        trailing: false,
      }));
  },
};
</script>

<style lang="scss">
.slide-2 {
  background-image: url("../assets/images/van5.gif") !important;
  @include for-desktop-up {
    background-image: url("../assets/svg/van-shadowed.svg") !important;
  }
}
.container {
  display: block;
  padding: 0;
  margin: 0;
  h1 {
    // margin: 50px;
    color: #000;
  }

  #decrease {
    margin-left: 20px;
  }
  .img-galleries {
    background-color: #ffff;
    position: fixed;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    width: 100%;
    height: 50vh;
    z-index: -1;

    @include for-Square {
      height: 100vh;
      width: 50%;
    }
    @include for-desktop-up {
      height: 100vh;
      width: 50%;
    }
    @include for-tablet-landscape-up {
      width: 50%;
      height: 100vh;
    }
  }
}

// @supports (display: -ms-grid){
//   .slide-2{
//     background-image: url('../assets/images/van5.gif')!important;
//   }
// }

@supports not (display: grid) {
  .slide-2 {
    background-image: url("../assets/images/van5.gif") !important;
  }
}

@media screen and (-webkit-min-device-pixel-ratio: 0) {
  /* Safari and Chrome */
  // .flex-direction-nav-featured a{
  //     margin-top: 4%;
  // }

  /* Safari only override */
  // ::i-block-chrome, .slide-2{
  //      background-image: url('../assets/images/van5.gif')!important;
  // }
}
</style>
