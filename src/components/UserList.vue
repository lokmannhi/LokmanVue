<template>
  <div>
    <div class="header-bar">
      <img src="../assets/kiratech.png" alt="kira tech logo" class="logo" />
      <div class="icon-container">
        <svg
          class="icon"
          xmlns="http://www.w3.org/2000/svg"
          height="1em"
          viewBox="0 0 448 512">
          <!--! Font Awesome Free 6.4.2 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2023 Fonticons, Inc. -->
          <path
            d="M224 0c-17.7 0-32 14.3-32 32V51.2C119 66 64 130.6 64 208v18.8c0 47-17.3 92.4-48.5 127.6l-7.4 8.3c-8.4 9.4-10.4 22.9-5.3 34.4S19.4 416 32 416H416c12.6 0 24-7.4 29.2-18.9s3.1-25-5.3-34.4l-7.4-8.3C401.3 319.2 384 273.9 384 226.8V208c0-77.4-55-142-128-156.8V32c0-17.7-14.3-32-32-32zm45.3 493.3c12-12 18.7-28.3 18.7-45.3H224 160c0 17 6.7 33.3 18.7 45.3s28.3 18.7 45.3 18.7s33.3-6.7 45.3-18.7z" />
        </svg>
        <svg
          class="icon"
          xmlns="http://www.w3.org/2000/svg"
          height="1em"
          viewBox="0 0 512 512">
          <!--! Font Awesome Free 6.4.2 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2023 Fonticons, Inc. -->
          <path
            d="M495.9 166.6c3.2 8.7 .5 18.4-6.4 24.6l-43.3 39.4c1.1 8.3 1.7 16.8 1.7 25.4s-.6 17.1-1.7 25.4l43.3 39.4c6.9 6.2 9.6 15.9 6.4 24.6c-4.4 11.9-9.7 23.3-15.8 34.3l-4.7 8.1c-6.6 11-14 21.4-22.1 31.2c-5.9 7.2-15.7 9.6-24.5 6.8l-55.7-17.7c-13.4 10.3-28.2 18.9-44 25.4l-12.5 57.1c-2 9.1-9 16.3-18.2 17.8c-13.8 2.3-28 3.5-42.5 3.5s-28.7-1.2-42.5-3.5c-9.2-1.5-16.2-8.7-18.2-17.8l-12.5-57.1c-15.8-6.5-30.6-15.1-44-25.4L83.1 425.9c-8.8 2.8-18.6 .3-24.5-6.8c-8.1-9.8-15.5-20.2-22.1-31.2l-4.7-8.1c-6.1-11-11.4-22.4-15.8-34.3c-3.2-8.7-.5-18.4 6.4-24.6l43.3-39.4C64.6 273.1 64 264.6 64 256s.6-17.1 1.7-25.4L22.4 191.2c-6.9-6.2-9.6-15.9-6.4-24.6c4.4-11.9 9.7-23.3 15.8-34.3l4.7-8.1c6.6-11 14-21.4 22.1-31.2c5.9-7.2 15.7-9.6 24.5-6.8l55.7 17.7c13.4-10.3 28.2-18.9 44-25.4l12.5-57.1c2-9.1 9-16.3 18.2-17.8C227.3 1.2 241.5 0 256 0s28.7 1.2 42.5 3.5c9.2 1.5 16.2 8.7 18.2 17.8l12.5 57.1c15.8 6.5 30.6 15.1 44 25.4l55.7-17.7c8.8-2.8 18.6-.3 24.5 6.8c8.1 9.8 15.5 20.2 22.1 31.2l4.7 8.1c6.1 11 11.4 22.4 15.8 34.3zM256 336a80 80 0 1 0 0-160 80 80 0 1 0 0 160z" />
        </svg>
        <svg
          class="icon"
          xmlns="http://www.w3.org/2000/svg"
          height="1em"
          viewBox="0 0 512 512">
          <!--! Font Awesome Free 6.4.2 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2023 Fonticons, Inc. -->
          <path
            d="M377.9 105.9L500.7 228.7c7.2 7.2 11.3 17.1 11.3 27.3s-4.1 20.1-11.3 27.3L377.9 406.1c-6.4 6.4-15 9.9-24 9.9c-18.7 0-33.9-15.2-33.9-33.9l0-62.1-128 0c-17.7 0-32-14.3-32-32l0-64c0-17.7 14.3-32 32-32l128 0 0-62.1c0-18.7 15.2-33.9 33.9-33.9c9 0 17.6 3.6 24 9.9zM160 96L96 96c-17.7 0-32 14.3-32 32l0 256c0 17.7 14.3 32 32 32l64 0c17.7 0 32 14.3 32 32s-14.3 32-32 32l-64 0c-53 0-96-43-96-96L0 128C0 75 43 32 96 32l64 0c17.7 0 32 14.3 32 32s-14.3 32-32 32z" />
        </svg>
      </div>
    </div>

    <div class="controls-bar">
      <div>
        <input
          v-model="searchQuery"
          type="text"
          placeholder="Search by name..." />
      </div>
      <div>
        <select v-model="sortOrder">
          <option value="a-z">A-Z</option>
          <option value="z-a">Z-A</option>
        </select>
      </div>
      <div class="pagination">
        <button @click="prevPage" :disabled="currentPage === 1">
          Previous
        </button>
        <span>{{ currentPage }}</span>
        <button @click="nextPage" :disabled="currentPage === 10">Next</button>
      </div>
      <div>
        <select v-model="results" @change="fetchUsers">
          <option v-for="n in 20" :key="n" :value="n">{{ n }}</option>
        </select>
      </div>
      <div>
        <button @click="fetchUsers">Refresh</button>
      </div>
    </div>

    <ul v-if="users.length">
      <!-- Headers -->
      <li class="header">
        <span>Picture</span>
        <span>Age</span>
        <span>Name</span>
        <span>Gender</span>
        <span>Country</span>
        <span>Email</span>
      </li>
      <!-- Users -->
      <li
        v-for="user in filteredUsers"
        :key="user.login.uuid"
        class="users"
        @click="openModal(user)">
        <img :src="user.picture.thumbnail" alt="User thumbnail" />
        <p>{{ user.dob.age }}</p>
        <strong>{{ user.name.first }} {{ user.name.last }}</strong>
        <p>{{ user.gender }}</p>
        <p>{{ user.location.country }}</p>
        <p>{{ user.email }}</p>
      </li>
    </ul>
    <p v-if="error">{{ error }}</p>
    <!-- Modal -->
    <div v-if="selectedUser" class="modal">
      <div class="modal-content">
        <span class="close-btn" @click="closeModal">X</span>
        <h2>{{ selectedUser.name.first }} {{ selectedUser.name.last }}</h2>
        <p><strong>Age:</strong> {{ selectedUser.dob.age }}</p>
        <p>
          <strong>Address:</strong> {{ selectedUser.location.street.number }}
          {{ selectedUser.location.street.name }}, <br />
          {{ selectedUser.location.city }}, <br />
          {{ selectedUser.location.state }}, <br />
          {{ selectedUser.location.country }} - <br />
          {{ selectedUser.location.postcode }}
        </p>
        <p><strong>Phone:</strong> {{ selectedUser.phone }}</p>
        <p><strong>Cell:</strong> {{ selectedUser.cell }}</p>
      </div>
    </div>
  </div>
