<script lang="ts">
    import type { Product } from '$lib/product';
    import { Heading, Table, TableBody, TableBodyCell, TableBodyRow, TableHead, TableHeadCell, Button } from 'flowbite-svelte';
    import { CloseCircleSolid } from "flowbite-svelte-icons";
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();

    export let products: Product[] = [];

    function deleteClickHandler(event: any) {
        console.log("Delete button clicked: ", event.target);
        dispatch('deleteProduct', {
            id: event.target.id
        });
    }
</script>

<div class="p-5 w-full border-solid border-2"> 
    <Heading tag='h3'>Products</Heading>
    <Table>
        <TableHead>
            <TableHeadCell>Id</TableHeadCell>
            <TableHeadCell>name</TableHeadCell>
            <TableHeadCell>Quantity</TableHeadCell>
            <TableHeadCell>Price</TableHeadCell>
        </TableHead>
        <TableBody>
            {#each products as product}
                <TableBodyRow>
                    <TableBodyCell>{product.id}</TableBodyCell>
                    <TableBodyCell>{product.name}</TableBodyCell>     
                    <TableBodyCell>{product.quantity}</TableBodyCell>
                    <TableBodyCell>{product.price}</TableBodyCell>
                    <TableBodyCell><Button on:click={deleteClickHandler} id={product.id}><CloseCircleSolid on:click={deleteClickHandler}></CloseCircleSolid></Button></TableBodyCell>
                </TableBodyRow>
            {/each}
        </TableBody>
    </Table>
</div>