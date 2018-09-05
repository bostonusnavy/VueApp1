<template>
    <div class="test">

        <!-- using interpolation -->
        <h1>{{titleText}}</h1> <!-- injecting via interpolation -->
        <p>{{user.firstName}} {{user.lastName}}.</p> <!-- injecting via interpolation -->

        <br>
        <br>

        <!-- using directives -->
        <p v-html="titleHTML"></p> <!-- injecting via v-html parsing directive -->
        <p v-text="user.firstName"></p> <!-- injecting via v-text directive  -->

        <br>
        <br>

        <!-- conditionals: if/else -->
        <p>Is the conditional true:</p>
        <p v-if="showConditional">Yep, it sure is!</p>
        <p v-else>Nope, it ain't.</p>

        <br>
        <br>

        <!-- looping through an array: for loop -->
        <!-- also don't forget the v-bind:key="" -->
        <ul>
          <li v-for="item in items" v-bind:key="item">{{item.title}}</li>
        </ul>

        <br>
        <br>

        <!-- input binding using v-model directive -->
        <h2>Enter text in the following input to change the text below it:</h2>
        <input type="text" v-model="titleBind">
        <br>
        <h3>{{titleBind}}</h3>

        <br>
        <br>

        <!-- adding some interaction events -->
        <button v-on:click="greet('Greetings!')">Click for a greeting!</button>
        <p id="greetingClickText"></p>
        <br>
        <p>Type in the following input and watch the text dynamically appear below the input!</p>
        <input id="keyPressedInputElement" type="text" v-on:keyup="pressKey()">
        <p id="keyPressedInputValue"></p>
        <br>
        <p>Type text in the following input and the counter below it will tell you how many characters are in what you have typed:</p>
        <input id="keystrokeInputElement" type="text" v-on:keyup="countKeystrokes()">
        <p id="keystrokeCounterValue"></p>

        <br>
        <br>

    </div>
</template>

<script>
export default {
  name: 'test',
  data() {
    return {
      titleText: 'Hiya there, ',
      titleHTML: '<h1>Hey ho there, </h1>',
      titleBind: '',
      user: {
        firstName: 'John',
        lastName: 'Doe',
        isConditionalTrue: 'Yes',
      },
      showConditional: true,
      items: [
        {
          title: 'Item Number One',
        },
        {
          title: 'Item Number Two',
        },
        {
          title: 'Item Number Three',
        },
      ],
    };
  },
  methods: {
    greet: (greetingMessage) => {
      document.querySelector('#greetingClickText').innerHTML = greetingMessage;
    },
    pressKey: () => {
      document.querySelector('#keyPressedInputValue').innerHTML = document.querySelector('#keyPressedInputElement').value;
    },
    countKeystrokes: () => {
      document.querySelector('#keystrokeCounterValue').innerHTML = `There are ${document.querySelector('#keystrokeInputElement').value.length} characters in what you have typed.`;
    }
  },
};
</script>

<style scoped>

</style>