</template>

<script>
  import axios from "axios";

  export default {
    data() {
      return {
        users: [],
        error: null,
        results: 5,
        selectedUser: null,
        searchQuery: "",
        sortOrder: "a-z",
        currentPage: 1,
        maxPages: 10,
      };
    },
    async mounted() {
      this.fetchUsers();
    },
    methods: {
      async fetchUsers() {
        try {
          const response = await axios.get(
            `https://randomuser.me/api/?page=${this.currentPage}&results=${this.results}`
          );
          this.users = response.data.results;
        } catch (err) {
          this.error = "Error fetching data";
        }
      },
      openModal(user) {
        this.selectedUser = user;
      },
      closeModal() {
        this.selectedUser = null;
      },
      nextPage() {
        if (this.currentPage < this.maxPages) {
          this.currentPage++;
          this.fetchUsers();
        }
      },
      prevPage() {
        if (this.currentPage > 1) {
          this.currentPage--;
          this.fetchUsers();
        }
      },
    },
    computed: {
      filteredUsers() {
        let filtered = this.users;

        if (this.searchQuery) {
          filtered = filtered.filter((user) => {
            const fullName =
              `${user.name.first} ${user.name.last}`.toLowerCase();
            return fullName.includes(this.searchQuery.toLowerCase());
          });
        }

        if (this.sortOrder === "a-z") {
          filtered = filtered.sort((a, b) => {
            const nameA = `${a.name.first} ${a.name.last}`.toLowerCase();
            const nameB = `${b.name.first} ${b.name.last}`.toLowerCase();
            return nameA.localeCompare(nameB);
          });
        } else if (this.sortOrder === "z-a") {
          filtered = filtered.sort((a, b) => {
            const nameA = `${a.name.first} ${a.name.last}`.toLowerCase();
            const nameB = `${b.name.first} ${b.name.last}`.toLowerCase();
            return nameB.localeCompare(nameA);
          });
        }

        return filtered;
      },
    },
  };
