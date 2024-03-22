<script>
  import { T } from '@threlte/core';
  import Plane from './Plane.svelte';
</script>

<T.DirectionalLight intensity={5} position={[0, 10, 0]} color="#ffbbff"/>
<Plane />