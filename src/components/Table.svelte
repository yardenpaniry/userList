<script>
  import pic1 from '../../images/pic-1.png'
  import pic2 from '../../images/pic-2.png'
  import pic3 from '../../images/pic-3.png'
  import pic4 from '../../images/pic-4.png'
  import pic5 from '../../images/pic-5.png'
  import pic6 from '../../images/pic-6.png'
  import pic7 from '../../images/pic-7.png'
  import pic8 from '../../images/pic-8.png'
  import pic9 from '../../images/pic-9.png'
  import pic10 from '../../images/pic-10.png'

  const usersImages = [
    pic1,
    pic2,
    pic3,
    pic4,
    pic5,
    pic6,
    pic7,
    pic8,
    pic9,
    pic10,
  ]
  export let users
</script>

<table>
  <thead>
    <tr>
      <th></th>
      <th>Name</th>
      <th>Phone</th>
      <th>Email</th>
      <th>User ID</th>
    </tr>
  </thead>
  <tbody>
    <!-- <li>
            <a >{user.firstName}</a>
          </li> -->
    {#each users as user , index}

    <tr>
      <td>
        <a href={`/#/UserDetails/${user.userId}`}>
          <img
            class="userPicture"
            src="{usersImages[index]}"
            alt="{user.name}"
            width="55"
            height="65"
          />
        </a>
      </td>
      <td>
        <a href={`/#/UserDetails/${user.userId}`}>{#if user.firstName && user.lastName} {user.firstName + ' ' +
          user.lastName} {:else if user.firstName} {user.firstName} {:else if
          user.lastName} {user.lastName} {:else} no name {/if}</a
        >
      </td>
      <td><a href={`/#/UserDetails/${user.userId}`}>{user.phone}</a></td>
      <td><a href={`/#/UserDetails/${user.userId}`} class="emailLink">{user.email}</a></td>
      <td><a href={`/#/UserDetails/${user.userId}`}>{user.userId}</a></td>
    </tr>

    {/each}
  </tbody>
</table>

<style>
  table {
    width: 100%;
    border-collapse: collapse;
    border: 1px solid #cccccc;
  }

  th,
  td {
    padding: 8px;
    border-bottom: 1px solid #ccc;
  }

  th {
    text-align: left;
  }

  tr:hover {
    background-color: #f2f2f2;
  }
  img.userPicture {
    /* border: 1px solid black; */
    border-radius: 29px;
  }
  .emailLink {
    overflow-wrap: anywhere;
  }
</style>
