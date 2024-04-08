<script>
    //@ts-nocheck
    import Login from "../lib/components/Login.svelte"
    import LoggedIn from "../store";
</script>

<svelte:head>
    <title>Amez media</title>
</svelte:head>

{ #if !$LoggedIn}
<Login/>
{:else }
{window.location.href='/posts'}
{/if}
