<script>
    import WorksHead from '$lib/components/WorksHead.svelte';
    import { onMount } from 'svelte';
    import {cursorColor} from "$lib/stores.js";
    import anime from "animejs";

    onMount(() => {
        cursorColor.set("#ff0000");

        const drag = document.querySelector('.drag')

        drag.addEventListener('mouseover', function (e) {
            // If the word is already invisible (opacity is 0), do nothing
            if (window.getComputedStyle(e.target).opacity === '0') {
                return;
            }
            anime({
                targets: e.target,
                duration: 600,
                opacity: 0
            });
        });
    });
</script>

<div id="body" class="h-screen bg-[#696170] text-white">
    <WorksHead title="the way we love is like we're here but we're not" />
    <div id="poem" class="flex items-center justify-center space-x-8 h-[90%]">
        <div class="stanza">
            <p>eyes so sore they must be</p>
            <p>screen-glazing alll day</p>
            <p>that thick film <span class="w-10 inline-block" />thuggish-</p>
            <p>lodging <span class="w-10 inline-block" />itself in likeness</p>
            <p>the rock in goliath eyes</p>
        </div>
        <div class="stanza heart bg-red">
            <p>what you know about love?</p>
            <p>you ever flirted over insta?</p>
            <p class="text-sm animate-pulse text-yellow-300 blur-[0.8px]">the heart is as big as it wants to be</p>
            <p class="drag hover:hidden">drag me</p>
        </div>
        <div class="stanza">
            <p>is sluggish if not david</p>
            <p>that slings mud slingingly</p>
            <p>out <span class="w-10 inline-block" />of ogreish ways</p>
            <p>beating down <span class="w-10 inline-block" />on</p>
            <p>our own atom-ridden times</p>
        </div>
    </div>
</div>

<style>
    .stanza {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        font-size: 1.25rem;
        line-height: 1.75rem;
    }

    .heart {
        width:200px;
        height:200px;
        background:
                radial-gradient(90% 90% at 60% 65%, transparent calc(64% - 1px), #ff0000 64%, transparent calc(64% + 1px)) top left,
                radial-gradient(90% 90% at 40% 65%, transparent calc(64% - 1px), #ff0000 64%, transparent calc(64% + 1px)) top right,
                linear-gradient(to bottom left,     transparent calc(43% - 1px), #ff0000 43%, transparent calc(43% + 1px)) bottom left ,
                linear-gradient(to bottom right,    transparent calc(43% - 1px), #ff0000 43%, transparent calc(43% + 1px)) bottom right;
        background-size:50% 50%;
        background-repeat:no-repeat;
        border:10px dotted red;
        overflow:hidden;
        resize:both;
    }
    .drag {
        position: absolute;
        bottom: calc(-85px + 90vh / 2);
        right: calc(-35px + (100vw - 200px) / 2);
        font-size: 12px;
        color: white;
        transform: rotate(-45deg);
        margin: 10px
    }
</style>