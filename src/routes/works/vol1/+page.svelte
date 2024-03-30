<script lang="ts">
    import WorksHead from "$lib/components/WorksHead.svelte";
    import { onMount } from "svelte";

    let intervalId: number | undefined;
    let isFlickering = false;
    let hasFlickered = false;
    let mouseX = 0;
    let mouseY = 0;
    let lastMousePosition = { x: 0, y: 0 };
    let lastMouseMovedTime = Date.now();

    onMount(() => {
        const light = document.querySelector(".light") as HTMLElement;
        const body = document.querySelector("#body") as HTMLElement;

        body.addEventListener("mousemove", (e: MouseEvent) => {
            mouseX = e.clientX;
            mouseY = e.clientY;
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
                light.style.background = `rgba(0, 0, 0, 0.95) 5%`;
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

<div id="body" class="h-screen bg-stone-950 text-white">
    <WorksHead title="Streetlamps"/>
    <div id="poem" class="w-screen flex flex-col justify-center items-center text-xl">
        <div>
            <p>&nbsp;&nbsp;&nbsp;Twas the eve before Christmas</p>
            <p>All was snowy and snivvy on the ground</p>
            <p>&nbsp;&nbsp;&nbsp;The lamps were lit and frying,</p>
            <p>And the air was thick and brown.</p>
        </div>
        <div class="py-5">
            <p>&nbsp;&nbsp;&nbsp;Twas the eve before Christmas</p>
            <p>All was snowy and snivvy on the ground</p>
            <p>&nbsp;&nbsp;&nbsp;The lamps were lit and frying,</p>
            <p>And the air was thick and brown.</p>
        </div>
    </div>
    <div class="light" />
</div>

<style>
    .light {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        pointer-events: none;
        background: rgba(0, 0, 0, 0.95) 5%;
    }
</style>