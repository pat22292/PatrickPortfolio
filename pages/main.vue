<template>
  <div>
    <!-- <Preloader/> -->
    <div id="main-page" class="mainpage">
      <!-- <h1>HEY</h1> -->

      <div class="main-content">
        <n-link to="/" class="myButton" no-prefetch>Home</n-link>

        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Quasi itaque
          ducimus ipsam tempora dolores veritatis excepturi assumenda recusandae
          vel beatae, officiis corrupti aspernatur! Praesentium ab magni
          officiis nesciunt perspiciatis delectus quod mollitia molestias ipsam
          cupiditate, ipsa voluptatem odit dolore sint dolorem. Commodi nostrum
          impedit quaerat dolore tempore! Odio provident laborum reprehenderit,
          est numquam sit suscipit natus ad omnis dolor cum inventore
          blanditiis, nostrum obcaecati laboriosam quas tenetur eius nihil nulla
          minus quae optio vitae expedita at? Ab fuga nam quas accusamus eum
          distinctio pariatur adipisci aliquam odit hic. Ex minima sed ullam
          assumenda quibusdam dignissimos, vitae dolores commodi fuga, hic et,
          harum asperiores saepe doloremque ipsa tenetur necessitatibus! Iure
          earum aut ex, ullam perferendis amet voluptas quasi expedita
          accusantium obcaecati consequatur quibusdam libero porro eligendi
          deleniti sunt nulla, a cupiditate exercitationem officiis aliquid?
          Quia tempora doloribus saepe sequi corporis totam dignissimos, dolor
          officiis debitis delectus enim. Facere, impedit soluta itaque eaque
          mollitia omnis non ipsum a quisquam ad blanditiis porro quae incidunt
          corrupti obcaecati enim magnam, cupiditate harum illum dignissimos
          saepe repellat, ipsa id. Delectus consequuntur cumque ab iste nam
          fugit placeat quam veritatis deleniti, eveniet distinctio labore
          dignissimos incidunt, ducimus excepturi, nihil est cum commodi animi
          dicta consequatur? At magni, iusto eius minus ea quo molestiae
          asperiores a enim consequatur unde consectetur, provident vero quod?
          Natus consequatur impedit delectus pariatur consequuntur voluptatibus
          esse obcaecati, voluptatum qui recusandae asperiores repudiandae alias
          consectetur itaque nihil iste fugiat maiores odio rem at. Libero
          voluptatibus, tempore nobis in quam ex perferendis inventore ipsa
          fugit ab! Explicabo debitis quisquam delectus odio expedita esse
          aperiam laudantium exercitationem rerum, vero architecto pariatur
          magni possimus alias et provident error ullam deserunt reiciendis
          ipsum similique laborum maxime! Omnis dolorem sed veritatis suscipit
          ex nam nihil eaque itaque. Recusandae labore corporis modi quam
          officia inventore vel earum sed. Rem quia dolores voluptas minus!
          Voluptatibus reprehenderit perspiciatis provident sequi? Cumque quo
          ullam consequuntur inventore. Iure facere, praesentium magni enim vel
          consequatur accusamus repellendus, autem numquam possimus dolor totam
          perferendis, laudantium recusandae. Earum minima eveniet, nihil
          distinctio, quas amet maxime adipisci consequuntur temporibus tenetur
          soluta autem tempore illum et exercitationem esse fuga? Placeat, totam
          molestiae tempora optio magnam vel atque blanditiis repellat
          voluptatibus porro id! Aut, nemo hic! Optio eveniet eum quae nobis.
          Sunt nesciunt, exercitationem maiores, architecto quam magni expedita
          maxime veniam nihil repudiandae at sapiente! Illo voluptatibus
          necessitatibus, libero dignissimos aliquam temporibus dolorem optio
          quo, nemo praesentium, in exercitationem.
        </p>
      </div>
    </div>
    <!-- <img src="~/assets/svg/van-shadowed.svg" alt="" width="50%"> -->
  </div>
</template>

<script>
import { TweenMax, TimelineMax, Power0 } from "gsap";

// import Preloader from '~/components/Preloader.vue'

export default {
  asyncData() {
    return new Promise((resolve) => {
      setTimeout(function () {
        resolve({});
      }, 200);
    });
  },
  components: {
    //  Preloader
  },
  mounted() {
    TweenMax.fromTo(
      "#main-page",
      1,
      { y: -10, opacity: 0 },
      { autoAlpha: 1, y: 0, ease: Power0.easeInOut },
      1.5
    );
  },
};
</script>

<style lang="scss" scoped>
.company-logo {
  display: hidden !important;
}
.mainpage {
  overflow: initial;
  padding-top: 100px;
  display: flex;
  z-index: 10;
  position: relative;
  .main-content {
    margin: 0 150px;
  }
  p {
    position: relative;
    text-align: justify;
    font-size: 2rem;
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
  display: inline-block;
  cursor: pointer;
  color: #ffffff;
  font-family: Arial;
  font-size: 15px;
  font-weight: bold;

  padding: 6px 24px;
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
  position: relative;
  top: 1px;
}
</style>
