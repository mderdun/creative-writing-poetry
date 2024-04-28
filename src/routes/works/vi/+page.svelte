<script>
    // Importing necessary components and libraries
    import WorksHead from "$lib/components/WorksHead.svelte"; // Component for the header of the works
    import { cursorColor } from "$lib/stores.js"; // Store for managing cursor color
    import { onMount } from "svelte"; // Svelte lifecycle method
    import { Canvas } from "@threlte/core"; // Core Canvas component from threlte library
    import Scene from "$lib/components/Scene.svelte"; // Scene component for 3D rendering

    // On mount lifecycle method to set the cursor color
    onMount(() => {
        cursorColor.set("#0007a7");
    });
</script>

<!-- Main body of the page -->
<div id="body" class="flex flex-col h-full">
    <!-- Header of the works -->
    <div class="z-20">
        <WorksHead title="Ode on a Polish Urn" />
    </div>
    <!-- 3D rendering area -->
    <div id="3d" class="h-full flex-grow z-10">
        <Canvas>
            <Scene />
        </Canvas>
    </div>
    <!-- Overlay with SVG for navigation -->
    <div id="overlay" class="z-20">
        <svg
                width="50"
                height="50"
                viewBox="0 0 24 24"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
                stroke="currentColor"
        >
            <path
                    d="M5.65698 9.17157L4.24276 7.75735L0.00012207 12L4.24276 16.2426L5.65698 14.8284L3.82858 13H10.0001V11H3.82851L5.65698 9.17157Z"
                    stroke-linecap="round" stroke-linejoin="round"
            />
            <path
                    d="M14.0001 11V13H20.1716L18.3432 14.8284L19.7574 16.2426L24.0001 12L19.7574 7.75735L18.3432 9.17157L20.1717 11H14.0001Z"
                    stroke-linecap="round" stroke-linejoin="round"
            />
        </svg>
        <p class="font-bold">Drag to rotate.</p>
    </div>
    <!-- Loader displayed while the page is loading -->
    <div id="loader" class="absolute top-0 left-0 w-full h-full flex justify-center items-center -z-0">
        <div class="text-2xl">Loading...</div>
    </div>
</div>

<!-- Styling for the page -->
<style>
    /* Styling for the body */
    #body {
        background-color: white;
        color: #0007a7;
        height: 100vh;
    }
    /* Styling for the 3D rendering area */
    #3d {
        cursor: none;
    }

    /* Styling for the overlay */
    #overlay {
        position: fixed;
        display: flex;
        flex-direction: column;
        align-items: center;
        bottom: 20px;
        left: 50%;
        transform: translateX(-50%);
        padding: 10px;
        border-radius: 5px;
        color: white;
    }
</style>