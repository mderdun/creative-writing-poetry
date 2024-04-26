<script>
    import WorksHead from "$lib/components/WorksHead.svelte";
    import { cursorColor } from '$lib/stores.js';
    import {onMount} from "svelte";
    import sticky from "$lib/sticky.js";

    let isStuck = false;

    function handleStuck(e) {
        isStuck = e.detail.isStuck;
    }

    onMount(() => {
        cursorColor.set('#41fd16');
    });
</script>

<div id="body">
    <WorksHead title="the great a©ker-gram" />
    <div id="work" class="flex flex-col text-xl w-screen items-center">
        <div id="text">
            <div id="categories" class="flex flex-row items-center justify-center">
                <p class="mr-5"><span id="num">1</span> Desire</p>
                <p class="mr-5"><span id="num">2</span> Utterance</p>
                <p class="mr-5"><span id="num">3</span> Oedipus</p>
                <p><span id="num">4</span> Authority/Agency</p>
            </div>
            <div id="intertext">
                <div class="sticky box" class:isStuck use:sticky={{ stickToTop: true }} on:stuck="{handleStuck}"><p>Theory of the Intertext</p></div>
                <p><span id="num">1</span> Intertextuality is desirous. Unsatisfied with singularity, it always points and gestures to “more”; each utterance the offspring of an amalgam of likely and unlikely matches that consummate in snowballing necessity simply because <span class="under">there is no other way</span>.</p>
                <p><span id="num">2</span> As such ‘women writers’ (any writers outside hegemony) enter into a landscape where heteronormative, white, and patriarchal utterances have had centuries to reproduce and permeate through. The languages they use all bear traces of the “stuff”. What they, the others, have to themselves, their identities and embodied selves, are raised in this system. But they are not dependent on it. There is a wealth of unique experience that warrants expression, and can bend the intertexts to stake claims in new, autonomous territories, or take over the old, existing orders. It is precisely because the “regulative fictions” are imposed from the dominant perspective that allow them to be warped under the weight of real experience. You can find out who you are by trying to be what you aren’t and seeing the ways your body and the mask respond. This is but one way.</p>
                <p><span id="num">3</span> Being born in the midst of already chattering utterances can mean the curse of living your parents. Especially when their subjectivities were shaped before reflexive consideration of the utterances and texts that shaped them. But you, by being conscious of these things, can wear the mask and investigate these shaping utterances. And by realising the forces at play, you can begin to collage for yourself.</p>
                <p><span id="num">4</span> As you realise that all authority and agency is non-absolute, referential (and deferential), and non-originary, you can see both the arbitrariness of authority (everyone and no-one can have it) and also that it functions without feeling or ethics because it is machinic. You will have to become machine if you want to deal directly with things.</p>
            </div>
            <div id="bio">
                <div class="sticky box" class:isStuck use:sticky={{ stickToTop: true }} on:stuck="{handleStuck}"><p>Biography & Life</p></div>
                <p><span id="num">3</span> You realise quickly that you are born into a system particular to your surroundings and your parents. You will share in their pain and their joy because what they teach you, tell you, as well as what they don’t, these things will be a guide for you at an age when you need these guides and you know nothing else. You will also realise that your parents are not necessarily biological but they are also myths and functions. This hurts because it severs your claim to unique connection, but it will also free you to the thought that anything can be your parent. You can find new parents in books or older kids or the Art World.</p>
                <p><span id="num">1</span> Now you look for these things, you desire them because it is clear that there is a pool of infinite sources for your collage. Desire for all things becomes your driving force. This desire you will realise is penetrative, that is it seeks entry, but can only achieve by being entered. Desiring self-knowledge is a desire for entry, but it requires that you are transparent and permeable. Desire for language is a desire to project meaning which requires an absorption by meaning-making structures of language. Sexual desire is the physical, most embodied manifestation of all desire.</p>
                <p><span id="num">2</span> All this is a mental expression of desire, and a balanced one. But not everyone, in actuality, balances desire, particularly men who have no real checks in place for over-reaches of desire and who have set the stage for a long time now. When the desire to be penetrated comes up against the unchained hetero-patriarchal desire to take and penetrate objects, the consequence for the penetrable body is the vulnerability to rape (though the rapist does not care for the desires of his objects). It should go without saying that the desiring body does not want to be raped.</p>
                <p><span id="num">4</span> At the centre of desire is a voice that wants self-determination, self-respect, self-nurture. This is the penetrable authority and agent which gives and takes in equal measure (the zero-sumness of the non-originary). You can be who you want by being open to being anyone. But in the real world this is dangerous especially for those who are outnumbered in utterance. Keep generating utterance; keep generating potentialities.</p>
            </div>
            <div id="methodology">
                <div class="sticky box" class:isStuck use:sticky={{ stickToTop: true }} on:stuck="{handleStuck}"><p>Methodology</p></div>
                <p><span id="num">3</span> Lay bare all your parents, all the utterances that have shaped you, that still can, even in their opposition or lack. Now it is time to interrogate them not for the signs which automate their readability, that outsource meaning-making, but read them for what they <span class="under">really, consequentially</span> mean.</p>
                <p><span id="num">1</span> Desire all experience in all positions and situations. Try everything on. Play with desire of penetrator and penetrable, give and take. See what happens.</p>
                <p><span id="num">2</span> Create a space where your utterance can direct and dominate no matter the opposition. But also where it can be safe being dominated, getting all things it wants.</p>
                <p><span id="num">4</span> Undermine all authority and agency, give yourself over to the anti-ethics of working machinically so it carries you outside but also burrows into you, becoming cyborg—only by being implanted can you “get outside” your condition.</p>
            </div>
            <div id="reading">
                <div class="sticky box" class:isStuck use:sticky={{ stickToTop: true }} on:stuck="{handleStuck}"><p>Reading</p></div>
                <p><span id="num">1</span> How do you approach the desire to see into the text? The same way that the text is written. It requires give-and-take.</p>
                <p><span id="num">4</span> You give up your control (no more privileged critic who knows all and selects relevance and quotation and receives authority of voice) now you give over agency of reading (this will be automated for you) so that you can receive sight this will feed your desire to experience more of everything. You bypass system of representation and allegory and you receive a diagram which is yours to inhabit and explore.</p>
                <p><span id="num">2</span>&<span id="num">3</span> All things can be read as such and nothing is not utterance. All things have their parents too and nothing is not progeny. You read your science and you read your poetry. Beyond them there is something that is the blob the connection of all things. Are you religious? But everything is everything.</p>
            </div>
            <div id="acker" class="flex flex-col justify-center items-center">
                <div class="sticky box"><p>In Memoriam to Kathy's Identity</p></div>
                <img src="/imgs/kathy.gif" class="w-full mb-5"/>
                <div class="mb-10">
                    <p><span id="num">A</span> is for alternatives.</p>
                    <p><span id="num">C</span> is for collecting.</p>
                    <p><span id="num">K</span> is for a krime.</p>
                    <p><span id="num">E</span> could be everything.</p>
                    <p><span id="num">R</span> is for when you like to read a book!</p>
                </div>
            </div>
        </div>
    </div>
</div>

<style>
    .sticky {
        position: sticky;
        padding: 1rem;
        top: 1rem;
        transition: all 0.3s;
    }

    #text {
        width: 40%;
        justify-content: center;
    }

    p {
        text-align: justify;
        line-height: 200%;
    }

    .under {
        text-decoration: underline #41fd16 wavy 3px;
        text-underline-offset: 7px;
    }

    #num {
        display: inline-block;
        width: 30px; /* adjust as needed */
        height: 30px; /* adjust as needed */
        line-height: 30px; /* adjust as needed */
        text-align: center;
        border-radius: 50%;
        border-color: #41fd16;
        border-width: 2px;
        color: #41fd16;
    }

    .box {
        display: flex;
        justify-content: center;
        width: 100%;
        border-top: 2px black solid;
        border-bottom: 2px black solid;
        margin-top: 30px;
        margin-bottom: 5px;
        background: white;
    }

    .box p::after{
        content: ' ↓↓↓';
    }
    .box p::before{
        content: '↓↓↓ ';
    }
</style>