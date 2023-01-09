<script lang="ts">
  import { gsap } from "gsap";
  import { ScrollTrigger } from "gsap/ScrollTrigger";

  import { onMount } from "svelte";

  gsap.registerPlugin(ScrollTrigger);

  let video;

  onMount(() => {
    gsap.to("#title", {
      opacity: 0,
      scale: 0.5,
      duration: 1.2,
      scrollTrigger: {
        trigger: "#section1",
        start: "70% center",
        scrub: true,
      },
    });

    gsap.to("#title2", {
      opacity: 1,
      scrollTrigger: {
        trigger: "#section1",
        start: "520% center ",
        scrub: true,
      },
    });

    ScrollTrigger.create({
      trigger: "#section1",
      end: "500%",
      pin: true,
      onUpdate: ({ progress }) => {
        video.currentTime = progress * 9;
      },
    });
  });
</script>

<section id="section1" class="relative grid h-screen place-items-center ">
  <header
    class="absolute top-0 flex w-full items-center justify-between border-b  border-gray-500 p-4 md:w-[80vw]"
  >
    <figure class="w-8">
      <img
        src="https://upload.wikimedia.org/wikipedia/commons/3/31/Apple_logo_white.svg"
        class="w-full"
      />
    </figure>
    <nav class="flex items-center gap-4">
      <a href="">Home</a>
      <a href="">Products</a>
      <a href="">Contact</a>
    </nav>
  </header>
  <h2
    id="title"
    class="absolute left-[25%] right-[25%] top-[50%] block  text-center text-9xl font-bold"
  >
    BatteryPro
  </h2>
  <video
    bind:this={video}
    src="/video-scroll.mp4"
    class="h-full w-full object-cover"
  />
  <h2
    id="title2"
    style:opacity={0}
    class="absolute left-[25%] right-[25%] top-[50%] block text-center  text-7xl font-bold "
  >
    Don't worry about him
  </h2>
</section>

<section id="section2" class=" grid h-screen place-items-center bg-red-500" />

<style>
</style>
