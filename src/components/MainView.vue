<template>
  <div class="main-view">
    <table id="table-content">
      <tr>
        <th>Title</th>
        <th>Description</th>
        <th>URL</th>
        <th>Language</th>
      </tr>
      <tr>
        <td>Alfreds Futterkiste</td>
        <td>Maria Anders</td>
        <td>
          GermanGermanyGermanyGermanyGermanyGermanyGermanyGermanyGermanyGermanyy
        </td>
        <td>Germany</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "MainView",
};
</script>

<style scoped>
.main-view {
  background: rgba(255, 255, 255, 0.5);
  /* width: 800px; */
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
