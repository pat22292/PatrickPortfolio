<template>
  <div>
    <div class="button-background"></div>
    <div
      v-tooltip.left="'Double Click'"
      class="toggle-btn"
      @dblclick="(showing = !showing), menu()"
    >
      <span class="one"></span>
      <span class="two"></span>
      <span class="bottom"></span>
    </div>
    <div class="menu">
      <div class="data">
        <ul>
          <li>Navigation</li>
          <li><a href="#">Home</a></li>
          <li><a href="#">Our Story</a></li>
          <li><a href="#">Services</a></li>
          <li><a href="#">Contact</a></li>
        </ul>
      </div>
    </div>
    <!-- <FullPageMenu/> -->
    <!-- <div  @click="menu()" class="toggle-btn menuToggle">
          <span class="one"></span>
          <span class="two"></span>
          <span class="bottom"></span>
     </div> -->

    <!-- <button class="menuToggle" @click="menu()">Menu</button> -->

    <FirstLoad />
    <img class="company-logo" src="../assets/images/patlogo2.png" alt="#" />

    <nuxt />
  </div>
</template>
<script>
import FirstLoad from "~/components/FirstLoad.vue";
import FullPageMenu from "~/components/FullPageMenu.vue";

export default {
  data() {
    return {
      showing: false,
    };
  },
  asyncData() {
    return new Promise((resolve) => {
      setTimeout(function () {
        resolve({});
      }, 1000);
    });
  },
  mounted() {
    window.addEventListener("load", () => {
      document.getElementById("Loader").setAttribute("style", "display: none;");
    });

    //      if (process.browser) {
    //   window.onNuxtReady((app) => {
    //    document.getElementById("Loader").setAttribute('style', 'display: none;');
    //   })
    // }
  },
  updated: function () {},
  components: {
    FirstLoad,
    FullPageMenu,
  },
  methods: {
    menu() {
      document.body.scrollTop = 0;
      document.documentElement.scrollTop = 0;
      var tl3 = new TimelineMax({ paused: false });

      if (this.showing == true) {
        tl3.play();
      } else {
        tl3.reverse();
      }
      // tl3.paused();
      tl3

        .staggerFromTo(
          ".button-background",
          1,
          { scale: "0" },
          { scale: "100", autoAlpha: 1, ease: Power1.easeInOut },
          1
        )
        .add("show-menu")
        //  .staggerFromTo(".toggle-btn", .5, {rotation:0}, {rotation:360, ease:Linear.easeNonet}, .5)
        .staggerFromTo(
          ".bottom",
          0.1,
          { opacity: 1 },
          { opacity: 0, ease: Bounce.easeNonet },
          0.1
        )
        .staggerFromTo(
          ".one",
          0.1,
          { rotation: 0, y: 0 },
          { rotation: 45, y: 10, ease: Bounce.easeNonet },
          0.1
        )
        .staggerFromTo(
          ".two",
          0.1,
          { rotation: 0 },
          { rotation: -45, ease: Bounce.easeNonet },
          0.1
        )

        .staggerFromTo(
          "body",
          0.15,
          { overflow: "initial" },
          { overflow: "hidden" },
          0.75
        )

        .staggerFromTo(
          ".menu",
          0.15,
          { autoAlpha: 0 },
          { display: "initial", autoAlpha: 1 },
          "show-menu",
          0.75
        )
        .addPause();
      // TweenMax.fromTo("#Main-Menu", .5, {autoAlpha: 0}, {autoAlpha: 1,display: "flex", ease: Power4.easeInOut}, .5)
      // TweenMax.staggerFromTo(".menu", .5, {x: "-50px", autoAlpha: 0}, {x: "0px", autoAlpha: 1, ease: Power4.easeInOut}, .5)
    },
  },
};
</script>


<style lang="scss">
.page-enter-active,
.page-leave-active {
  transition: all 0.5s ease-out;
}
.page-enter,
.page-leave-active {
  opacity: 0.5;
  transform: translateY(-10px);
  transform-origin: 50% 50%;
}
body,
html {
  padding: 0;
  margin: 0;
  font-family: "Source Sans Pro", sans-serif;
  height: 100%;
  width: 100%;
}
.company-logo {
  margin: 40px;
  position: fixed;
  z-index: 1;
  width: 10%;
  @include for-desktop-up {
    width: 6%;
  }
}
.menuToggle {
  display: block;
  position: absolute;
  // top: 50px;
  // right: 50px;
  cursor: pointer;
  z-index: 500;

  -webkit-user-select: none;
  user-select: none;
}

#menuToggle span {
  display: block;
  width: 33px;
  height: 4px;
  margin-bottom: 5px;
  position: absolute;
  background: #cdcdcd;
  border-radius: 3px;

  transform-origin: 4px 0px;

  transition: transform 0.5s cubic-bezier(0.77, 0.2, 0.05, 1),
    background 0.5s cubic-bezier(0.77, 0.2, 0.05, 1), opacity 0.55s ease;
  .button-menu {
    cursor: pointer;
  }
}

.toggle-btn {
  position: fixed;
  margin: 1.4em;
  padding: 1em;
  width: 40px;
  height: 40px;
  right: 0;
  z-index: 102;
  cursor: pointer;
  //  z-index: 1;
}

span.one {
  position: absolute;
  width: 40px;
  height: 2px;
  background: gray;
}

span.two {
  position: absolute;
  width: 40px;
  height: 2px;
  background: gray;
  margin-top: 12px;
}
span.bottom {
  position: absolute;
  width: 30px;
  text-align: right;
  height: 2px;
  background: gray;
  margin-top: 24px;
}
.menu {
  z-index: 102;
  position: absolute;
  display: none;
  height: 100vh;
  width: 50%;
  //  top: -100vh;
}

.data {
  padding: 8em 0 0 2em;
  text-align: left;
}

ul {
  list-style: none;
}

li:first-child {
  color: #000;
  font-family: Poppins;
  font-size: 24px;
}

li:not(:first-child) {
  color: #000;
  font-size: 42px;
}

a {
  text-decoration: none;
  color: #000;
  font-family: Poppins;
}
.button-background {
  opacity: 0;
  //   height: 10px;
  // width:10px;
  background-color: #fff;
  border-radius: 50%;
  // position: absolute;

  position: fixed;
  margin: 1em;
  padding: 1em;
  width: 50px;
  height: 50px;
  right: 0;
  z-index: 101;
}
.tooltip {
  z-index: 102;
  border-radius: 10px;
  // ...
  background-color: #378de5;
  color: #fff;
  padding: 12px;
  margin: 0;
  opacity: 0.75;
  // font-weight: bolder;
  // border-radius: 5px;
  // margin: 5px;
  &.popover {
    $color: #378de5;

    .popover-inner {
      background: $color;
      color: black;
      padding: 24px;
      border-radius: 5px;
      box-shadow: 0 5px 30px rgba(black, 0.1);
    }

    .popover-arrow {
      border-color: $color;
    }
  }
}

.tooltip-arrow {
  border-width: 5px 0 10px 10px;
  border-top-color: transparent !important;
  border-right-color: transparent !important;
  border-bottom-color: transparent !important;
  // background-color: #378de5;
  color: #378de5;
  // right: -5px;
  left: calc(100%);
  margin-left: 0;
  margin-right: 0;
  width: 0;
  height: 0;
  border-style: solid;
  position: absolute;
}
</style>
