<script>
    // Importing required modules and components
    import anime from "animejs"; // A lightweight JavaScript animation library
    import SplitType from "split-type"; // A utility for splitting HTML elements into typographic HTML structures
    import { onMount } from "svelte"; // Svelte lifecycle method that runs after the component first renders
    import WorksHead from "$lib/components/WorksHead.svelte"; // Custom component for the header of the work
    import { cursorColor } from "$lib/stores.js"; // Svelte store for managing cursor color

    // This function runs after the component first renders
    onMount(() => {
        // Set the cursor color to black
        cursorColor.set('black')

        // Select all paragraph elements within the element with id 'poem'
        const poemParagraphs = document.querySelectorAll("#poem p");

        // For each paragraph element
        poemParagraphs.forEach(paragraph => {
            // Split the paragraph into words and wrap each word in a span with class 'word'
            const words = new SplitType(paragraph, {
                types: "words",
                wordsClass: 'word' // wrap each word in a span with class 'word'
            });

            // Select all elements with class 'word'
            const wordElements = document.querySelectorAll('.word'); // select the word elements

            // For each word element
            wordElements.forEach(word => {
                // Add a mouseover event listener
                word.addEventListener('mouseover', function (e) {
                    // If the word is already invisible (opacity is 0), do nothing
                    if (window.getComputedStyle(e.target).opacity === '0') {
                        return;
                    }
                    // Otherwise, animate the word to fade out over 600ms
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

<!-- The main body of the page -->
<div id="body">
    <!-- The header of the work, with a title and a subtitle -->
    <WorksHead title="you send words till they're gone" subtitle="hover over them and see what happens" />

    <!-- The poem section, with a specific style and behavior -->
    <div id="poem" class="text-xl w-screen flex justify-center items-center">
        <div>
            <!-- Each paragraph represents a line of the poem -->
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

<!-- Styling for the paragraph elements -->
<style>
    /* The space between words is set to 10px and the line height is set to 2 for better readability */
    p {
        word-spacing: 10px;
        line-height: 2;
    }
</style>