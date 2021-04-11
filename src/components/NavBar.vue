<template>
    <img src="../assets/image.jpg" width="1519" height="200" alt="">
     <nav class="navbar navbar-expand-sm bg-dark navbar-dark sticky-top justify-content-end">
            <a class="navbar-brand" href="#">Spectro Shop</a>
            <ul class="navbar-nav">
                <li class="nav-item">
                    <a class="nav-link" href="#">Nosotros</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link"><i class="fas fa-user-circle"></i></a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" data-toggle="modal" data-target="#myModal"> <i class="fas fa-shopping-cart"></i> </a>
                </li>
                <li>
                    <div id="articulos" v-if="conteo > 0">{{ conteo }}</div>
                </li>
                <li class="nav-item">
                    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                </li>
            </ul>
    </nav>
</template>

<script>
export default {
    name:'NavBar',
    props:['conteo']
}
</script>

<style>
    #articulos{
            display: inline-block;
            color: yellow;
        }
</style>