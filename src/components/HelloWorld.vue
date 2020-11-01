<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <ul>
      <li>
        <p>{{cards[counter].question}}</p>
        <p>{{cards[counter].answer}}</p>
      </li>
    </ul> 
    <button v-on:click="counter++">+</button>
    <button v-on:click="counter--">-</button>
    <div>
    <button v-on:click="shuffleDeck()">-</button>
      
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  data: function () {
    return {
    counter: 1,
    cards : [
      {
        question: 'Lorsque des chercheurs anglais ont inventé la première webcam, pour quoi a-t-elle été utilisée ?',
        answer: 'La surveillance de leur machine à café.',
        detail: 'Les chercheurs voulaient simplement vérifier s il restait du café dans la pièce d à côté.',
        category: 'wtf'
      },
      {
        question: 'Il y 100 millions d années, pourquoi aurait-il été impossible de prendre un bain de minuit ?',
        answer: 'Parce que les jours ne duraient que 23 heures.',
        detail: 'À sa formation, il y a 4 milliards d années, la journée terrestre ne durait que 6 heures.',
        category: 'vie de la terre'
      },
            {
        question: 'En 1979, le fermier Argentin Pedro Martin Ureta réalise un étrange hommage à sa femme décédée. Lequel ?',
        answer: 'Il a fait pousser un forêt en forme de guitare.',
        detail: 'La forêt et composée de 7000 arbres et mesure plus d un kilomètre de longueur.',
        category: 'histoire'
      },
    ]
    }
  },
  methods: {
    shuffleDeck() {        
      for(let i = this.cards.length - 1; i > 0; i--) {
        let randomIndex = Math.floor(Math.random() * i);
        
        let temp = this.cards[i];
        this.$set(this.cards, i, this.cards[randomIndex]);
        this.$set(this.cards, randomIndex, temp);
      }
    },
  },
  computed: {
    }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
