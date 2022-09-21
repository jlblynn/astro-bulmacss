<script>

  import LogIn from './LogIn.svelte';
  import SignUp from './SignUp.svelte';

  let showLogIn = false;
  let showSignUp = false;

  function displayLogIn() {
    showSignUp = false;
    showLogIn = !showLogIn;
  }

  function displaySignUp() {
    showSignUp = !showSignUp;
    showLogIn = false;
  }

</script>

<div>

  {#if showLogIn}
    <button class="btn active" on:click={displayLogIn}>log in</button>
    <button class="btn" on:click={displaySignUp}>sign up</button>
    <LogIn />
  {:else if showSignUp}
    <button class="btn" on:click={displayLogIn}>log in</button>
    <button class="btn active" on:click={displaySignUp}>sign up</button>
    <SignUp />
  {:else}
    <button class="btn" on:click={displayLogIn}>log in</button>
    <button class="btn" on:click={displaySignUp}>sign up</button>
  {/if}

</div>


<style>
  
</style>