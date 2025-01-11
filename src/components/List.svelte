<script>
    import { createEventDispatcher } from "svelte";

    const dispatch = createEventDispatcher();
    export let items = [];

    const handleRemove = (id) => {
        dispatch("remove", { id });
    };
</script>

<ul>
    {#each items as item (item.id + item.text)}
        <li>
            <span>{item.text}</span>
            <button on:click={() => handleRemove(item.id)}>x</button>
        </li>
    {/each}
</ul>

<style>
    ul {
        width: 400px;
        margin-bottom: 20px;
        padding: 0;
        list-style: none;
    }

    li {
        padding: 10px;
        margin-bottom: 10px;
        border: 1px solid #ccc;
        border-radius: 5px;
        font-size: 16px;
        background-color: #59f795;

        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    button {
        border: none;
        background-color: transparent;
        margin: 0;
        padding: 0px 5px 5px 0px;
    }

    button:hover {
        cursor: pointer;
        color: white;
    }
</style>
