<template>
    <card class="card-box">
      <div v-for="card in conteudoCard" v-bind:key="card" class="card-item">
        <div class="card-content">
          <img :src="card.icone">
          <h2>{{ card.titulo }}</h2>
          <p>{{ card.texto }}
          <a v-if="card.linkFont != undefined" :href="card.linkFont" target="_blank"> Fonte dos textos &#10084;</a>
          </p>
          
        </div>
      </div>
    </card>
</template>

<script>
export default {
  data(){
    return{
      conteudoCard: [
        {icone: './src/assets/img/ideia.svg', 
        titulo: `What's Glassmorphism?`, 
        texto: 'There is a new style on the block right now and it’s growing in popularity. While Neumorphism was imitating an extruded, plastic surface (but still looking like one layer), this new trend goes a bit more vertical. See it caractheristics in next card'},
        {icone: './src/assets/img/book.svg', 
        titulo: `Glassmorphism's caractheristics`, 
        texto: 'Transparency (frosted-glass effect using a Background Blur). Multi-layered approach with objects floating in space. Vivid colors to highlight the blurred transparency. A subtle, light border on the translucent objects.'},
        {icone: './src/assets/img/affection.svg', 
        titulo: 'Glassmorphism 2021?', 
        texto: 'Apple introducing this style into Big Sur is a sure way that it will be emulated and immitated in the months to come. It probably won’t take over all the interfaces (and that’s good), but it is going to be a bit more popular than it is right now',
        linkFont: 'https://uxdesign.cc/glassmorphism-in-user-interfaces-1f39bb1308c9'},
      ]
    }
  }
}
</script>

<style lang="scss" scoped>

$background: rgba(23, 171, 197, 0.267);

@mixin display-flex(){
  display: flex;
  justify-content: center;
  align-content: center;
}

%position-relative{
  position: relative;
}  


  .card-box, .card-content{
    @extend %position-relative;
  }

  .card-box{
    @include display-flex;
    flex-wrap: wrap;
    width: auto;
  }
  .card-item{
    @include display-flex;
    background: hsl(197, 71%, 73%);
    cursor: default;
    // Inicio - Efeito de bordas
    border-radius: 2%;
    border-top: 3px inset hsla(197, 96%, 78%, 0.596);
    border-left: 3px outset hsla(197, 57%, 72%, 0.596);
    border-bottom: 2px solid hsla(197, 69%, 59%, 0.596);
    border-right: 2px solid hsla(197, 69%, 59%, 0.596);
    box-shadow: -3px 3px 30px hsla(0, 12%, 7%, 0.761);
    // Fim - Efeito de bordas
    height: 400px;
    margin: 1em;
    overflow: hidden;
    position: relative;
    width: 350px;
    z-index: 2;
  }

  .card-content{
    padding: 2rem;
    text-align: left;
    &:hover{
      h2, p{
        opacity: 1;
        transform: translateY(0);
        z-index: 1;
      }
      img{
        opacity: .5;
        top: 1em;
        transform: translate3d(3.5em,0,0);
        z-index: 0;
      }
    }
    img{
      height: 100%;
      left: 50%;
      max-height: 100px;
      max-width: 100px;
      position: absolute;
      transform: translate3d(-50%, -50%, 0);
      transition: 0.5s;
      top: 50%;
      width: 100%;
    }
    h2, p{
      transform: translateY(-100px);
      transition: 1s all;
      opacity: 0;
    }
    h2{
      color: #e8e9e9;
      font-size: 1.5em;
      margin: 10px 0;
      text-transform: uppercase;
      text-shadow: 3px 5px 2px #47474765;
    }
    p{
      color: #fefefe;
      font-variant: normal;
      font-size: 1.3em;
      a{
        display: block;
        color: rebeccapurple;
        font-size: .7em;
        margin: 1em 0;
        text-decoration: none;
        text-transform: uppercase;
      }
    }
  }

  
</style>