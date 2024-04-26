<script>
    import WorksHead from "$lib/components/WorksHead.svelte";
    import { cursorColor } from "$lib/stores.js";
    import { onMount } from "svelte";

    onMount(() => {
        cursorColor.set("black");
    });
</script>

<div id="body" class="h-screen overscroll-none">
    <WorksHead title="so badly breaking it hurts" />
    <div id="poem">
        <img src="/imgs/badly_breaking.gif" class="flex flex-grow" />
    </div>
</div>

<style>
    img {
        height: 100vh;
        width: 100vw;
        object-fit: fill;
        z-index: -1;
        position: absolute;
        top: 0;
        left: 0;
    }

    #body {
        color: white;
        text-shadow:
                3px 3px 0 #000,
                -1px -1px 0 #000,
                1px -1px 0 #000,
                -1px 1px 0 #000,
                1px 1px 0 #000;
        height: 100vh;
        margin: 0;
        overflow-y: hidden;
    }
</style>