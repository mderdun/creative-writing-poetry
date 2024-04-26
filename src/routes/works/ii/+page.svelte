<script>
    import anime from "animejs";
    import SplitType from "split-type";
    import { onMount } from "svelte";
    import WorksHead from "$lib/components/WorksHead.svelte";
    import { cursorColor } from "$lib/stores.js";

    onMount(() => {
        cursorColor.set('black')
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
    <WorksHead title="you send words till they're gone" subtitle="hover over them and see what happens" />
    <div id="poem" class="text-xl w-screen flex justify-center items-center">
        <div>
            <p>even i could</p>
            <p>and could be good</p>
            <p>and nothing</p>
            <p>and even i would</p>
            <p>and could and nothing</p>
            <p>so nothing is good</p>
            <p>even when there is something</p>
            <p class="ml-36">or</p>
            <p>must there be always boats</p>
            <p>or trees or thimbles too</p>
            <p>or might there just be nothing</p>
            <p>so wide and blue to make</p>
            <p>a something out of should</p>
            <p class="ml-52">or could</p>
            <p>a bloom too too</p>
            <p>that goodness is for nothing</p>
            <p>that lends itself to milkbun</p>
            <p class="ml-64">icing</p>
            <p>burns itself to stuffing</p>
        </div>
    </div>
</div>

<style>
    p {
        word-spacing: 10px;
        line-height: 2;
    }
</style>