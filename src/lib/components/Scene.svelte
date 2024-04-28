<script>
    // Importing the Urn component from the same directory
    import Urn from './Urn.svelte';
    // Importing the T object from the threlte core library
    import {T} from "@threlte/core";
    // Importing the OrbitControls, Suspense, and Text components from the threlte extras library
    import {OrbitControls, Suspense, Text} from "@threlte/extras";

</script>

<!-- Creating a PerspectiveCamera component from the T object -->
<!-- This camera is set as the default, positioned at [0, 7, 20], and has a field of view of 10 -->
<T.PerspectiveCamera
        makeDefault
        position={[0, 7, 20]}
        fov={10}
>
    <!-- Adding OrbitControls to the camera -->
    <!-- These controls allow for rotation and auto-rotation, with specified speeds -->
    <!-- Damping is enabled, zoom is disabled, and the polar angle is restricted to between PI/2.5 and PI/2.5 -->
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

<!-- Creating a Suspense component -->
<!-- This component will display a fallback UI while the Urn component is loading -->
<Suspense>
    <!-- Loading the Urn component -->
    <Urn/>
</Suspense>