<script>
import { T } from '@threlte/core';
import { SheetObject } from '@threlte/theatre';
import Plane from './Plane.svelte';
import Ramsden from './Ramsden.svelte';
</script>

<T.DirectionalLight intensity={1} color="#ffffff" position={[0, 10, 10]} />
<T.DirectionalLight intensity={1} color="#ffffff" position={[10, 10, 0]} />

<T.AmbientLight intensity={2} color="#ffffff"/>
<Ramsden />
