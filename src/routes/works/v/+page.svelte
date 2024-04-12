<script>
    import WorksHead from "$lib/components/WorksHead.svelte";
    import SplitType from "split-type";
    import { onMount } from "svelte";

    const cap_red = ["CE2826", "C52320", "BF1F1C"];
    const cap_white = ["FFC0C0", "FF9999"];
    const stem = ["D4CDC5", "CEC7BE", "CBC4BA", "C8C2B5", "C3BDAE"];

    function getRandomColor(colors) {
        return colors[Math.floor(Math.random() * colors.length)];
    }

    function colorizeWord(word, colors) {
        let lastColor = "";
        let sameColorCount = 0;
        for (let i = 0; i < word.length; i++) {
            let color = getRandomColor(colors);
            if (color === lastColor) {
                sameColorCount++;
                if (sameColorCount === 3) {
                    color = colors.find(c => c !== color) || color;
                    sameColorCount = 0;
                }
            } else {
                sameColorCount = 0;
            }
            lastColor = color;
            word[i].style.color = `#${color} !important`;
        }
    }

    function assignCapColor(whitePercentage) {
        return Math.random() < whitePercentage ? cap_white : cap_red;
    }

    function colorizeWords(words, colors, whitePercentage) {
        let lastWasWhite = false;
        words.forEach(word => {
            if (Math.random() < whitePercentage && !lastWasWhite) {
                colorizeWord(word, colors);
                lastWasWhite = true;
            } else {
                colorizeWord(word, assignCapColor(whitePercentage));
                lastWasWhite = false;
            }
        });
    }

    onMount(async () => {
        const capParagraphs = document.querySelectorAll("#cap p");
        const stemParagraphs = document.querySelectorAll("#stem p");

        for (const paragraph of capParagraphs) {
            await new Promise(resolve => {
                new SplitType(paragraph, {
                    types: "words",
                    wordsClass: 'word', // wrap each word in a span with class 'word'
                    onSplitComplete: resolve
                });
            });
        }

        for (const paragraph of stemParagraphs) {
            await new Promise(resolve => {
                new SplitType(paragraph, {
                    types: "words",
                    wordsClass: 'word', // wrap each word in a span with class 'word'
                    onSplitComplete: resolve
                });
            });
        }

        const capWords = Array.from(document.querySelectorAll("#cap .word"));
        const stemWords = Array.from(document.querySelectorAll("#stem .word"));

        colorizeWords(capWords, assignCapColor(0.1), 0.1);
        colorizeWords(stemWords, stem, 0);
    });
</script>

<div id="body" class="h-screen bg-[#696170]">
    <WorksHead title="mushroom and growth" />
    <div id="poem" class="flex flex-col items-center justify-center space-y-3">
        <div id="cap" class="flex flex-col items-center justify-center text-xl space-y-3">
            <p>if I seek you out i'll probably die</p>
            <p>unsupervised this time no holding hand;</p>
            <p>my parents would be ashamed so in safety</p>
            <p>all we have is happy memory and what we lose is</p>
        </div>
        <div id="stem" class="flex flex-col items-center justify-center text-xl space-y-3">
            <p>mud &nbsp;&nbsp;dirt</p>
            <p>soil on our fingers</p>
            <p>or a kind</p>
            <p>of slime</p>
            <p>also we lose</p>
            <p>thinking moments</p>
            <p>looking &nbsp;&nbsp;&nbsp;around</p>
            <p>learning relearning</p>
            <p>visiting revisiting</p>
            <p>we &nbsp;&nbsp;&nbsp;lose</p>
            <p>warm soup.</p>
        </div>
    </div>
</div>
