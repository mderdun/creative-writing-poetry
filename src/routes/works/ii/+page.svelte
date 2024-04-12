<script>
    import anime from "animejs";
    import SplitType from "split-type";
    import { onMount } from "svelte";
    import WorksHead from "$lib/components/WorksHead.svelte";

    onMount(() => {
        const poemParagraphs = document.querySelectorAll("#poem p");
        poemParagraphs.forEach(paragraph => {
            const words = new SplitType(paragraph, {
                types: "words",
                wordsClass: 'word' // wrap each word in a span with class 'word'
            });

            const wordElements = document.querySelectorAll('.word'); // select the word elements
            wordElements.forEach(word => {
                word.addEventListener('mouseover', function (e) {
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
        });
    });
</script>

<div id="body">
    <WorksHead title="Summoning Words" />
    <div id="poem" class="text-xl w-screen flex justify-center items-center">
        <div>
            <p>Summoning words</p>
            <p>from the dark</p>
            <p>to the light</p>
            <p>from the light</p>
            <p>to the dark</p>
            <p>Summoning words</p>
            <p>from the past</p>
            <p>to the present</p>
            <p>from the present</p>
            <p>to the future</p>
            <p>Summoning words</p>
            <p>from the dead</p>
            <p>to the living</p>
            <p>from the living</p>
            <p>to the dead</p>
            <p>Summoning words</p>
            <p>from the heart</p>
            <p>to the mind</p>
            <p>from the mind</p>
            <p>to the heart</p>
            <p>Summoning words</p>
            <p>from the body</p>
            <p>to the soul</p>
            <p>from the soul</p>
            <p>to the body</p>
            <p>Summoning words</p>
            <p>from the earth</p>
            <p>to the sky</p>
            <p>from the sky</p>
            <p>to the earth</p>
            <p>Summoning words</p>
            <p>from the water</p>
            <p>to the fire</p>
            <p>from the fire</p>
            <p>to the water</p>
            <p>Summoning words</p>
            <p>from the wind</p>
            <p>to the rain</p>
            <p>from the rain</p>
            <p>to the wind</p>
            <p>Summoning words</p>
            <p>from the light</p>
            <p>to the dark</p>
            <p>from the dark</p>
            <p>to the light</p>
            <p>Summoning words</p>
        </div>
    </div>
</div>

<style>
    p {
        word-spacing: 10px;
    }
</style>