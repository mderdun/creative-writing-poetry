<script>
    import WorksHead from "$lib/components/WorksHead.svelte";
    import { onMount } from 'svelte';
    import { cursorColor } from '$lib/stores.js';

    function handleHoverEffect(classGroups) {
        classGroups.forEach(classNames => {
            const elements = document.querySelectorAll(classNames.map(className => `.${className}`).join(', '));

            elements.forEach((element) => {
                element.addEventListener('mouseover', () => {
                    elements.forEach((el) => {
                        el.style.color = '#e1efff'; // Change this to the color you want
                        el.style.textShadow = '0 0 5px #3c536e'
                    });
                });

                element.addEventListener('mouseout', () => {
                    elements.forEach((el) => {
                        el.style.color = ''; // Change this to the original color
                        el.style.textShadow = '';
                    });
                });
            });
        });
    }

    onMount(() => {
        cursorColor.set('#3c536e');
        handleHoverEffect([['dear'], ['alt', 'alt2']]);
    });
</script>

<div id="body" class="body text-white">
    <div id="text">
    <WorksHead title="my dear miracle in the winery" />
    <div id="container" class="w-screen flex items-center justify-center">
    <div id="poem" class="poem flex flex-col text-xl">
        <div id="epigraph" class="text-sm flex flex-col items-end opacity-90">
            <p>you are the one who makes the wine</p>
            <p>you are the one who drinks the wine</p>
            <p>you are the one who is the wine</p>
            <p>you are the one who is the winery</p>
            <p>you are the one who is the miracle</p>
            <p>you are the one who is the dear</p>
            <p>thank you KONSTANTY ILDEFONS GAŁCZYŃSKI</p>
        </div>
        <div id="stanza1" class="stanza">
            <p class="dear">truth: he has a car we can't afford</p>
            <p class="dear">my dear</p>
            <p class="dear">but look: only fools are in a hurry——how much more dignified it is to walk</p>
            <p class="dear">my dear</p>
        </div>
        <div id="stanza2" class="stanza">
            <p class="dear">there are also no funds for london</p>
            <p class="alt">two skippers from the london docks found it one year a forgotten wine barrel they took off the lid and both of them they were terrified; from the barrel the person of the six-winged seraph! serafin was walking up the stairs like a sweet lamp and it smelled</p>
            <p class="dear">my dear</p>
            <p class="alt">but it was decreasing</p>
            <p class="dear">but why london? london-burrow: in “paris-soir” I read yesterday</p>
            <p class="alt">and the poor kippers they scratched their heads</p>
            <p class="dear">that marquis q</p>
            <p class="alt">that character is not a local</p>
        </div>
        <div id="stanza3" class="stanza">
            <p class="dear">that is</p>
            <p class="alt">the wind with a furious storm simply tore london apart like a tree—a visible act of god; the king hid in the cupboard</p>
            <p class="dear">a baronet</p>
            <p class="alt">they were shaking under the beds of barbers and astronomers</p>
            <p class="dear">he poisoned his wife with dog noodles... to bloody hell with london</p>
            <p class="alt2">this sad london our seraph is wandering</p>
            <p class="dear">my dear !</p>
        </div>
        <div id="stanza4" class="stanza">
            <p class="alt2">homeless</p>
            <p class="dear">for caviar from the kremlin</p>
            <p class="alt2">the rain poured down on him</p>
            <p class="dear">for sturgeon we don't have any either</p>
            <p class="alt2">a policeman will shout from the bridge:</p>
            <p class="dear">my dear</p>
            <p class="alt2">"who are you?"—and he just did</p>
            <p class="dear">but what good is the kremlin</p>
            <p class="alt2">"i am the pole</p>
            <p class="dear">when I have your hips?</p>
            <p class="alt2">jam polak"</p>
            <p class="dear">the hips are golden</p>
            <p class="alt2">"that's beautiful</p>
            <p class="dear">and the night is blue</p>
            <p class="alt2">my winged one</p>
            <p class="dear">and we also have a glass of wine and an account in heaven with a seraphim</p>
            <p class="alt2">please go to the embassy there's everything for poles</p>
            <p class="dear">so whistle for the car</p>
            <p class="alt2">good english "cop" serafin explained: go there then there</p>
        </div>
        <div id="stanza5" class="stanza pb-10">
            <p class="dear">kremlin and london</p>
            <p class="alt2">there's an angel in the embassy he cried over the whole stool</p>
            <p class="dear">my dear</p>
            <p class="alt2">over form</p>
            <p class="dear">&nbsp;</p>
            <p class="alt2">stamp and pad</p>
            <p class="dear">&nbsp;</p>
            <p class="alt2">he borrowed from grief pln 340 and disappeared like a cloud</p>
        </div>
    </div>
    </div>
    </div>
</div>

<style>
    .body {
        display: block;
        background-image: url("/imgs/beach_THREEwater_ani.gif");
        background-size: cover;
    }
    #text {
        backdrop-filter: blur(20px) saturate(140%);
    }
    .stanza {
        margin-top: 2.5em;
    }
    #poem {
        max-width: 550px
    }
    .alt {
        margin-left: 2em;
        margin-top: -0.8em;
    }
    .alt2{
        margin-left: -2.68em;
        margin-top: -0.8em;
    }
    .dear, .alt, .alt2 {
        transition: color 0.3s ease, text-shadow 0.3s ease;
    }
    p {
        padding-left: 1em;
        text-indent: -1em;
        width: fit-content;
    }
</style>