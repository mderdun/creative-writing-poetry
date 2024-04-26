<script>
    import {onMount, onDestroy} from 'svelte';
    import {browser} from '$app/environment';
    import {cursorColor} from "$lib/stores.js";
    import WorksHead from "$lib/components/WorksHead.svelte";
    import Title from '$lib/components/ascii/Title.svelte';
    import AsciiOne from "$lib/components/ascii/AsciiOne.svelte";
    import AsciiTwo from "$lib/components/ascii/AsciiTwo.svelte";
    import AsciiThree from "$lib/components/ascii/AsciiThree.svelte";
    import AsciiFour from "$lib/components/ascii/AsciiFour.svelte";
    import AsciiFive from "$lib/components/ascii/AsciiFive.svelte";
    import AsciiSix from "$lib/components/ascii/AsciiSix.svelte";

    let currentPart = 0;
    let showOverlay = true; // add a new variable to control the overlay visibility
    const parts = [
        Title,
        AsciiOne,
        AsciiTwo,
        AsciiThree,
        AsciiFour,
        AsciiFive,
        AsciiSix,
        null,
        null
    ];

    const nextPart = () => {
        if (currentPart < parts.length - 1) {
            currentPart++;
        }
        if (currentPart === parts.length - 1) {
            currentPart = 0;
        }
    };

    const prevPart = () => {
        if (currentPart > 0) {
            currentPart--;
        }
    };

    const handleKeydown = (event) => {
        if (event.code === 'ArrowRight') {
            nextPart();
        }
        if (event.code === 'ArrowLeft') {
            prevPart();
        }
        if (currentPart === 0) {
            showOverlay = true;
        } else {
            showOverlay = false;
        }
    };

    onMount(() => {
        cursorColor.set("#41fd16");
        if (browser) { // check if the code is running in the browser
            window.addEventListener('keydown', handleKeydown);
        }
    });

    onDestroy(() => {
        if (browser) { // check if the code is running in the browser
            window.removeEventListener('keydown', handleKeydown);
        }
    });
</script>

<div id="body" class="h-screen bg-slate-950 text-[#41fd16]">
    <WorksHead title="i feel like ascii-ng"/>
    <div class="flex items-center justify-center h-[90vh] max-w-[100vw] overflow-hidden">
        {#each parts as Part, index}
            {#if index === currentPart}
                <svelte:component this={Part} />
            {/if}
        {/each}
    </div>
    {#if showOverlay} <!-- use an if block to control the overlay visibility -->
        <div id="overlay" class="animate-pulse">
            <p>Use arrow keys to navigate</p>
            <div id="arrows">
                <div id="left-arrow">←</div>
                <div id="right-arrow">→</div>
            </div>
        </div>
    {/if}
</div>

<style>
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
    }

    #arrows {
        display: flex;
        justify-content: space-between;
        width: 50px;
    }

    #left-arrow, #right-arrow {
        font-size: 20px;
    }
</style>