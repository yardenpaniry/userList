<script lang="ts">
  import { onMount } from "svelte";
  import axios from "axios";
  import Table from '../components/Table.svelte';
 

  const PAGE_SIZE = 10;
  let users = [];
  let total_size; //number of users
  let currentPage;
  let totalPages;

  const load_more = async () => {
    await fetchUsers(); 
    currentPage++;
   };
   const getPage= async (index)=>{
    currentPage = index;
    await fetchUsers();
    
   }

  // Function to navigate to the previous page
  const prevPage = async () => {
    if (currentPage > 1) {
      currentPage -= 1;
        await fetchUsers();
    }
  

  }

  // Function to navigate to the next page
   const nextPage = async () => {
    if (currentPage < totalPages) {
      currentPage += 1;
          await fetchUsers();
    }


  }
  const fetchUsers = async () => {
    console.log("page: ", currentPage)
    const response = await axios.get(
      `https://admin.dev.orcam.io/api/v8/users?page=${currentPage}&size=${PAGE_SIZE}&sort=email:desc`,
      {
        headers: {
          Authorization: "accessKey d5797433-f9e0-4c83-aba4-58cd1e3bab4a",
        },
      }
    );
    const newUsers = response.data.items;
    total_size = response.data.total;
    console.log("users: ", response.data)
    totalPages = Math.round(total_size/ PAGE_SIZE);
    users = newUsers;
    console.log("numOfPages: ", totalPages)

    // if (newUsers.length === PAGE_SIZE) {
    //   // If there are more devices to fetch, recursively call fetchUsers with the next page number
    //   await fetchUsers(page + 1);
    // }

  };

  onMount(async () => {
    currentPage = 0;
    await fetchUsers(); // Start fetching devices from page 0
  });
</script>

<div class="usersListPage">
  <div class="usersList">
    <h1>Users List</h1>
    <Table {users} />
  </div>
  <div class="paginationButtons">
    <button on:click={prevPage}>Prev</button>
    {#if totalPages>0}
        {#each Array(totalPages) as _, i}
        <button class={(i === currentPage) ? "currentPage":""} on:click={()=>getPage(i)}>{i+1}</button>
        {/each}
    {/if}


    <button on:click={nextPage}>Next</button>

  </div>
</div>

<style>
  .usersListPage {
    border: 1px solid #00000038;
    display: flex;
    flex-direction: column;
    align-items: center;
    box-shadow: black 1px 1px 9px 0px;
    background-color: #fdfdfd;
    overflow-x: auto;
  }
  .usersList {
    /* padding: 1% 6% 2% 6%; */
    color: black;
    font-family: sans-serif;
    text-align: center;
    width: 100%;
  }
  .paginationButtons button:hover {
    background: silver;
  }
  .paginationButtons {
    display: flex;
    padding: 4% 0%;
    gap: 1%;
    flex-wrap: wrap;
    width: 100%;
    justify-content: center;
  }
  button.currentPage {
    background-color: #c8c4c4;
  }

</style>
