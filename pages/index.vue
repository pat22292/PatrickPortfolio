<template>
  <div class="grid-container">
    <!-- <FullPageMenu/> -->

    <div id="backgroundSVG"></div>
    <div class="left-area">
      <div class="content">
        <!-- <h1>Hi, our team is ready to help you.</h1> -->
        <div
          v-for="image in images"
          :class="`title-slide text-` + image.id"
          :key="image.id"
        >
          <h1>{{ image.title }}</h1>
          <p>
            Hi, I'm a freelancer developer and graphics designer, if you need
            something just leave a message.
          </p>
          <n-link to="/main" class="myButton" no-prefetch>{{
            image.buttonName
          }}</n-link>
          <!-- <button class="button button2"><n-link to="/main" no-prefetch>SVG TEST</n-link></button> -->
        </div>
      </div>
    </div>
    <div class="right-area">
      <transition name="fade">
        <ImageGallery :images="images" />
      </transition>
    </div>
    <div class="left-area-2">
      <div class="content-2">
        <!-- <h1>Hi, our team is ready to help you.</h1> -->
        <div
          v-for="image in images"
          :class="`title-slide safari text-` + image.id"
          :key="image.id"
        >
          <h1>{{ image.title }}</h1>
          <p>
            Hi, we are group of freelancer developers and graphics designer, if
            you need something just leave us a message.
          </p>
          <!-- <a href="#" class="myButton">Main</a> -->
          <n-link class="myButton" to="/main" no-prefetch>{{
            image.buttonName
          }}</n-link>
          <!-- <n-link to="/" no-prefetch> <button class="button button2">  SVG TEST</button></n-link> -->
        </div>

        <!-- <n-link to="/main" no-prefetch>About</n-link> -->
      </div>
    </div>
    <div class="menu-area"></div>
  </div>
</template>

<script>
import ImageGallery from "~/components/ImageGallery.vue";
import FullPageMenu from "~/components/FullPageMenu.vue";

export default {
  asyncData() {
    return new Promise((resolve) => {
      setTimeout(function () {
        resolve({});
      }, 200);
    });
  },
  data() {
    return {
      images: [
        {
          id: "1",
          title: "Decent Graphics design.",
          location: require("~/assets/svg/3d3.svg"),
          buttonName: "Check Designs",
        },
        // {id: "2",title: "Isn't Cool? we can make one for you.", location: require('~/assets/images/van6.gif')},
        {
          id: "2",
          title: "Cool right? let's build yours.",
          location: require("~/assets/svg/van-shadowed.svg"),
          buttonName: "Check Mob. App",
        },
        {
          id: "3",
          title: "Hi, Do you need a developer?",
          location: require("~/assets/svg/dev.svg"),
          buttonName: "Check Web / App",
        },
      ],
    };
  },
  updated() {
    document.firstElementChild.style.zoom = "reset";
  },

  components: {
    ImageGallery,
    FullPageMenu,
  },
};
</script>

<style lang="scss">
// .fade-enter-active,
// .fade-leave-active {
//   transition: opacity 0.5s;
//   transform: translateX(-10px);
//   transform-origin: 50% 50%;
// }
// .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
//   transform: translateX(-10px);
//   transform-origin: 50% 50%;
// }
/* Transitions using the page hook */

