<script>
    import { onMount } from 'svelte';
    import { cursorColor } from "$lib/stores.js";
    import WorksHead from "$lib/components/WorksHead.svelte";

    onMount(() => {
        cursorColor.set("black");
    });
</script>

<div id="body">
    <WorksHead title="garden too concrete" />
    <div class="w-screen flex items-center justify-center">
    <div id="poem" class="text-xl w-1/3 flex flex-col justify-start items-start">
        <div id="p1" class="mb-12">
            <h1 class="rome">I.</h1>
            <p>Border crossings to retrieve my clothes</p>
            <p>I press my body into shape between poles</p>
            <p>A flag that waved up and a little to the side,</p>
            <p>that once strung with string and held by a peg</p>
            <p class="ml-14">now rolled in ask of being noticed by my foot</p>
            <p>this peg I assumed yours but was mine by mistake.</p>

            <p class="blocky">It was funny to see and to talk to older neighbours because we would talk about things like gardening that i knew little about besides it was the thing my mother did and my father didn’t. how would I grow up to be bigger than I already am? sometimes growing would feel like the difference between swallowing and throwing.</p>

            <p class="blocky">If not for the wind we would repeat thin-dry and aching gestures, and had I never been to your garden I would not have know to leave myself at the border, because your clothes are quite different to mine.</p>

            <p class="blocky">I learned that I could be less space than I thought I could.</p>
        </div>
        <div id="p2">
            <h1 class="rome">II.</h1>
            <p>My garden</p>
            <p>concrete limit of an embodied soul.</p>
            <div class="flex gap-32"><p>But my shirt</p><p>in your yard</p></div>
            <p class="ml-[20rem]">gives horizon to possibility</p>
        </div>
        <img src="/imgs/scribble.gif" class="mt-[-5rem] ml-16 -z-10"/>
    </div>
    </div>
</div>

<style>
    .rome {
        font-variant: small-caps;
        width: 100%;
        margin-bottom: 1.5rem;
    }

    .blocky {
        text-align: justify;
        text-justify: inter-character;
        margin-top: 1rem;
    }

    p {
        line-height: 1.5;
    }
</style>