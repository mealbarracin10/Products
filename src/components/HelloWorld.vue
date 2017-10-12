 <template id="product-list">
<div class="container">
<header class="page-header">
    <div class="branding">
      <img src="https://vuejs.org/images/logo.png" alt="Logo" title="Home page" class="logo"/>
      <h1>INVENTARIO APP</h1>
    </div>
  </header>
  <div class="filters row">
    <div class="form-group col-sm-3">
      <label for="search-element">LISTADO DE PRODUCTOS</label>
      <input v-model="search" class="form-control" id="search-element" requred/>
    </div>
  </div>

<table class="table">
    <thead>
    <tr>
      <th>Nombre</th>
      <th>Descripcion</th>
      <th>Precio</th>
      <th>Cant.</th>
      <th class="col-sm-2">Borrar</th>
    </tr>
    </thead>
    <tbody>
    <tr v-for="product in filteredProducts">
      <td>
        <a v-link="{name: 'product', params: {product_id: product.id}}">{{ product.name }}</a>
      </td>
      <td>{{ product.description }}</td>
      <td>
        {{ product.price }}
        <span class="glyphicon glyphicon-euro" aria-hidden="true"></span>
          <td>
        {{ product.quantity }}
        <span  aria-hidden="true">
          
        </span>
      </td>
      <td>
		<a class="btn btn-danger btn-xs" href="#" v-on:click="deleteproduct(product.id)">X</a>
      </td>
    </tr>
    </tbody>
  </table>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
	 search: '',
     products : [
  {id: 1, name: 'Leche', description: 'Parrafo muy largo con la descripcion del producto que se va a extender.', price: 2500, quantity: 100},
  {id: 2, name: 'Huevos', description: 'Descripcion bla bla bal', price: 200, quantity: 150},
  {id: 3, name: 'Pan', description: 'Descripcion bla bla bal.', price: 200, quantity: 150},
  {id: 4, name: 'Carne', description: 'Descripcion bla bla bal', price: 200, quantity: 50},
  {id: 5, name: 'Pollo', description: 'Descripcion bla bla bal', price: 200, quantity: 50},
  {id: 6, name: 'Chocolate', description: 'Descripcion bla bla bal.', price: 200, quantity: 50}
]
    }
  }, 
  methods: {
        deleteproduct(product_id){
		
			let i = this.products.map(item => item.id).indexOf(product_id)
			this.products.splice(i, 1)
			router.go('/');
        }	
    },
  computed: {
    filteredProducts() {
      return this.products.filter(item => {
         return item.name.toLowerCase().indexOf(this.search.toLowerCase()) > -1
      })
    }
  }
}
</script>

<style>
</style>
