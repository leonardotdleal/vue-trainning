<template>
  <div class="template">
    <h2>Incrementador</h2>
    <h3>{{ counter }}</h3>
    <span v-if="message">{{ message }}</span>
    
    <div class="increment">
      <span>Exemplo utilizando lógica inline e com a diretiva v-on e @click</span>
      <div>
        <button v-on:click="counter--">Decrement</button>
        <button @click="counter++">Increment</button>
      </div>
    </div>
    
    <div class="increment">
      <span>Exemplo utilizando método e com a diretiva v-on e @click</span>
      <div>
        <button v-on:click="decrement">Decrement</button>
        <button @click="increment()">Increment</button>
      </div>
    </div>

    <div class="increment">
      <span>Exemplo utilizando método passando parâmetros</span>
      <div>
        <button v-on:click="sub(value)">Sub</button>
        <input type="number" v-model="value"/>
        <button v-on:click="sum(value)">Sum</button>
      </div>
    </div>

    <div class="increment">
      <span>Exemplo utilizando modificadores de evento (prevent, stop, once...)</span>
      <div>
        <button v-on:click.prevent="prevent()">Check number</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      counter: 0,
      value: 0,
      message: ""
    };
  },
  methods: {
    decrement() {
      this.counter--;
    },
    increment() {
      this.counter++;
    },
    sub(value) {
      this.counter -= Number(value);
    },
    sum(value) {
      this.counter += Number(value);
    },
    prevent() {
      let isMultipleOfTwo = (this.counter % 2 === 0);
      let isMultipleOfThree = (this.counter % 3 === 0);

      if (isMultipleOfTwo && isMultipleOfThree) {
        this.message = "É divisível por 2 e 3";
        return;
      }

      if (isMultipleOfTwo) {
        this.message = "É divisível por 2";
        return;
      }

      if (isMultipleOfThree) {
        this.message = "É divisível por 3";
        return;
      }

      this.message = "";
    }
  }
}
</script>

<style scoped>

.increment {
  display: flex;
  padding: 20px 0;
  flex-direction: column;
}

.template {
  align-items: center;
  display: flex;
  flex-direction: column;
}

</style>