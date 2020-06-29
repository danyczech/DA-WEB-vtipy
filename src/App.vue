<template>
  <div id="app">

    <h1>Dad Jokes</h1>

    <joke v-for="joke in jokes"
      v-bind:key="joke.id"
      v-bind:id="joke.id"
      v-bind:user="joke.user"
      v-bind:jokeText="joke.jokeText"
      v-bind:like="joke.like"
      v-bind:dislike="joke.dislike"
      v-on:zmenit-like="zmenitLike ($event)"
      v-on:zmenit-dislike="zmenitDislike ($event)"
    />

    <!--
      
      Toto je HTML šablona pro jeden vtip.
      Pro vtip ale chceme mít samostatnou komponentu nazvanou Joke.
      Vytvoř komponentu, vezmi HTML zakomentované níže a vlož ho
      dovnitř template komponenty.

      Do komponenty posílej potřebné props a jejich hodnoty zobrazuj
      místo textu vtipů a počtů lajků, které jsou teď v šabloně
      zadané natvrdo. Nezapomeň i na ikonku uživatele.

      Zde uvnitř App vue pak procházej pole vtipů pomocí v-for
      a zobrazuj komponentu Joke pro každý vtip na seznamu.

      Zařiď, aby tlačítka v komponentě fungovala a emitovala sem
      do App.vue události, které zde budou spouštět příslušné metody,
      které změní počty lajků u vtipu v poli.
    -->
    <!--
    <div class="joke">
      <div class="joke-body">
        <img class="joke-user" src="/images/users/user01.png" />
        <p class="joke-text">
          The secret service isn't allowed to yell "Get down!" anymore when the president is about to be attacked. Now they have to yell "Donald, duck!"
        </p>
      </div>
      <div class="joke-likes">
        <button class="btn-like btn-up"></button>
        <span class="likes-count likes-up">0</span>

        <button class="btn-like btn-down"></button>
        <span class="likes-count likes-down">0</span>
      </div>
    </div>
    -->

  </div>
</template>


<script>
import Joke from './components/Joke.vue'

export default {

  components: {
    joke: Joke
  },

  methods: {
    zmenitLike (id) {
      const index = this.jokes.findIndex (joke => joke.id === id);
      this.jokes[index].like ++;
    }, 

    zmenitDislike (id) {
      const index = this.jokes.findIndex (joke => joke.id === id);
      this.jokes[index].dislike ++;
    } 

  },

  data () {
    return {
      jokes: [
        {id: 1, user: 'user01', jokeText: 'The secret service is not allowed to yell "Get down!" anymore when the president is about to be attacked. Now they have to yell "Donald, duck!"', like: 13, dislike:24},
        {id: 2, user: 'user02', jokeText: 'Why did the invisible man turn down the job offer? He could not see himself doing it.', like: 50, dislike: 8 },
        {id: 3, user: 'user03', jokeText: 'I bought some shoes from a drug dealer. I dont know what he laced them with, but I was tripping all day!', like: 30, dislike: 2},
        {id: 4, user: 'user04', jokeText: 'Did you hear the news? FedEx and UPS are merging. They are going to go by the name Fed-Up from now on.', like:15 , dislike:8 },
        {id: 5, user: 'user05', jokeText: 'My daughter screeched, "Daaaaaad, you have not listened to one word I have said, have you!?" What a strange way to start a conversation with me...', like: 90, dislike:44 },
        {id: 6, user: 'user06', jokeText: 'My wife tried to unlatch our daughters car seat with one hand and said, "How do one armed mothers do it?" Without missing a beat I replied, "Single handedly."', like: 38, dislike: 1},
        {id: 7, user: 'user07', jokeText: 'When a dad drives past a graveyard: Did you know that is a popular cemetery? Yep, people are just dying to get in there!', like: 66, dislike: 35},
        {id: 8, user: 'user08', jokeText: 'My friend keeps saying "cheer up man it could be worse, you could be stuck underground in a hole full of water." I know he means well.', like:27 , dislike:18 },
        {id: 9, user: 'user09', jokeText: 'The fattest knight at King Arthurs round table was Sir Cumference. He acquired his size from too much pi.', like:42 , dislike:9 }
      ]
    }
  }

}
</script>



<style>
html {
  box-sizing: border-box;
}

*, ::before, ::after {
  box-sizing: inherit;
}

body {
  font-family: sans-serif;
}

h1 {
  text-align: center;
}

.joke {
  max-width: 40rem;
  margin: 2rem auto;
}

.joke-body {
  display: flex;
}

.joke-user {
  flex: 0 0 auto;
  width: 5rem;
  height: 5rem;
  margin-right: 1rem;
}

.joke-text {
  background-color: cornflowerblue;
  color: white;
  border-radius: 1rem;
  padding: 1.5rem 2rem;
  margin: 0;
  line-height: 150%;
}

.joke-likes {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  margin-top: 1rem;
}

.likes-count {
  font-size: 1.5rem;
  font-weight: bold;
  margin: 0 0.5rem;
}

.likes-up {
  color: #00e268;
}

.likes-down {
  color: #ff5654;
}

.btn-like {
  border: none;
  outline: none;
  width: 2rem;
  height: 2rem;
  border-radius: 1rem;
  background-size: 1.2rem;
  background-position: center;
  background-repeat: no-repeat;
  cursor: pointer;
  transition: transform 0.3s;
}

.btn-like:hover {
  transform: scale(1.2);
}

.btn-up {
  background-color: #00e268;
  background-image: url('/images/like-up.png');
}

.btn-down {
  background-color: #ff5654;
  background-image: url('/images/like-down.png');
}

</style>
