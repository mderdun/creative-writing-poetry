<script>
    import Urn from './Urn.svelte';
    import {T} from "@threlte/core";
    import {OrbitControls, Suspense, Text} from "@threlte/extras";

</script>

<T.PerspectiveCamera
        makeDefault
        position={[0, 7, 20]}
        fov={10}
>
    <OrbitControls
            enableRotate
            autoRotate
            autoRotateSpeed={-1.35}
            rotateSpeed={0.5}
            enableDamping
            enableZoom={false}
            minPolarAngle={Math.PI / 2.5}
            maxPolarAngle={Math.PI / 2.5}
    />
</T.PerspectiveCamera>

<Suspense>
    <Urn/>
</Suspense>
