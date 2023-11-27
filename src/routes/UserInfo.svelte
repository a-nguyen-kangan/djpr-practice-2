<script lang="ts">
    import type { User } from '$lib/user';
    import { Button, Heading, Table, TableBody, TableBodyCell, TableBodyRow, TableHead, TableHeadCell } from 'flowbite-svelte';
    import { CloseCircleSolid } from 'flowbite-svelte-icons';
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();

    export let users: User[] = [];

    function deleteClickHandler(event: any) {
        console.log("Delete button clicked");

        dispatch('deleteUser', {
            username: event.target.id
        });

    }
</script>

<div class="p-5 w-full border-solid border-2"> 
    <Heading tag='h3'>Users</Heading>
    <Table>
        <TableHead>
            <TableHeadCell>Username</TableHeadCell>
            <TableHeadCell>First Name</TableHeadCell>
            <TableHeadCell>Last Name</TableHeadCell>
        </TableHead>
        <TableBody>
            {#each users as user}
                <TableBodyRow>
                    <TableBodyCell>{user.username}</TableBodyCell>
                    <TableBodyCell>{user.firstName}</TableBodyCell>     
                    <TableBodyCell>{user.lastName}</TableBodyCell>
                    <TableBodyCell><Button on:click={deleteClickHandler}><CloseCircleSolid on:click={deleteClickHandler} id={user.username}></CloseCircleSolid></Button></TableBodyCell>
                </TableBodyRow>
            {/each}
        </TableBody>
    </Table>
</div>