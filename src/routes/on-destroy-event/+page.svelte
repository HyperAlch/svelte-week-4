<script>
    import Game from "./Game.svelte";

    let games = ["World of Warcraft", "FF14", "The Elder Scrolls Online", "ArcheAge"];

    function deleteGame(event) {
        games = games.filter(game => event.detail.name != game);
    }
</script>
<h1>Choose some MMO's to shutdown</h1>
<ul>
    {#each games as game}
        <Game on:delete={deleteGame} name={game} />
    {/each}
</ul>

