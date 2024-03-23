<script>
  import { T } from '@threlte/core';
  import { SheetObject } from '@threlte/theatre';
  import Plane from './Plane.svelte';

</script>

<T.DirectionalLight intensity={5} position={[0, 10, 0]} color="#ffbbff"/>
<SheetObject
  key="box",
  let:Transform
  let:Sync
>
  <Transform>
    <Plane />
  </Transform>
</SheetObject>