</script>

<style scoped>
  div {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 100%;
    padding: 20px;
  }

  ul {
    width: 70vw;
    list-style-type: none;
    padding: 0;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  li {
    display: grid;
    grid-template-columns: auto 1fr 1fr 1fr 1fr 1fr;
    align-items: center;
    gap: 15px;
    padding: 15px;
    border: 2px solid transparent;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    transition: border-color 0.3s;
    height: 50px;
  }

  li.users:hover {
    border-color: lightblue;
  }

  li.header {
    font-weight: bold;
    text-transform: uppercase;
    box-shadow: none;
  }

  li img {
    width: 50px;
    height: 50px;
    border-radius: 50%;
  }

  strong,
  p {
    margin: 0;
    padding: 0;
  }

  button {
    padding: 10px 15px;
    cursor: pointer;
    background-color: #4caf50;
    color: #fff;
    border: none;
    border-radius: 4px;
    transition: background-color 0.2s;
  }

  button:hover {
    background-color: #45a049;
  }

  select {
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }

  .modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.7); /* Black with a bit of opacity */
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .modal-content {
    background-color: #ffffff;
    padding: 20px;
    border-radius: 5px;
    position: relative;
    width: 25%;
    height: 25%;
    display: flex;
    align-items: flex-start;
    justify-content: flex-start;
  }

  .close-btn {
    position: absolute;
    right: 15px;
    top: 5px;
    cursor: pointer;
    font-weight: bold;
  }

  .controls-bar {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    width: 70vw;
  }

  .controls-bar input {
    font-size: 20px;
  }

  .controls-bar select {
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    margin-left: 10px;
  }

  .pagination {
    display: flex;
    flex-direction: row;
    align-items: center;
    gap: 10px;
  }

  .pagination button {
    padding: 10px 15px;
    cursor: pointer;
    background-color: #4caf50;
    color: #fff;
    border: none;
    border-radius: 4px;
    transition: background-color 0.2s;
  }

  .pagination button:disabled {
    background-color: #ccc;
    cursor: not-allowed;
  }

  .pagination span {
    font-size: 1.2em;
  }

  .header-bar {
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    align-items: center;
    justify-content: center;
    width: 75%;
  }

  .logo {
    height: 75px;
    width: 150px;
    margin-left: 50px;
  }

  .icon-container {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: flex-end;
    gap: 10px;
    margin-right: 50px;
  }

  .icon {
    font-size: 24px;
    cursor: pointer;
    margin-left: 10px;
  }

  .icon:hover {
    opacity: 0.7;
  }
</style>
