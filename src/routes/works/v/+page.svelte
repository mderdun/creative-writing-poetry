<script>
    import WorksHead from '$lib/components/WorksHead.svelte';
    import { onMount } from 'svelte';
    import { cursorColor } from "$lib/stores.js";
    import anime from "animejs";

    onMount(() => {
        cursorColor.set("#ff0000");

        const drag = document.querySelector('.drag');

        drag.addEventListener('mouseover', function (e) {
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
            <p>the rock in goliath eye</p>
        </div>
        <div class="stanza heart bg-red">
            <p>what you know about love?</p>
            <p>you ever flirted over insta?</p>
            <p class="text-sm animate-pulse text-yellow-400 blur-[0.2px]">the heart is as big as it wants to be</p>
            <p class="drag hover:hidden">drag me</p>
        </div>
        <div class="stanza">
            <p>is sluggish if not david</p>
            <p>that slings mud slingingly</p>
            <p>down <span class="w-10 inline-block" />his ogreish ways</p>
            <p>beating <span class="w-10 inline-block" />on our own</p>
            <p>atom-ridden times</p>
        </div>
    </div>
</div>

<style>
    .stanza {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        font-size: 2rem;
        line-height: 2.25rem;
    }

    @media only screen and (max-width: 1024px) {
        .stanza {
            font-size: 1.25rem;
            line-height: 1.75rem;
        }
    }

    .heart {
        width: 500px;
        height: 300px;
        /*background: radial-gradient(90% 90% at 60% 65%, transparent calc(64% - 3px), #ff0000 64%, transparent calc(64% + 3px)) top left,*/
        /*radial-gradient(90% 90% at 40% 65%, transparent calc(64% - 3px), #ff0000 64%, transparent calc(64% + 3px)) top right,*/
        /*linear-gradient(to bottom left, transparent calc(43% - 3px), #ff0000 43%, transparent calc(43% + 3px)) bottom left,*/
        /*linear-gradient(to bottom right, transparent calc(43% - 3px), #ff0000 43%, transparent calc(43% + 3px)) bottom right;*/
        background-image: url("/imgs/heart.png");
        background-size: 100% 100%;
        background-repeat: no-repeat;
        border: 5px groove red;
        overflow: hidden;
        resize: both;
        animation: pulsate 0.1s ease-in-out infinite alternate;
    }

    @keyframes pulsate {
        100% {
            text-shadow:
                    0 0 2px white,
                    0 0 4px gold,
                    0 0 10px black;
            box-shadow: 0 0 7px #fff,
            0 0 10px #fff,
            0 0 21px #9f0a0a,
            0 0 42px #ff004d,
            0 0 82px #ff004d,
            0 0 92px #ff004d,
            inset 0 0 14px #9f0a0a;
        }
        0% {
            text-shadow:
                    0 0 2px white,
                    0 0 3px gold,
                    0 0 8px black;
            box-shadow: 0 0 7px #fff,
            0 0 9px #fff,
            0 0 18px #dd1818,
            0 0 37px #ff004d,
            0 0 69px #ff004d,
            0 0 83px #ff004d,
            inset 0 0 13px #a61111;
        }
    }

    .drag {
        position: absolute;
        bottom: calc(-150px + 90vh / 2);
        right: calc(-185px + (100vw - 200px) / 2);
        font-size: 12px;
        color: white;
        transform: rotate(-45deg);
        margin: 20px
    }
</style>