<template>
  <div class="main-view" @scroll="loadMore">
    <table id="table-content">
      <tr>
        <th>Title</th>
        <th>URL</th>
        <th>Language</th>
      </tr>
      <tr v-for="repo in repos" :key="repo.id">
        <td>{{ repo.name }}</td>
        <td>
          <a :href="repo.html_url">{{ repo.html_url }}</a>
        </td>
        <td>{{ repo.language }}</td>
      </tr>
    </table>

    <transition name="fade">
      <p v-if="isLoading" class="loading">{{ message }}</p>
    </transition>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "MainView",
  data() {
    return {
      loadStart: 0,
      loadEnd: 5,
      isLoading: false,
      repos: [],
      message: "Loading...",
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
      this.isLoading = false;
      let data = response.data.slice(this.loadStart, this.loadEnd);
      if (!data.length) {
        this.message = "No information";
        return;
      }
      this.repos.push(...data);
      this.loadStart += 5;
      this.loadEnd += 5;
    },
    loadMore(e) {
      let { scrollTop, clientHeight, scrollHeight } = e.target;
      if (!this.isLoading && scrollTop + clientHeight >= scrollHeight) {
        console.log(scrollTop + clientHeight, scrollHeight);
        this.isLoading = true;
        setTimeout(() => {
          this.reposFetch();
        }, 1000);
      }
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

#table-content td {
  height: 55px;
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

.loading {
  position: absolute;
  bottom: 15%;
  left: 0;
  right: 0;
  margin: auto;
  width: 100px;
  padding: 20px 10px;
  border-radius: 20px;
  text-align: center;
  background: #345047;
  color: #fff;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
