<script lang="ts">
    import { Heading } from "flowbite-svelte";
    import InputComponent from "./InputComponent.svelte";
    import type { User } from "$lib/user";
    import type { Product } from "$lib/product";
    import Info from "./Info.svelte";

    let users: User[] = [];
    let products: Product[] = [];

    function addProduct(event: any) {
        if(products.find(product => product.id === event.detail.newProduct.id)) {
            alert("Product with this id already exists");
            return;
        }

        products = [...products, event.detail.newProduct];
        console.log(products);
    }

    function addUser(event: any) {
        if(users.find(user => user.username === event.detail.newUser.username)) {
            alert("User with this username already exists");
            return;
        }

        users = [...users, event.detail.newUser];
    }

    function deleteUser(event: any) {
        console.log(event.detail.username)
        users = users.filter(user => user.username !== event.detail.username);
        console.log(users)
    }

    function deleteProduct(event: any) {
        console.log(event.detail.id)
        products = products.filter(product => product.id != (<Number>event.detail.id));
        console.log(products);
    }

</script>
<div class="flex flex-col items-center">
    <Heading class="text-center">Practice Exercise 2</Heading>
    <br>
    <div class="flex flex-col w-10/12 items-center border-solid border-2 p-2">
        <InputComponent on:addProduct={addProduct} on:addUser={addUser}/>
    </div>
    <div class="flex flex-col w-10/12 items-center border-solid border-2 p-2">
        <Info products={products} users={users} on:deleteUser={deleteUser} on:deleteProduct={deleteProduct}/>
    </div>
</div>