<template>
  <div class="main-view">
    <table id="table-content">
      <tr>
        <th>Title</th>
        <th>URL</th>
        <th>Language</th>
      </tr>
      <tr v-for="repo in repos" :key="repo.id">
        <td>{{ repo.name }}</td>
        <td>
          {{ repo.url }}
        </td>
        <td>{{ repo.language }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "MainView",
  data() {
    return {
      repos: null,
    };
  },
  created() {
    this.reposFetch();
  },
  methods: {
    async reposFetch() {
      const response = await axios.get(
        "https://api.github.com/users/apple890493/repos"
      );
      this.repos = response.data;
    },
  },
};
</script>

<style scoped>
.main-view {
  background: rgba(255, 255, 255, 0.5);
  height: 300px;
  overflow-y: scroll;
}

#table-content {
  font-family: Arial, Helvetica, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

#table-content td,
#table-content th {
  border: 1px solid #ddd;
  padding: 10px;
}

#table-content tr:nth-child(even) {
  background-color: #f2f2f2;
}

#table-content tr:hover {
  background-color: #ddd;
  cursor: pointer;
}

#table-content th {
  padding: 12px 0;
  text-align: center;
  background-color: #008080;
  color: #fff;
}
</style>

// https://api.github.com/users/apple890493/repos
