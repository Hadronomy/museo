<script>
import { Canvas, T } from '@threlte/core';
import { OrbitControls, useProgress } from '@threlte/extras';
import { Studio } from '@threlte/theatre';
import { Controller, XR, XRButton } from '@threlte/xr';
import { tweened } from 'svelte/motion';
import { fade } from 'svelte/transition';

import Scene from './Scene.svelte';

const isDev = import.meta.env.DEV;

const { progress } = useProgress();
const tweenedProgress = tweened($progress, {
  duration: 800,
});
$: tweenedProgress.set($progress);
</script>

{#if $tweenedProgress < 1}
  <div
    transition:fade|local={{
      duration: 200
    }}
    class="wrapper"
  >
    <p class="loading">Loading</p>
    <div class="bar-wrapper">
      <div
        class="bar"
        style="width: {$tweenedProgress * 100}%"
      />
    </div>
  </div>
{/if}

<div class="relative min-h-dvh w-full">
  <Studio enabled={isDev} />
  <Canvas>
    <Scene />
    <XR>
      <Controller left />
      <Controller right />

      <svelte:fragment slot="fallback">
        <T.PerspectiveCamera makeDefault position.z={2}>
          <OrbitControls />
        </T.PerspectiveCamera>
      </svelte:fragment>
    </XR>
  </Canvas>
  <!-- <XRButton mode="immersive-ar" sessionInit={{
    requiredFeatures: ['image-tracking'],
    optionalFeatures: ['local-floor', 'bounded-floor', 'hand-tracking', 'layers']
  }}/> -->
  <XRButton mode="immersive-ar" />
</div>

<style>
  .wrapper {
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    background-color: white;
    display: flex;
    flex-direction: column;
    gap: 0.25rem;
    align-items: center;
    justify-content: center;
    color: black;
    z-index: 20;
  }
  .loading {
    font-size: 0.875rem;
    line-height: 1.25rem;
  }
  .bar-wrapper {
    width: 33.333333%;
    height: 10px;
    border: 1px solid black;
    position: relative;
  }
  .bar {
    height: 100%;
    background-color: black;
  }
</style>