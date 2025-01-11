<script>
    import Form from "./components/Form.svelte";
    import List from "./components/List.svelte";

    let items = [
        { id: 1, text: "Buy groceries 🛒" },
        { id: 2, text: "Call a friend ☎️" },
        { id: 3, text: "Water the plants 🌱" },
        { id: 4, text: "Go for a run 🏃‍♂️" },
        { id: 5, text: "Clean the house 🧹" },
        { id: 6, text: "Plan a trip ✈️" },
        { id: 7, text: "Listen to music 🎧" },
    ];

    const handleItemAddition = (e) => {
        const newItem = {
            id: items.length + 1,
            text: e.detail.item,
        };
        items = [newItem, ...items];
    };

    const handleItemRemoval = (e) => {
        items = [...items.filter((item) => item.id !== e.detail.id)];
    };
</script>

<main>
    <h1>To-Do List 📖</h1>
    <Form on:add={(e) => handleItemAddition(e)} />
    <List {items} on:remove={(e) => handleItemRemoval(e)} />
</main>

<style>
    main {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    h1 {
        color: #35495e;
        margin-bottom: 50px;
    }
</style>
