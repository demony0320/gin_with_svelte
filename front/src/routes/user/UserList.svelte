<script>
    import { Router, Route, Link } from "svelte-navigator";
    import { onMount } from 'svelte';
    import { auth_fetch, get_backend_url } from "../../components/Util.svelte";
    //export let UserList;


	let users = [];
  let stat = '';

 
	onMount(async () => {
    const url = get_backend_url();
    const result = await auth_fetch(`${url}/admin/user`);
    console.log(result);
    users=result;

  });

  </script>
  
  <div class="Users">
    <h2>UserList</h2>
  
    <span>You're at user/userlist</span>
    <div class="users">
        {#each users as user}
            {user.name} , {user.userid} 
        {/each}
    </div>
    <nav>
      <Link to="../">Go back to the landing page</Link>
    </nav>

    <Router>
      <article>
        <Route path=":id" let:params>
          <h2>ID: {params.id}</h2>
          <p>I don't know what to do with this...</p>
        </Route>
  
        <Route path="svelte">
          <h2>Svelte</h2>
          <p>
            Svelte is a radical new approach to building user interfaces. Whereas
            traditional frameworks like React and Vue do the bulk of their work in
            the browser, Svelte shifts that work into a compile step that happens
            when you build your app. Instead of using techniques like virtual DOM
            diffing, Svelte writes code that surgically updates the DOM when the
            state of your app changes.
            <a href="https://svelte.dev/blog/svelte-3-rethinking-reactivity">
              Read the introductory post
            </a>
            to learn more.
          </p>
        </Route>
  
        <Route path="navigator">
          <h2>Navigator</h2>
          <p>
            Simple, declarative routing for single page apps built with Svelte.
          </p>
        </Route>
      </article>
    </Router>
  </div>
  