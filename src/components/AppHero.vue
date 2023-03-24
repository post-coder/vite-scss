<script>
export default {
  data() {
    return {
      heroTitle: "Ecco il titolo del jumbotron",
    };
  },
};
</script>

<template>

  <div id="hero">

    <h2>{{ heroTitle }}</h2>

    <h3>
      Sottotitolo
    </h3>

    <button class="btn">
      pulsante normale
    </button>

    <button class="btn btn-primary">
      pulsante primario
    </button>

  </div>

  <div id="hero-bottom">
    un altro elemento da centrare
  </div>

</template>

<style lang="scss" scoped>
// le variabili si identificano con un $
// possiamo chiamarle come vogliamo
$main-color: #ff6622;
$altezza-jumbotron: 500px;
$giustificazione-jumbotron: center;



// adesso con scss possiamo definire delle specie di funzioni
// che possono ripetere (o elaborare) le regole css per noi
// si chiamano mixin
// questa è la sintassi, possiamo chiamarle come vogliamo
@mixin centratura() {
  // qua dentro scriviamo le proprietà che vogliamo attribuire alla mixin (funzione)
  display: flex;
  flex-direction: column;
  justify-content: $giustificazione-jumbotron;
  align-items: center;
}


// stilizzare un pulsante
@mixin styilizeButton($color, $padding) {
  padding: $padding;

  border-radius: 4px;

  border: 1px solid $color;
  background-color: darken($color, 20%);

  color: white;
}


#hero {

  // per chiamare una mixin si usa @include
  // l'unica cosa che fa @include è prendere il contenuto della mixin e inserirlo
  // nel codice.
  @include centratura();

  position: relative;

  height: $altezza-jumbotron;

  background-image: url("/img/04-29.jpg");
  background-position: cover;
  background-repeat: no-repeat;
  background-position: bottom;

  * {
    z-index: 1;
  }

  h2 {
    color: $main-color;
  }

  h3 {
    color: $main-color;
  }

  // la "&" si riferisce al selettore "genitore"
  // è come se venga sostituita in tutto e per tutto con il nome del genitore
  .btn {
    @include styilizeButton(grey, 8px);
    margin: 8px;

    &-primary {
      @include styilizeButton($main-color, 16px);
    }

  }

  // la "&" si riferisce al selettore "genitore"
  // è come se venga sostituita in tutto e per tutto con il nome del genitore
  &::before {
    content: "";

    position: absolute;
    top: 0;
    left: 0;

    width: 100%;
    height: 100%;

    background-color: black;

    opacity: 0.8;
  }
}
  
#hero-bottom {
  
  // richiamiamo anche qua la mixin
  @include centratura();

  height: 200px;
}





</style>