#Preloading {
  position: absolute;
}
@supports (display: grid) {
  .grid-container {
    -ms-grid-rows: 50% 50%;
    grid-template-rows: 50% 50%;

    display: -webkit-grid;
    display: -ms-grid;
    display: grid;
    height: 100vh;
    width: 100vw;
    -ms-grid-columns: 100%;

    grid-template-areas:
      "right-area"
      "left-area";

    @include for-desktop-up {
      -ms-grid-rows: 100%;
      grid-template-rows: 100%;
      -ms-grid-columns: 50% 50%;
      grid-template-columns: 50% 50%;
      grid-template-areas: "left-area right-area";
    }
    @include for-tablet-landscape-up {
      -ms-grid-rows: 100%;
      grid-template-rows: 100%;
      -ms-grid-columns: 50% 50%;
      grid-template-columns: 50% 50%;
      grid-template-areas: "left-area right-area";
    }

    @include for-Square {
      grid-template-rows: 100%;
      grid-template-columns: 50% 50%;
      grid-template-areas: "left-area right-area";
    }

    .left-area-2 {
      display: none;
    }
    .left-area {
      z-index: 1;
      display: initial;
      grid-area: left-area;
      -ms-grid-row: 2;
      @include for-desktop-up {
        -ms-grid-row: 1;
        -ms-grid-column: 1;
      }
      .content-2 {
        display: none;
      }
      .content {
        position: absolute;

        display: flex;
        // justify-content: center;
        flex-direction: column;
        margin: 0 40px 0 100px;
        height: auto;
        // margin: 50px;
        @include for-desktop-up {
          justify-content: center;
        }
        @include for-tablet-landscape-up {
          margin: 0px 0 0 50px;
        }
        .title-slide {
          // top: 50vh;
          background-color: #ffffff;
          height: 25vh !important;
          position: fixed;
          width: 80vw;
          top: 45vh;
          @include for-desktop-up {
            width: 45vw;
            top: 27vh;
            height: 45vh !important;
          }
          @include for-Square {
            width: 30vw;
            top: 27vh;
          }
          @include for-laptop {
            top: 30vh;
          }
          @include for-tablet-landscape-up {
            width: 45vw;
            top: 25vh;
          }
        }
        h1 {
          text-shadow: 2px 2px 2px rgba(0, 0, 0, 0.2);
          font-size: 6rem;
          line-height: 6rem;
          color: #424242;
          padding: 0;
          margin: 0;

          @include for-desktop-up {
            font-size: 6rem;
            line-height: 6rem;
          }
          @include for-laptop {
            font-size: 4rem;
            line-height: 4.5rem;
          }
          @include for-Square {
            font-size: 3.5rem;
            line-height: 3.5rem;
          }
          @include for-tablet-landscape-up {
            font-size: 3.25rem;
            line-height: 3.25rem;
          }
        }
        p {
          font-size: 1.75rem;
          line-height: 1.75rem;
          color: #424242;
          @include for-Square {
            font-size: 1.5rem;
            line-height: 1.5rem;
          }
          @include for-desktop-up {
            font-size: 1.5rem;
            line-height: 1.5rem;
          }
          @include for-tablet-landscape-up {
            font-size: 1rem;
            line-height: 1rem;
          }
        }
        .button {
          background-color: #4caf50; /* Green */
          border: none;
          color: white;
          padding: 10px 20px;
          text-align: center;
          text-decoration: none;
          display: inline-block;
          font-size: 1rem;
          margin: 2px 2px;
          -webkit-transition-duration: 0.4s; /* Safari */
          transition-duration: 0.4s;
          cursor: pointer;
          z-index: 1000;
        }
        .button2 {
          background-color: white;
          color: #424242;
          border: 2px solid #25aae1;
        }

        .button2:hover {
          background-color: #25aae1;
          color: white;
        }
      }
    }
    .right-area {
      grid-area: right-area;
      -ms-grid-row: 1;

      @include for-desktop-up {
        -ms-grid-column: 2;
      }
    }
  }
}

/*********older Safari and messenger******/
.left-area {
  display: none;
}
.left-area-2 {
  padding-top: 50vh;

  @include for-tablet-landscape-up {
    padding-top: 15vh;
    padding-left: 50%;
  }

  .safari {
    position: fixed;

    h1 {
      text-shadow: 2px 2px 2px rgba(0, 0, 0, 0.2);
      font-size: 6rem;
      line-height: 6rem;
      color: #424242;
      padding: 0;
      margin: 0;
      @include for-tablet-landscape-up {
        font-size: 4rem;
        line-height: 4rem;
      }
    }
  }
  .content-2 {
    position: absolute;
    margin: 50px;
    @include for-tablet-landscape-up {
      margin: 0;
    }
    p {
      font-size: 1.5rem;
      line-height: 1.5rem;
      @include for-tablet-landscape-up {
        font-size: 1.25rem;
        line-height: 1.25rem;
      }
    }
  }
}

/******SUPPORT FOR EDGE******/

