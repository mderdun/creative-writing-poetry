<script lang="ts">
    import WorksHead from "$lib/components/WorksHead.svelte";
    import { onMount } from "svelte";
    import { cursorColor, cursorPosition } from "$lib/stores.js";

    let intervalId: number | undefined;
    let isFlickering = false;
    let hasFlickered = false;
    let mouseX = 0;
    let mouseY = 0;
    let lastMousePosition = { x: 0, y: 0 };
    let lastMouseMovedTime = Date.now();
    const speed = 0.25;

    onMount(() => {
        cursorColor.set("white");
        const light = document.querySelector(".light") as HTMLElement;
        const body = document.querySelector("#body") as HTMLElement;

        cursorPosition.subscribe(value => {
            mouseX = value.x;
            mouseY = value.y;
        });

        body.addEventListener("mousemove", (e: MouseEvent) => {
            mouseX += (e.clientX - mouseX) * speed;
            mouseY += (e.clientY - mouseY) * speed;
            lastMouseMovedTime = Date.now();
            lastMousePosition = { x: mouseX, y: mouseY };
            light.style.background = `radial-gradient(circle at ${mouseX}px ${mouseY}px, transparent 2%, rgba(0, 0, 0, 0.95) 5%)`;
            if (!isFlickering && hasFlickered) {
                startFlickering();
            }
        });

        function flicker() {
            const minSize = 1;
            const maxSize = 2;
            const size = Math.floor(Math.random() * (maxSize - minSize + 1)) + minSize;
            light.style.background = `radial-gradient(circle at ${mouseX}px ${mouseY}px, transparent ${size}%, rgba(0, 0, 0, 0.95) ${size + 3}%)`;
        }

        function startFlickering() {
            if (!isFlickering) {
                isFlickering = true;
                hasFlickered = true;
                intervalId = window.setInterval(flicker, Math.random() * 10);
            }
        }

        function stopFlickering() {
            if (isFlickering) {
                isFlickering = false;
                if (intervalId !== undefined) {
                    window.clearInterval(intervalId);
                }
                light.style.background = `rgba(0, 0, 0, 0.95) 2%`;
            }
        }

        setInterval(() => {
            if (Date.now() - lastMouseMovedTime > 500) { // mouse has not moved in 3 seconds
                stopFlickering();
            }
        }, 100);

        setTimeout(() => {
            if (!isFlickering) {
                startFlickering();
            }
        }, 10000); // start flickering after 10 seconds
    });
</script>

<div id="body" class="min-h-screen bg-stone-950 text-white">
    <WorksHead title="when in dark"/>
    <div id="poem" class="w-screen flex flex-col justify-center items-center text-xl">
        <div class="flex flex-col gap-y-5 justify-start items-start">
            <div>
                <p>start reading<span class="gappy">&nbsp;&nbsp;&nbsp;</span>was already dark</p>
                <p>kicked in the shins on the way home</p>
                <p>past 10's enough a curfew<span class="gappy">&nbsp;&nbsp;&nbsp;</span>enough</p>
                <p>to make you feel kid again</p>
            </div>
            <div>
                <p>to make you remember that there are more ways to read<span class="gappy">&nbsp;&nbsp;&nbsp;</span>in the dark</p>
            </div>
            <div>
                <p>what is a curfew what is a curfew when you can wake up</p>
                <p>early enough which is early<span class="gappy">&nbsp;&nbsp;&nbsp;</span>enough</p>
                <p>which is reading in the dark</p>
                <p>or when others read not<span class="gappy">&nbsp;&nbsp;&nbsp;</span>in the dark</p>
                <p>you know this you know your paper-round you know</p>
                <p>at sunrise you know your route and you know<span class="gappy">&nbsp;&nbsp;&nbsp;</span>the dark</p>
                <p>and you know that newsprint stains and letters your hands</p>
                <p>go dark<span class="gappy">&nbsp;&nbsp;&nbsp;</span>you know</p>
                <p>to make your money at a young age</p>
                <p>you know the lights would never<span class="gappy">&nbsp;&nbsp;&nbsp;</span>go out</p>
                <p>you know when they go out it is not permanent</p>
            </div>
            <div>
                <p>so you get kicked in the shins so the lights will<span class="gappy">&nbsp;&nbsp;&nbsp;</span>not go out <span class="text-sm ml-3">THE END</span>.</p>
            </div>
        </div>
    </div>
    <div class="light" />
</div>

<style>
    .gappy {
        width: 2.5rem;
        display: inline-block;
        transition: 1s all;
    }

    .gappy:hover {
        width: 7rem !important;
        display: inline-block
    }

    #poem {
        line-height: 2.5rem;
    }

    .light {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        pointer-events: none;
        background: rgba(0, 0, 0, 0.95) 3%;
    }
</style>