<script lang="ts">
  import { onMount } from 'svelte'
  import { push, pop, replace } from 'svelte-spa-router'
  import axios from 'axios'
  import pic1 from "../../images/pic-1.png"

  let user = {
    firstName: '',
    lastName: '',
    country: '',
    createdAt: '',
    details: [],
    email: '',
    ipAddress: '',
    lastAccessTime: '',
    phone: '',
    role: 'null',
    updatedAt: '',
    userId: '',
  }

  export let params = {
    id: String,
  }

  const go_back = () => {
    pop()
  }
  const go_home = () => {
    push('/')
  }

  const convertDate = (timestamp) => {
    const dateObj = new Date(timestamp)

    const formattedDate = dateObj.toLocaleDateString()
    const formattedTime = dateObj.toLocaleTimeString()

    return formattedDate + ' ' + formattedTime
  }
  onMount(async () => {
    const response = await axios.get(
      `https://admin.dev.orcam.io/api/v8/users/${params.id}`,
      {
        headers: {
          Authorization: 'accessKey d5797433-f9e0-4c83-aba4-58cd1e3bab4a',
        },
      }
    )
    user = response.data
    console.log('user: ', response.data)
  })
</script>
<div class="userDetailsPage">
  <!-- <h1>User Details: {params.id}</h1> -->
  {#if user}
  <img class="userPicture" src="{pic1}" alt="userpic" width="55" height="65" />

  <p>
    {#if user.firstName && user.lastName} {user.firstName + ' ' + user.lastName}
    {:else if user.firstName} {user.firstName} {:else if user.lastName}
    {user.lastName} {:else} no name {/if}
  </p>

  <div class="userDetails">
    <div class="item">
      country:
      <div class="itemDetail">{user.country ? user.country:""}</div>
    </div>
    <div class="item">
      createdAt:
      <div class="itemDetail">{convertDate(user.createdAt)}</div>
    </div>
    <div class="item">
      email:
      <div class="itemDetail">{user.email ? user.email:""}</div>
    </div>
    <div class="item">
      ipAddress:
      <div class="itemDetail">{user.ipAddress ? user.ipAddress:""}</div>
    </div>
    <div class="item">
      lastAccessTime:
      <div class="itemDetail">
        {user.lastAccessTime? convertDate(user.lastAccessTime):""}
      </div>
    </div>
    <div class="item">
      phone:
      <div class="itemDetail">{user.phone ? user.phone:""}</div>
    </div>
    <div class="item">
      role:
      <div class="itemDetail">{user.role? user.role:""}</div>
    </div>
    <div class="item">
      updatedAt:
      <div class="itemDetail">
        {user.updatedAt?convertDate(user.updatedAt):""}
      </div>
    </div>
    <div class="item">
      userId:
      <div class="itemDetail">{user.userId? user.userId:""}</div>
    </div>
  </div>
  <!-- Display other user details as needed -->
  {:else}
  <p>Loading user details...</p>
  {/if}

  <div class="homeBackButtons">
    <!-- <button on:click="{go_home}">Home</button> -->
    <button on:click="{go_back}">Back</button>
  </div>
</div>

<style>
  .userDetailsPage {
    /* padding: 5%; */
    border: 1px solid #00000038;
    /* border: black; */
    display: flex;
    flex-direction: column;
    align-items: center;
    box-shadow: black 1px 1px 9px 0px;
    background-color: #fdfdfd;
  }

  .userDetails {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    gap: 5%;
  }

  .itemDetail {
    box-shadow: #0000007a 1px 1px 9px 0px;
    border: 1px solid #00000085;
    border-radius: 10px;
    /* width: 137px; */
    padding: 4px 5px;
    min-height: 35%;
    /* width: 100%; */
    overflow-y: auto;
  }

  .item {
    width: 40%;
    margin: 1%;
  }
  .item:last-child {
    width: 87%;
  }
  .homeBackButtons {
    display: flex;
    padding: 3%;
    gap: 16%;
  }
  img.userPicture {
    width: 100px;
    height: 120px;
  }
</style>
