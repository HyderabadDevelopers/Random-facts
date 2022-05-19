<template>
<div id='app'>
  <main>

    <div class='button-box'>
      <div class='button-container'>
        <input type='button' class='button-55' value='Tell me a new fact...' @click='fetchFact'/>
      </div>
    </div>

    <div class='fact-wrap'>
      <div class='fact-box'>
        <div class='fact'>{{facts.text}}</div>
      </div>
    </div>

    <div class='creator-wrap'>
      <div class='creator-name'>developed by Rahul Pareek</div>
    </div>

  </main>
</div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      url_base: 'https://uselessfacts.jsph.pl/random.json?language=en',
      facts: {}
    }
  },
  methods: {
    fetchFact()
    {
      try {
        fetch(this.url_base).then(res=> {
          return res.json();
        }).then(this.setResults);
      }
      catch{
        var obj = {
          "text": "Cats are cute. That's all",
          "_id":"123"
        };
        this.facts=obj;
      }
    },
    setResults(results) {
      this.facts = results;
    }
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'monoserrat', sans-serif;
}

#app {
  background-image: url('./assets/fact.jpg');
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
  background-color: pink;
}

main {
  min-height: 100vh;
  padding: 25px;

  background-image: linear-gradient(to bottom, rgba(0,0,0,0.25), rgba(0,0,0,0.75));
}

.button-55 {
  align-self: center;
  background-color: #fff;
  background-image: none;
  background-position: 0 90%;
  background-repeat: repeat no-repeat;
  background-size: 4px 3px;
  border-radius: 15px 225px 255px 15px 15px 255px 225px 15px;
  border-style: solid;
  border-width: 2px;
  box-shadow: rgba(0, 0, 0, .2) 15px 28px 25px -18px;
  box-sizing: border-box;
  color: #41403e;
  cursor: pointer;
  display: inline-block;
  font-family: Neucha, sans-serif;
  font-size: 1rem;
  line-height: 23px;
  outline: none;
  padding: .75rem;
  text-decoration: none;
  transition: all 235ms ease-in-out;
  border-bottom-left-radius: 15px 255px;
  border-bottom-right-radius: 225px 15px;
  border-top-left-radius: 255px 15px;
  border-top-right-radius: 15px 225px;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
}

.button-55:hover {
  box-shadow: rgba(0, 0, 0, .3) 2px 8px 8px -5px;
  transform: translate3d(0, 2px, 0);
}

.button-55:focus {
  box-shadow: rgba(0, 0, 0, .3) 2px 8px 4px -6px;
}

.button-box{
  height: 200px;
  position: relative;
}

.button-container{
  margin: 0;
  position: absolute;
  top: 50%;
  left: 50%;
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
}

.fact{
  color: white;
  font-size: 20px;
  font-weight: 200;
  text-align: center;
  text-shadow: 1px 3px rgba(0,0,0,0.25);

  background-color:rgba(255,255,255,0.1);
  border-radius: 16px;
  margin: 30px 0px;
}

.creator-wrap {
    position: fixed; 
    background: rgba(255,0,0,0.25); 
    width:100%;
    bottom:0;
}

.creator-name {
  align-self: center;
  color: white;
  font-size: 12px;
}
</style>
