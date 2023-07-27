<script lang="ts">
  let pic1 ='../../images/pic-1.png'
</script>

<div class="aboutPage">
  <h1>About</h1>
  <p>
    The application will display a list of users, and an option to view the user
    details for each user in the list. <br />
    The application has these pages (single-page application, but with routing):
    <br />
    1. Users list <br />
    2. User details <br />
    3. About <br />
  </p>
  Users list <br />
  A paginated list of users which should be fetched using the User List API -
  see below. <br />
  <p>
    User details <br />
    User details are fetched using the User Details API - see below. <br />
    The page should receive user id as a route parameter and fetch user details
    using the API. <br />
    Displays the user details. <br />
  </p>
  <p>
    About page: just a page with some text. <br />

    General Notes: <br />
    * Use TypeScript <br />
    * Use router for routing <br />
    * Convert timestamps to date/time <br />
  </p>
  <p>
    APIs: <br />
    Use these APIs to make calls to the server to fetch data and make changes.
  </p>
</div>

<style>
  .aboutPage {
    background-image: url({logo});
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center;
  }
</style>
