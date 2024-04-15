<script>
    import WorksHead from "$lib/components/WorksHead.svelte";
    import { cursorColor } from "$lib/stores.js";
    import { onMount } from "svelte";
    import { Canvas } from "@threlte/core";
    import Urn from "$lib/components/Urn.svelte";

    onMount(() => {
        cursorColor.set("#0007a7");
    });
</script>

<div id="body" class="flex flex-col h-full">
<WorksHead title="Ode on a Polish Urn" />
<div id="3d" class="h-full flex-grow">
    <Canvas>
        <Urn />
    </Canvas>
</div>
</div>

<style>
    #body {
        background-color: #e4e4e2;
        color: #0007a7;
        height: 100vh;
    }
    #3d {
        cursor: none;
    }
</style>