@supports (display: -ms-grid) {
  .grid-container {
    -ms-grid-rows: 50% 50%;
    grid-template-rows: 50% 50%;
    display: -webkit-grid;
    display: -ms-grid;

    height: 100vh;
    width: 100vw;
    -ms-grid-columns: 100%;

    grid-template-areas:
      "right-area"
      "left-area";

    @include for-desktop-up {
      -ms-grid-rows: 100%;
      -ms-grid-columns: 50% 50%;
    }
    @include for-tablet-landscape-up {
      -ms-grid-rows: 100%;
      -ms-grid-columns: 50% 50%;
    }

    .left-area-2 {
      display: none;
    }
    .left-area {
      display: initial;
      grid-area: left-area;
      -ms-grid-row: 2;
      @include for-desktop-up {
        -ms-grid-row: 1;
        -ms-grid-column: 1;
      }

      .content {
        position: absolute;
        z-index: 1;
        display: flex;
        // justify-content: center;
        flex-direction: column;
        margin: 0 40px 0 100px;
        height: 100%;
        // margin: 50px;
        @include for-desktop-up {
          justify-content: center;
        }
        @include for-tablet-landscape-up {
          margin: 0px 0 0 50px;
        }
        .title-slide {
          top: 50vh;
          // background-color: #ffffff;
          height: 100vh !important;
          position: fixed;
          width: 80vw;

          @include for-desktop-up {
            width: 44vw;
            height: 100vh !important;
            top: 27vh;
          }
          @include for-tablet-landscape-up {
            width: 45vw;
            top: 25vh;
            height: 100vh !important;
          }
        }
        h1 {
          text-shadow: 2px 2px 2px rgba(0, 0, 0, 0.2);
          font-size: 6rem;
          line-height: 6rem;
          color: #424242;
          padding: 0;
          margin: 0;
          @include for-desktop-up {
            font-size: 6rem;
            line-height: 6rem;
          }
          @include for-Square {
            font-size: 3rem;
            line-height: 3em;
          }
          @include for-tablet-landscape-up {
            font-size: 3.25rem;
            line-height: 3.25rem;
          }
        }
        p {
          font-size: 1.75rem;
          line-height: 1.75rem;
          color: #424242;

          @include for-desktop-up {
            font-size: 2rem;
            line-height: 2rem;
          }
          @include for-tablet-landscape-up {
            font-size: 1rem;
            line-height: 1rem;
          }
        }
        .button {
          background-color: #4caf50; /* Green */
          border: none;
          color: white;
          padding: 10px 20px;
          text-align: center;
          text-decoration: none;
          display: inline-block;
          font-size: 1rem;
          margin: 2px 2px;
          -webkit-transition-duration: 0.4s; /* Safari */
          transition-duration: 0.4s;
          cursor: pointer;
          z-index: 1000;
        }
        .button2 {
          background-color: white;
          color: #424242;
          border: 2px solid #25aae1;
        }

        .button2:hover {
          background-color: #25aae1;
          color: white;
        }
      }
    }
    .right-area {
      grid-area: right-area;
      -ms-grid-row: 1;

      @include for-desktop-up {
        -ms-grid-column: 2;
      }
    }
  }
}

#backgroundSVG {
  position: fixed;
  background-image: url(../assets/svg/back-4.svg);
  background-position: center;
  background-attachment: fixed;
  background-repeat: no-repeat;
  background-size: 380%;
  height: 100vh;
  width: 100%;
  // overflow: hidden;
  z-index: 1;
  @include for-desktop-up {
    background-size: cover;
  }
}

.myButton {
  -moz-box-shadow: inset 0px 1px 0px 0px #bbdaf7;
  -webkit-box-shadow: inset 0px 1px 0px 0px #bbdaf7;
  box-shadow: inset 0px 1px 0px 0px #bbdaf7;
  background: -webkit-gradient(
    linear,
    left top,
    left bottom,
    color-stop(0.05, #79bbff),
    color-stop(1, #378de5)
  );
  background: -moz-linear-gradient(top, #79bbff 5%, #378de5 100%);
  background: -webkit-linear-gradient(top, #79bbff 5%, #378de5 100%);
  background: -o-linear-gradient(top, #79bbff 5%, #378de5 100%);
  background: -ms-linear-gradient(top, #79bbff 5%, #378de5 100%);
  background: linear-gradient(to bottom, #79bbff 5%, #378de5 100%);
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#79bbff', endColorstr='#378de5',GradientType=0);
  background-color: #79bbff;
  -moz-border-radius: 6px;
  -webkit-border-radius: 6px;
  border-radius: 6px;
  border: 1px solid #84bbf3;
  display: absolute;
  cursor: pointer;
  color: #ffffff;
  font-family: Arial;
  font-size: 15px;
  font-weight: bold;
  padding: 6px 24px;
  z-index: 1000;
  text-decoration: none;
  text-shadow: 0px 1px 0px #528ecc;
}
.myButton:hover {
  background: -webkit-gradient(
    linear,
    left top,
    left bottom,
    color-stop(0.05, #378de5),
    color-stop(1, #79bbff)
  );
  background: -moz-linear-gradient(top, #378de5 5%, #79bbff 100%);
  background: -webkit-linear-gradient(top, #378de5 5%, #79bbff 100%);
  background: -o-linear-gradient(top, #378de5 5%, #79bbff 100%);
  background: -ms-linear-gradient(top, #378de5 5%, #79bbff 100%);
  background: linear-gradient(to bottom, #378de5 5%, #79bbff 100%);
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#378de5', endColorstr='#79bbff',GradientType=0);
  background-color: #378de5;
}
.myButton:active {
  // position: relative;
  top: 1px;
}
</style>
