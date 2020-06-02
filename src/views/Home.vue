/* eslint-disable vue/valid-template-root */
<template>
  <div>
    <label>Biblioteca Fulanito</label>
    <br />
    <select v-model="selectedOption">
      <option>All</option>
      <option>Books</option>
      <option>Magazines</option>
      <option>Newspapers</option>
      <option>Others</option>
    </select>
    <br />

    <input v-model="name" placeholder="Busqueda" />
    <br />

    <table>
      <thead>
        <tr>
          <th>Code</th>
          <th>Name</th>
          <th>Description</th>
          <th>Category</th>
        </tr>
      </thead>
    </table>

    <div :key="item.name + '1'" v-for="item in list">
      <table>
        <tfoot>
          <tr>
            <td>{{ item.code }}</td>
            <td>{{ item.name }}</td>
            <td>{{ item.description }}</td>
            <td>{{ item.category }}</td>
          </tr>
        </tfoot>
      </table>
    </div>
    <br />
    <div :key="item.name" v-for="item in filterList">
      <table>
        <tr>
          <td>{{ item.code }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.description }}</td>
          <td>{{ item.category }}</td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  components: {
    //Nothing
  },

  data() {
    return {
      name: "",
      list: [
        {
          code: "B1",
          name: "book1",
          description: "This is the book1",
          category: "Books"
        },
        {
          code: "M1",
          name: "Magazine1",
          description: "This is the Magazine1",
          category: "Magazines"
        },
        {
          code: "N1",
          name: "Newpaper1",
          description: "This is the newpaper1",
          category: "Newspapers"
        },
        {
          code: "O1",
          name: "other1",
          description: "This is the other1",
          category: "Others"
        },
        {
          code: "B2",
          name: "book2",
          description: "This is the book2",
          category: "Books"
        },
        {
          code: "M2",
          name: "Magazine2",
          description: "This is the Magazine2",
          category: "Magazines"
        },
        {
          code: "N2",
          name: "Newpaper2",
          description: "This is the newpaper2",
          category: "Newspapers"
        },
        {
          code: "O2",
          name: "other2",
          description: "This is the other2",
          category: "Others"
        }
      ]
    };
  },

  computed: {
    filterList() {
      return this.name === ""
        ? this.list
        : this.list.filter(
            item =>
              item.category === this.name ||
              item.name === this.name ||
              item.code === this.name ||
              item.description === this.name
          );
    }
  }
};
</script>

<style src="./home.css"></style>
