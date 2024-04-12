<script>
    import IndexBox from "$lib/components/IndexBox.svelte";
    import {onMount} from "svelte";
    import {cursorColor} from "$lib/stores.js";

    onMount(() => {
        cursorColor.set('red');
    });
</script>

<div id="body" class="max-h-screen">
    <div id="header" class="w-screen h-[10vh] flex items-center justify-center">
        <h1 class="text-4xl">Index</h1>
    </div>
    <div id="grid" class="flex flex-col w-screen h-[90vh]">
        <div id="top-row" class="flex w-screen h-1/2">
            <IndexBox n="i" title="Streetlamps" c1="white" c2="black"/>
            <IndexBox n="ii" title="Summoning Words" c1="black" c2="white"/>
            <IndexBox n="iii" title="my dear miracle in the winery" c1="green" c2="#e1efff"/>
            <IndexBox n="iv" title="Some Needs of Our Polish Community Across London" c1="black" c2="white"/>
            <IndexBox n="v" title="The Great Library" c1="white" c2="black"/>
        </div>
        <div id="bottom-row" class="flex w-screen h-1/2">
            <IndexBox n="vi" title="The Great Library" c1="black" c2="white"/>
            <IndexBox n="vii" title="The Great Library" c1="white" c2="black"/>
            <IndexBox n="viii" title="the great a©ker-gram" c1="black" c2="white"/>
            <IndexBox n="ix" title="The Great Library" c1="white" c2="black"/>
            <IndexBox n="x" title="The Great Library" c1="black" c2="white"/>
        </div>
    </div>
</div>