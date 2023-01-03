<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p v-if="abonnes == 0">Aucun abonnés :'(</p>
    <p v-else-if="abonnes == 1">Une personne s'est abonnée !</p>
    <p v-else>{{abonnes}} personnes sont abonnées 🎉</p>
    <button v-on:click="subscribe()">S'abonner !</button>
    <div class="comment" v-for="comment, idx in comments" v-bind:key="idx">
      <h3>{{comment.nom}}</h3>
      <p>{{comment.commentaire}}</p>

      <div v-if="comment.note > 1">
        <span v-for="i in comment.note" v-bind:key="i">⭐</span>
      </div>
      <span v-else>🌟</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data: function () {
    return {
      abonnes: 0,
      comments: [{
        nom : 'Toto',
        commentaire: "blablabla",
        note : 3,
      },
      {
        nom : 'Titi',
        commentaire: "le ciel est bleu",
        note : 5,
      },
      {
        nom : 'Grominet',
        commentaire: "Sabristi-saucisse !",
        note : 1,
      }
    
    ],
    }
  },
  methods: {
    subscribe: function () {
      this.abonnes++;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

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

p {
  font-size: 22px;
}


</style>
