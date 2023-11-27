<script lang="ts">
    import { Heading } from "flowbite-svelte";
    import ProductInfo from "./ProductInfo.svelte";
    import UserInfo from "./UserInfo.svelte";
    import type { User } from "$lib/user";
    import type { Product } from "$lib/product";

    import { createEventDispatcher } from 'svelte';
    const dispatchEvent = createEventDispatcher();

    export let users: User[] = [];
    export let products: Product[] = [];

    function deleteUser(event: any) {
        dispatchEvent('deleteUser', {
            username: event.detail.username
        })
    }
</script>

<div class="flex flex-col w-full">
    <div class="flex flex-row w-full">
        <ProductInfo products={products} on:deleteProduct />
        <br>
        <hr>
        <br>
        <UserInfo users={users} on:deleteUser={deleteUser}/>
    </div>
</div>