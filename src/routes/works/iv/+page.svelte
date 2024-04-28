<script>
    import WorksHead from "$lib/components/WorksHead.svelte";
    import FBPost from "$lib/components/FBPost.svelte";
    import {onMount} from "svelte";
    import {cursorColor} from "$lib/stores.js";

    onMount(() => {
        cursorColor.set('white');
    });
</script>

<div id="body" class="bg-[#18191a] min-h-screen text-[#e4e6eb] pb-6">
    <WorksHead title="some needs of our polish community" subtitle="Across London,&nbsp;&nbsp;Collected Digitally,&nbsp;&nbsp;Winter -> Spring 2024" />
    <div id="poem" class="flex flex-col items-center text-xl">
        <FBPost>
            <p>we look for muscular poles</p>
            <p>anyone anysomething</p>
            <p>shops with corners or tips</p>
            <p>getting a tesco night job</p>
            <p>working and managing two kids</p>
        </FBPost>
        <FBPost>
            <p>we too have rooves for sale</p>
            <p>and need places to rest</p>
            <p>always away from stress</p>
        </FBPost>
        <FBPost>
            <p>we have parties to cool off</p>
            <p>somewhere in the city</p>
            <p>and polish cigarettes</p>
            <p>in sw15</p>
        </FBPost>
        <FBPost>
            <p>we have our papers</p>
            <p>and our bank accounts</p>
        </FBPost>
        <FBPost>
            <p>we have a need for jobs</p>
        </FBPost>
        <FBPost>
            <p>we are available since yesterday</p>
        </FBPost>
        <FBPost>
            <p>we are plasterers that take orders</p>
            <p>for the price of plastering</p>
            <p>for bathroom sets</p>
            <p>vocabulary</p>
            <p>& polish internet television that’s not worth millions</p>
        </FBPost>
    </div>
</div>