<script lang="ts">
    import { Button, Input } from 'flowbite-svelte';
    import type { User } from "$lib/user";
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();

    let username: string = "";
    let firstName: string = "";
    let lastName: string = "";

    function addUser() {
        const newUser = {
            username: username,
            firstName: firstName,
            lastName: lastName
        }

        dispatch('addUser', {
            newUser: newUser
        });
    }
</script>

<div>
    <form>
        <Input type="text" placeholder="Username" bind:value={username}/>
        <Input type="text" placeholder="First Name" bind:value={firstName}/>
        <Input type="text" placeholder="Last Name" bind:value={lastName}/>
        <Button type="submit" on:click={addUser}>Add User</Button>
    </form>
</div>