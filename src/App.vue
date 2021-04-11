<template>
  <NavBar :conteo="carrito.length"/>
  <Cart :items="carrito" v-on:remover-item="removerProducto" v-on:pagar="pagar"/>

  <div class="container-fluid bg-secondary">
    <div class="row">
      <div class="col-md-12">
        <div class="row">
          <div class="col-md-2" v-for="prod in productos" :key="prod.id">
              <producto :producto="prod" v-on:agregar-carro="agregarProdCarro" :estaEnCarrito="estaEnCarrito(prod)"></producto>
          </div>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
import Producto from './components/Producto.vue'
import NavBar from './components/NavBar.vue'
import Cart from './components/Cart.vue'
import productos from './productos.json'

export default {
  name: 'App',
  components: {
    Producto,
    NavBar,
    Cart
  },
  data(){
    return{
      productos,
      carrito:[]
    }
  },
  methods:{
    agregarProdCarro(producto){
      this.carrito.push(producto);
    },
    estaEnCarrito(producto){
      const item= this.carrito.find(item => item.id === producto.id);
      if (item){
        return true;
      }
      return false;
    },
    removerProducto(producto){
      this.carrito=this.carrito.filter(item => item.id != producto.id);
    },
    pagar(){
      this.carrito=[];
      alert('Gracias por tu compra!');
    }
  }
}
</script>

<style>
  
</style>
