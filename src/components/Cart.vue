<template>
    <div class="modal fade" id="myModal">
    <div class="modal-dialog">
      <div class="modal-content">
      
        <!-- Modal Header -->
        <div class="modal-header">
          <h4 class="modal-title">{{ items.length === 0 ? 'Carrito vacío' : 'Pedido'}}</h4>
          <button type="button" class="close" data-dismiss="modal">&times;</button>
        </div>
        
        <!-- Modal body -->
        <div class="modal-body" v-if="items.length > 0">
          <div class="row" v-for="item in items" :key="item.id">
              <div class="col-2">
                  <input type="number" min="1" value="1" style="width:100%">
              </div>
              <div class="col-3">
                  <img :src="item.imagen" width="45" height="45">
              </div>
              <div class="col-4">
                  <h6>{{ item.nombre }}</h6>
              </div>
              <div class="col-2">
                  <h6>${{ item.precio }}.00</h6>
              </div>
              <div class="col-1">
                  <i class="fas fa-times" @click="removerItem(item)"></i>
              </div>
          </div>
        </div>

        <!-- Modal body secondary -->
        <div class="modal-body" v-if="items.length === 0">
          <div class="row">
              <div class="col-12">
                  <h6>No ha añadido artículos al carrito.</h6>
              </div>
          </div>
        </div>
       
       
        
        <!-- Modal footer -->
        <div class="modal-footer">
          <button type="button" class="btn btn-primary" data-dismiss="modal" @click="$emit('pagar')" :disabled="items.length === 0" v-if="items.length > 0">Comprar ${{ total }}</button>
        </div>
        
      </div>
    </div>
  </div>
</template>

<script>
export default {
    name:'Cart',
    props:['items'],
    computed:{
      total(){
        return this.items.reduce( (acumulador, item) => acumulador+Number(item.precio),0);
      }
    },
    methods:{
      removerItem(item){
        this.$emit('remover-item', item);
      }
    }
}
</script>

<style>

</style>