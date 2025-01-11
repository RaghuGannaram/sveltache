<script>
    import { createEventDispatcher } from "svelte";

    let item = "";
    let error = "";

    const dispatch = createEventDispatcher();

    const handleSubmit = () => {
        if (item.trim() === "") {
            error = "Please enter a valid item";
            return;
        }
        dispatch("add", { item });
        item = "";
        error = "";
    };
</script>

<section>
    <form on:submit|preventDefault={handleSubmit}>
        <input type="text" placeholder="Add new item" bind:value={item} />
        <button type="submit">Add</button>
    </form>
    {#if error}
        <p class="error">{error}</p>
    {/if}
</section>

<style>
    section {
        width: 400px;
        margin-bottom: 20px;
    }

    form {
        width: 100%;
        display: flex;
        justify-content: space-between;
    }

    input {
        width: 72%;
        padding: 10px;
        outline: none;
        border: 1px solid #ccc;
        border-radius: 5px;
        font-size: 16px;
    }

    button {
        width: 25%;
        color: white;
        background-color: #35495e;
        padding: 10px;
        border: 1px solid #ccc;
        border-radius: 5px;
        font-size: 16px;
    }

    button:hover {
        background-color: #26415e;
    }

    .error {
        color: red;
        font-size: 14px;
        margin-top: 5px;
        padding: 0px 10px;
    }
</style>
