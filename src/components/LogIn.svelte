<script>
  import { getUserDetails } from '../hooks/auth';
  import { store } from '../hooks/auth';
  import { onMount } from 'svelte';

  let username = '';
	let password = '';
	let error = '';
  let user;
  let data = false;

  onMount(async () => {
		user = await getUserDetails( username, password )
	});


	async function login() {
		const user = await getUserDetails( username, password )

		if ( user ) {
			console.log(user)
			$store = user
      data = true
			if ( error ) error = ''
		}
		else {
			error = 'Incorrect username and password.'
			console.log("Incorrect username and password.")
		}

	}
</script>

{#if !data}
<div class="form-group">
  <form on:submit|preventDefault={login}>
    <div>
      <label class="form-label" for="username">Email</label>
      <input class="form-input" type="email" id="username" bind:value={username}/>
      {#if error}
        <div class="toast toast-error">
          <p class="error-message">Email is required</p>
        </div>
      {/if}
    </div>
    <div>
      <label class="form-label" for="name">Password</label>
      <input class="form-input" type="password" id="password" bind:value={password} />
      {#if error }
        <div class="toast toast-error">
          <p class="error-message">Password is required</p>
        </div>
      {/if}
    </div>
    <button class="btn" type="submit">Log In</button>
  </form>
</div>
{:else if data}
  <p>Hello</p>
{/if}

<style>
  
</style>