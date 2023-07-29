<script lang="ts">
	import  Router from "svelte-spa-router";
	import About from "../routes/About.svelte";
	import UserDetails from "../routes/UserDetails.svelte";
	import UsersList from "../routes/UsersList.svelte";
    import logo from "../../images/logo_white-1.svg"

	let routes={
		"/": About,
		"/UserDetails/:id":UserDetails,
		"/UsersList":UsersList


		// "*": NotFound
	}
	
</script>

<nav class="navbar">
    <div class="navbar-container">
    
        <a href="#/">
        <img class="navbar-logo" src={logo} alt="Logo" />
    </a>
      <div class="navbar-links">
        <li><a href="#/">About</a></li>
        <li><a href="#/UsersList">Users List</a></li>
      </div>
    </div>
  </nav>
 
  
  <style>
	/* Navbar styles */
	.navbar {
	  background-color: #333;
	  color: #fff;
	  padding: 1% 2%;
	  display: flex;
	  justify-content: space-between;
	}
  
	.navbar-container {
        display: flex;
        align-items: center;
        width: 50%;
        justify-content: space-between;
	}
  
	.navbar-logo {
      width: 130px;
	}
  
	.navbar-links {
	  list-style: none;
	  margin: 0;
	  padding: 0;
	  display: flex;
	}
  
	.navbar-links li {
	  margin-right: 20px;
	}
  
	.navbar-links li:last-child {
	  margin-right: 0;
	}
  
	.navbar-links li a {
	  text-decoration: none;
	  color: #fff;
	  font-size: 16px;
	  transition: color 0.2s ease;
      padding: 3px 5px;
	}
    .navbar-links li a:hover {
        color: #333333;
        background: #f0f0f0;
        border-radius: 8px;
    }
	.navbar-links:last-child {
    	margin-right: 0;
	}
	@media screen and (max-width: 700px) {
        .navbar-container{
            width: 100%;
        }
	}
</style>