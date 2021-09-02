<template>
  <div class="menu">
    <div class="data">
      <ul>
        <li>Navigation</li>
        <li id="first"><a href="#">Home</a></li>
        <li id="second"><a href="#">Our Story</a></li>
        <li id="third"><a href="#">Services</a></li>
        <li id="fourth"><a href="#">Contact</a></li>
      </ul>
    </div>
  </div>
</template>

<script>
import $ from "jquery";
export default {
  asyncData() {
    return new Promise((resolve) => {
      setTimeout(function () {
        resolve({});
      }, 2000);
    });
  },
  methods: {
    //     closeMenu: () => {
    //       TweenMax.staggerFromTo(
    //         ".menu",
    //         2,
    //         { x: "0", autoAlpha: 0 },
    //         { x: "-50px", autoAlpha: 1, ease: Power4.easeInOut },
    //         2
    //       );
    //       TweenMax.staggerFrom(
    //         ".menu ul li",
    //         2,
    //         { x: 200, opacity: 0, ease: Expo.easeOut },
    //         0.3
    //       );
    //       TweenMax.fromTo(
    //         "#Main-Menu",
    //         0.5,
    //         { autoAlpha: 1 },
    //         { autoAlpha: 0, display: "none", ease: Power4.easeInOut },
    //         0.5
    //       );
    //       document
    //         .getElementById("Main-Menu")
    //         .setAttribute("style", "display: none;");
    //     },
  },
  mounted() {
    var t1 = new TimelineMax({ paused: true });

    t1.to(".one", 0.8, {
      y: 6,
      rotation: 45,
      ease: Expo.easeInOut,
    });
    t1.to(".two", 0.8, {
      y: -6,
      rotation: -45,
      ease: Expo.easeInOut,
      delay: -0.8,
    });

    t1.to(".menu", 2, {
      top: "0%",
      ease: Expo.easeInOut,
      delay: -2,
    });

    t1.staggerFrom(
      ".menu ul li",
      2,
      { x: 200, opacity: 0, ease: Expo.easeOut },
      0.3
    );

    t1.to(".first", 0.8, {
      y: 6,
      rotation: 45,
      ease: Expo.easeInOut,
    });
    t1.reversed();
    $(document).on("click", ".toggle-btn", function () {
      t1.reversed(!t1.reversed());
    });
    $(document).on("click", "a", function () {
      t1.reversed(!t1.reversed());
    });
  },
};
</script>

<style lang="scss" scoped>
@keyframes show {
  from {
    transform: translateX(-5000px);
  }
  to {
    transform: translateX(0);
  }
}
#menuContainer {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
}
#Main-Menu {
  display: none;
  //    animation: show 500ms ease-in-out;
}
.menu-background {
  // background-color: blue;
  background-color: rgb(255, 255, 255); /* Fallback color */
  background-color: black;
  // background-color: rgba(216, 216, 216, 0.4); /* Black w/ opacity */
  // display: flex;
  flex-direction: column;
  justify-content: center;
  justify-items: center;
  align-items: center;
  vertical-align: middle;
  width: 100vw;
  height: 100vh;
  margin: 0;
  padding: 0;
  position: fixed;

  z-index: 105;
  .menu-container {
    z-index: 105;
    height: 700px;
    width: 500px;
    background-color: black;
    z-index: 20;
    vertical-align: middle;
    overflow: auto;
    opacity: 1;
    p {
      margin: 20px;
      text-align: justify;
    }
  }
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
  background: #000;
  margin-top: 24px;
}
.menu {
  z-index: 101;
  position: absolute;
  background: #0675f3;
  height: 100vh;
  width: 100%;
  // top: -100vh;
}

.data {
  padding: 8em 0 0 2em;
  text-align: left;
}

ul {
  list-style: none;
}

li:first-child {
  color: grey;
  font-family: Poppins;
  font-size: 24px;
}

li:not(:first-child) {
  color: #fff;
  font-size: 42px;
}

a {
  text-decoration: none;
  color: #fff;
  font-family: Poppins;
}
</style>
