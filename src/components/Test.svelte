<script>
  import { Canvas } from '@threlte/core';
  import Scene from './Scene.svelte';
  import { T } from '@threlte/core';
  import { XR, Controller, ARButton } from '@threlte/xr';
  import { OrbitControls } from '@threlte/extras';
</script>

<div class="relative min-h-dvh w-full">
  <Canvas>
    <XR>
      <Controller left />
      <Controller right />

      <T.Mesh>
        <T.BoxGeometry attach="geometry" />
        <T.MeshBasicMaterial attach="material" />
      </T.Mesh>

      <svelte:fragment slot="fallback">
        <Scene />
        <T.PerspectiveCamera makeDefault position.z={5}>
          <OrbitControls />
        </T.PerspectiveCamera>
      </svelte:fragment>
    </XR>
  </Canvas>
  <ARButton on:click={(event) => {
    alert('ARButton clicked');
  }} />
</div>