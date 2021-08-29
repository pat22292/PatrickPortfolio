<template>
<div id="Loader">
      <div id="loading">
<div class="svg-load">
<svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
	 viewBox="0 0 728 430" style="enable-background:new 0 0 728 430;" xml:space="preserve">
<style type="text/css">
	.st0{opacity:0.19;}
	.st1{fill:#414042;}
	.st2{opacity:0.3;fill:#27AAE1;}
	.st3{fill:#27AAE1;}
</style>

<g id="Front">
	<path id="T" class="st1" d="M715.9,23.7l-10.5,27.2c-1.7,4.5-8.5,7.7-16.2,7.7L623,59.3c-7.8,0-14.5,3.2-16.2,7.7l-51.6,133.7
		l-70.5,182.3c-1.7,4.5-8.5,7.7-16.2,7.7h-48.1l0.3-0.8h-0.3l73.1-189.3l49.9-129.3c2.4-6.2-5.5-12.2-16.2-12.2h-70.6
		c-10.7,0-18.6-5.9-16.2-12.1L450.5,20c1.7-4.5,8.5-7.7,16.2-7.7l233-0.8C710.4,11.5,718.3,17.4,715.9,23.7z"/>
	<path id="a3" class="st2" d="M262,96c-19.4,0-36.3,8-40.6,19.4l-10.5,27.7l-22,56.9h61.4l22-56.9h145.5l-54.6,141.4H217.7
		l14.5-37.4h-61.4l-14.5,37.4l-18.2,47.1l-34.3,90h61.4l34.3-90H345L311,420.7h61.5l33.5-89.2h0.5l18.2-47.1l54.6-141.4l6.4-16.6
		c6-15.6-13.8-30.4-40.6-30.4H262z"/>
	<path id="A2" class="st2" d="M273.1,96c-19.4,0-36.3,8-40.6,19.4L222,143.1L200,200h61.4l22-56.9h145.5l-54.6,141.4H228.8
		l14.5-37.4h-61.4l-14.5,37.4l-18.2,47.1l-34.3,90h61.4l34.3-90h145.6l-34.1,89.2h61.5l33.5-89.2h0.5l18.2-47.1l54.6-141.4l6.4-16.6
		c6-15.6-13.8-30.4-40.6-30.4H273.1z"/>
	<path id="A" class="st3" d="M283.2,96c-19.4,0-36.3,8-40.6,19.4L232,143.1L210,200h61.4l22-56.9h145.5l-54.6,141.4H238.8l14.5-37.4
		h-61.4l-14.5,37.4l-18.2,47.1l-34.3,90h61.4l34.3-90h145.6l-34.1,89.2h61.5l33.5-89.2h0.5l18.2-47.1l54.6-141.4l6.4-16.6
		c6-15.6-13.8-30.4-40.6-30.4H283.2z"/>
	<path id="P" class="st1" d="M401.1,11.5c10.7,0,18.6,5.9,16.2,12.2l-13.5,34.9L389.4,96H328l14.5-37.4H210.2
		c-7.8,0-14.5,3.2-16.2,7.7l-46.9,121.5c-2.4,6.2,5.5,12.2,16.2,12.2h111.3c7.8,0,14.5-3.2,16.2-7.7l19-49.2h61.4l-22,56.9
		L334,239.3c-1.7,4.5-8.5,7.7-16.2,7.7H137.4c-7.8,0-14.5,3.2-16.2,7.7L72,382.3c-1.7,4.5-8.5,7.7-16.2,7.7H28.5
		c-10.7,0-18.6-5.9-16.2-12.2L62.7,247L80.9,200l54.6-141.4l15-39.3c1.7-4.5,8.5-7.7,16.2-7.7H401.1z"/>
</g>
</svg>
</div>
    </div>
    </div>
</template>

<script>
export default {
    mounted(){
          var tl2 = new TimelineMax({paused:false});

tl2
   .fromTo("#A", 2, {x: -30, autoAlpha: 0 }, {x: 0,autoAlpha: 1, ease: Power4.easeInOut, repeat: 2}, .1,)
   .fromTo("#A2", 2, {x: -30}, {x: 0, ease: Power3.easeInOut, repeat: 2}, 1,)
   .add('end')
   .fromTo("#a3", 2, {x: -30}, {x: 0,ease: Power2.easeInOut, repeat: 2}, 1,)
   .to("#loading", 1, {autoAlpha: 0,scale: 0.8, display: "none", ease: Power4.easeInOut,},'end', 0.5)
    }
}
</script>

<style lang="scss">
#Loader{
	position: absolute;
	z-index: 103;
	width: 100vw;
	height: 100vh;
	background-color: #FBFBFF;
	margin: 0;
	padding: 0;
}
  #loading{
      display: flex;
  align-items: center;
  justify-content: center;
    width: 100vw;
    height: 100vh;

    background-color: #FBFBFF;
  .svg-load{
    width: 30%;
        @include for-desktop-up {
        width: 10%;
    }
  }
  }
</style>
