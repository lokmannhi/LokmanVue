<template>
  <div>
    <div class="controls-bar">
      <input
        v-model="searchQuery"
        type="text"
        placeholder="Search by name..." />
      <select v-model="sortOrder">
        <option value="a-z">A-Z</option>
        <option value="z-a">Z-A</option>
      </select>
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

    <div class="pagination">
      <button @click="prevPage" :disabled="currentPage === 1">Previous</button>
      <span>{{ currentPage }}</span>
      <button @click="nextPage" :disabled="currentPage === 10">Next</button>
    </div>

    <div class="controls">
      <button @click="fetchUsers">Refresh</button>
      <select v-model="results" @change="fetchUsers">
        <option v-for="n in 20" :key="n" :value="n">{{ n }}</option>
      </select>
    </div>
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

  img {
    width: 50px;
    height: 50px;
    border-radius: 50%;
  }

  strong,
  p {
    margin: 0;
    padding: 0;
  }

  .controls {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    gap: 10px;
    margin-top: 20px;
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
    justify-content: space-around;
    align-items: center;
    width: 70vw;
    margin-bottom: 20px;
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
    margin-top: 20px;
    margin-bottom: 20px;
  }

  .pagination button {
    padding: 5px 10px;
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
</style>
