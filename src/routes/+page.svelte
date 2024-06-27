<script>
    // @ts-nocheck

    import ListItem from "$lib/components/ListItem.svelte";

    let todoItems = [
        { title: "Item 1"},
        { title: "Item 2"},
        { title: "Item 3"},
    ];

    function addTodoItem(event) {
        event.preventDefault();
        const input = event.target.querySelector("input");
        const title = input.value;
        todoItems = [...todoItems, { title, buttonText: "Delete" }];
        input.value = "";
    }

    function deleteTodoItem(event) {
        const { title } = event.detail; 
        todoItems = todoItems.filter(item => item.title !== title);
    }
</script>

<div class="flex flex-col items-center justify-center h-screen">
    <form class="flex justify-center mb-4" on:submit={addTodoItem}>
        <input
            type="text"
            class="rounded-lg p-2 shadow-lg w-96 outline outline-offset-2 outline-pink-400"
            placeholder="Enter a todo item"
        />
        <button
            class="outline outline-offset-2 outline-pink-400 ml-2 rounded-lg bg-cyan-600 hover:bg-cyan-700 text-white py-2 px-4"
        >
            Add
        </button>
    </form>
    <div class="backdrop-opacity-25 backdrop-blur-sm overflow-auto h-5/6 w-full max-w-7xl p-4 shadow-lg rounded-lg space-y-4 flex flex-col items-center bg-cyan-800">
        {#each todoItems as item, index}
            <ListItem
                key={index}
                id={index}
                title={item.title}
                on:delete={deleteTodoItem}
            />
        {/each}
    </div>
</div>


