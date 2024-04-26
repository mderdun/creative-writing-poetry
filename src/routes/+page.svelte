<script>
    import IndexBox from "$lib/components/IndexBox.svelte";
    import {onMount} from "svelte";
    import {cursorColor} from "$lib/stores.js";

    onMount(() => {
        cursorColor.set('black');
    });
</script>

<div id="body" class="max-h-screen">
    <div id="header" class="w-screen h-[10vh] flex items-center justify-center">
        <h1 class="text-4xl">Index</h1>
    </div>
    <div id="grid" class="flex flex-col w-screen h-[90vh]">
        <div id="top-row" class="flex w-screen h-1/2">
            <IndexBox n="i" title="when in dark"/>
            <IndexBox n="ii" title="you send words till they're gone"/>
            <IndexBox n="iii" title="my dear miracle in the winery"/>
            <IndexBox n="iv" title="some needs of our polish community"/>
            <IndexBox n="v" title="the way we love is like we're here but we're not"/>
        </div>
        <div id="bottom-row" class="flex w-screen h-1/2">
            <IndexBox n="vi" title="ode on a polish urn"/>
            <IndexBox n="vii" title="i feel like ascii-ng"/>
            <IndexBox n="viii" title="the great a©ker-gram"/>
            <IndexBox n="ix" title="garden too concrete"/>
            <IndexBox n="x" title="so badly breaking it hurts"/>
        </div>
    </div>
</div>