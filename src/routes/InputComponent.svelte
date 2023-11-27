<script lang="ts">
    import ProductInput from "./ProductInput.svelte";
    import UserInput from "./UserInput.svelte";

    import { createEventDispatcher } from 'svelte';


    // I've dispatched user and product differently to show a couple of ways to do it
    const dispatch = createEventDispatcher();

    function addUser(event: any) {
        dispatch('addUser', {
            newUser: event.detail.newUser
        });
    }
</script>

<div class="flex flex-col w-10/12">
    <ProductInput on:addProduct />
    <br>
    <hr>
    <br>
    <UserInput on:addUser={addUser} />
</div>