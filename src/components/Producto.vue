<template>
    <div class="card my-5">
        <img :src="producto.imagen" alt="" class="card-img-top">
        <div class="card-body">
            <h5 class="card-title text-center">{{ producto.nombre }}</h5>
            <p class="card-text text-center text-muted">${{ Number(producto.precio).toFixed() }}.00</p>
            <button @click="agregarCarro(producto)" class="btn btn-outline-dark form-control" :disabled="estaEnCarrito"> 
                <i class="fas fa-cart-plus"></i> {{  estaEnCarrito ? 'Agregado' : 'Agregar al carrito'}}
            </button>
        </div>
    </div>
</template>

<script>
export default {
    name:'Producto',
    props:['producto', 'estaEnCarrito'],
    methods:{
        agregarCarro(producto){
            this.$emit('agregar-carro', producto);
        }
    }
}
</script>

<style>

</style>