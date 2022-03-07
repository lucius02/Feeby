<template>
  <div id="home">
    <HeaderCom />
    <div id="search-bar">
      <div class="search-wrapper panel-heading col-sm-12">
        <input v-model="search" type="text" placeholder="Search"> <br> <br>
      </div>
      <table id="myTable" class="table">
        <thead>
          <tr>
            <th>ID</th>
            <th>Name</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="product in filteredProducts" :key="product.id">
            <td>{{ product.id }}</td>
            <td>{{ product.name }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import HeaderCom from './HeaderCom.vue'
export default {
  name: 'HomePage',
  components: { HeaderCom },
  data () {
    return {
      products: [
        { id: 1, name: 'Foo' },
        { id: 2, name: 'Bar' },
        { id: 3, name: 'Baz' },
        { id: 4, name: 'Foobar' }
      ],
      search: ''
    }
  },
  computed: {
    filteredProducts () {
      return this.products.filter((p) => {
        // return true if the product should be visible
        // in this example we just check if the search string
        // is a substring of the product name (case insensitive)
        return p.name.toLowerCase().includes(this.search.toLowerCase())
      })
    }
  }
}
</script>

<style scoped>

</style>
