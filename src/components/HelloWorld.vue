<template id="product-list">
<div class="container">
  <div>  
    <div class = "row">
    <div class="col-lg-8 col-sm-8 col-xs-5">
    <p class = "nuevoProducto">NUEVO PRODUCTO</p>
	<hr> 
  </div>
  </div>
    <form v-on:submit.prevent="createProduct">
      <div class="form-group">
		    <div class="row">
			    <div class="col-lg-4 col-sm-4 col-xs-3">
				  <input v-model="products.name" class="form-control" id="add-name"  placeholder="Nombre" required/>
			</div>
			<div class="col-lg-2 col-sm-2 col-xs-2">
			<input v-model="products.price" class="form-control" id="add-price" placeholder="Precio" />
			</div>
			<div class="col-lg-2 col-sm-2 col-xs-2">
			<input v-model="products.quantity" class="form-control" id="add-price" placeholder="Cantidad"/>
			</div>
		</div>	
      </div>
      <div class="form-group">
      <div class="row">
      <div class="col-lg-6 col-sm-6 col-xs-4">
        <textarea v-model="products.description" class="form-control" id="add-description" rows="4" placeholder="Descripcion" ></textarea>
        </div>
        <div class="col-lg-2 col-sm-2 col-xs-1">
        <button type="submit" class="btn btn-primary addproducts">Agregar</button>
        </div>
        </div>
      </div>  
    </form>
  </div>
  <div class="row">
    <div class="form-group col-lg-8 col-sm-8 col-xs-5">
      <p class = "nuevoProducto">LISTADO DE PRODUCTOS</p>
      	<hr> 

       <div class="right-inner-addon ">
          <input v-model="search" class="form-control no-border glyphicon glyphicon-search" id="search-element"  placeholder="Filtrar" requred/>
      </div>    
    </div>
  </div>

  <div class = "container">
  <div class="row">
      <div class="col-lg-7 col-sm-7 col-xs-5">
<table class="table table-striped">
    <thead>
    <tr>
      <th>Nombre</th>
      <th>Descripcion</th>
      <th>Precio</th>
      <th>Cant.</th>
      <th>Borrar</th>
    </tr>
    </thead>
    <tbody>
    <tr v-for="product in filteredProducts">
      <td class="nameProduct">
        <a>{{ product.name }}</a>
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
  </div>
  </div>
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
			router.go('/')
        },
        createProduct(e)
          {
            this.products.push({
            id: Math.random().toString().split('.')[1],
            name: this.products.name,
            description: this.products.description,
            price: this.products.price,
            quantity: this.products.quantity
          });
          this.products.name = ""
          this.products.description = ""
          this.products.price = ""
          this.products.quantity = ""
          e.preventDefault();
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