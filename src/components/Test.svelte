<script>
  import { Canvas } from '@threlte/core';
  import Scene from './Scene.svelte';
  import { T } from '@threlte/core';
  import { XR, Controller, XRButton } from '@threlte/xr';
  import { OrbitControls } from '@threlte/extras';
</script>

<div class="relative min-h-dvh w-full">
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
  <XRButton mode="immersive-ar" />
</div>