<script lang="ts">
  import { gsap } from 'gsap';
  import { ScrollTrigger } from 'gsap/ScrollTrigger';

  import { onMount } from 'svelte';

  gsap.registerPlugin(ScrollTrigger);

  let video;
  let scale = 1;

  onMount(() => {
    ScrollTrigger.create({
      trigger: '#section1',
      end: '500%',
      pin: true,
      markers: true,
      onUpdate: ({ progress }) => {
        scale = progress.toFixed(3) * 10;
        video.currentTime = progress * 9;
      },
    });
  });
</script>

<section
  id="section1"
  class="h-screen  border-b-4 border-purple-300 grid place-items-center relative"
>
  <video
    bind:this={video}
    src="/video-scroll.mp4"
    class="w-full h-full object-cover"
  />
  <div class="absolute top-0 left-0 box w-10 h-10 bg-blue-500" style:scale />
</section>

<section id="section2" class=" bg-red-500 h-screen grid place-items-center" />

<style>
</style>
