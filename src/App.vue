<template>
  <div id="app">
    <nav class="navbar is-dark" role="navigation" aria-label="main navigation">
  <div class="navbar-brand">
    <a class="navbar-item" href="/">
      How Many Clicks In 10 Seconds?
    </a>
    <a role="button" class="navbar-burger" aria-label="menu" aria-expanded="false">
      <span aria-hidden="true"></span>
      <span aria-hidden="true"></span>
      <span aria-hidden="true"></span>
    </a>
  </div>
</nav>
<hr>
  
    <h1 v-if="timer >0"> Time: {{ timer }} </h1>
    <h1 v-if="timer<=0"> Your New Score <b>{{ newScore }}</b></h1>
    <h1 v-if="timer>0">Clicks: {{ counter }}</h1>
  
    <article v-if="oldScore < newScore && timer<=0 " class="message is-success">
        <b-message title="New Personal Record!" aria-close-label="Close message">
            Congratulations! You have accomblished a new personal recored with <b> {{ newScore }} </b> clicks
        </b-message>
</article>
    <br>
    <a v-if="timer>0" class="button is-danger is-large" @click="increase">Click</a>
    <a v-if="timer<=0" class="button is-warning is-large" @click="restart">Restart</a>
</div>
</template>

<script src="https://unpkg.com/vue/dist/vue.js"></script>
<script>


export default {
  data: function(){
    return { 
      counter: 0,
      timer:10,
      newScore:0,
      oldScore:0,
  }
  },
  methods: {
    increase() {
      this.counter++;
      this.newScore = this.counter;
    },
    decrease(){
      this.timer--;
    },
    restart(){
      this.counter = 0;
      this.oldScore = this.newScore;
      this.newScore = 0;
      this.timer = 10;
    }
  },
  mounted: function(){   
    setInterval(() => {
      this.timer -= 1
    }, 1000);
  }
};
</script>

<style>
#app {
  font-family: "Montserrat", sans-serif;
  text-align: center;
  color: #2c3e50;
  font-size:2.4em;
}
#navbar{
  font-size:0.4em;
}
</style>
