<template>
  <div id="app">
    <h1 class="titulo-principal">{{ msg }}</h1>
    <card></card>
  </div>
</template>

<script>
import VanillaTilt from './assets/js/vanilla-tilt.js';
import card from './components/Cards.vue';

export default {
  name: 'app',
  components: { 
   'card': card
  },
  data () {
    return {
      msg: 'Um estudo sobre Glassmorphis'
    }
  },
}
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
}

#app{
  align-content: center;
  background: #17abc544;
  background: url(./assets/img/triangles.png) no-repeat center / cover;
  display: flex;
  flex-direction: column;
  justify-content: center;
  min-height: 100vh;
}

// Criar efeito 3D - Título
@mixin render-shadow(
  $first, $second, $color,
  $hsl-initial: 80, $hsl-step: 1,
  $hsl-alpha-initial: 1, $hsl-alpha-step: .1
  ) {
    $firstShadow: ();
    @for $i from 1 through $first {
      $firstShadow: append(
        $firstShadow, 0px  $i * 1px 0px
        hsl(0, 0, ($hsl-initial - ($i * $hsl-step)))
      ),;
    }
    $secondShadow: ();
    @for $v from 1 through $second {
      $secondShadow: append(
        $secondShadow, -4px $v * 1px 50px
        hsla(0, 0, 0, ($hsl-alpha-initial - ($v * $hsl-alpha-step)))
      ),;
    }
    color: $color;
    text-shadow: $firstShadow, $secondShadow;
}

.titulo-principal{
  font-weight: bold;
  letter-spacing: .2em;
  padding: .8em;
  text-align: center;
  text-transform: uppercase;
  @include render-shadow(3, 5, #fefefe);
}

</style>
