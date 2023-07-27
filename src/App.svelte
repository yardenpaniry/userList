<script lang="ts">
	import  Router from "svelte-spa-router";
	import About from "./routes/About.svelte";
	import UserDetails from "./routes/UserDetails.svelte";
	import UsersList from "./routes/UsersList.svelte";
	import Navbar from "./components/Navbar.svelte";

	// Import the background image
	import backgroundImage from "../images/bg.jpg";

	let routes={
		"/": About,
		"/UserDetails/:id":UserDetails,
		"/UsersList":UsersList
		// "*": NotFound
	}
	
  </script>


<Navbar></Navbar>
<main style="background-image: url({backgroundImage});background-size: cover;">
	<Router {routes}/>
</main>
 
<style>
	main {
		padding: 5%;
		background-color: #e9e4e4cf;
	}
</style>