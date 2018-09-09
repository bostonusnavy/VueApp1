<template>
    <div class="testComponentClass">

        <!-- using interpolation -->
        <h1>Interpolation</h1>
        <p>{{ titleText }}</p> <!-- injecting via interpolation -->
        <p>{{ user.firstName }} {{ user.lastName }}.</p> <!-- injecting via interpolation -->

        <hr>

        <!-- using directives -->
        <h1>Directives</h1>
        <p v-html="titleHTML"></p> <!-- injecting via v-html parsing directive -->
        <p v-text="user.firstName"></p> <!-- injecting via v-text directive  -->
        <p v-text="user.lastName"></p>

        <hr>

        <!-- conditionals: if/else -->
        <h1>If and Else Conditionals</h1>
        <p>Is the conditional true:</p>
        <p v-if="showConditional">Yep, it sure is!</p>
        <p v-else>Nope, it ain't.</p>

        <hr>

        <!-- looping through an array: for loop -->
        <!-- also don't forget the v-bind:key="" -->
        <h1>Looping and Bind Key</h1>
        <ul>
          <li v-for="item in items" v-bind:key="item">{{item.title}}</li>
        </ul>

        <hr>

        <!-- input binding using v-model directive -->
        <h1>V-model Directives</h1>
        <p>Enter text in the following input to change the text below it:</p>
        <input type="text" v-model="titleBind">
        <br>
        <h3>{{ titleBind }}</h3>

        <hr>

        <!-- adding some interaction events -->
        <h1>Event Handlers</h1>
        <p>Click the button below for a greeting.</p>
        <button v-on:click="greet('Greetings!')">Click me!</button>
        <p id="greetingClickText"></p>
        <br>
        <p>Type in the following input and watch the text dynamically appear below the input!</p>
        <input id="keyPressedInputElement" type="text" v-on:keyup="pressKey()">
        <br>
        <i id="keyPressedInputValue"></i>
        <br>
        <p>Type text in the following input.</p>
        <p>A counter below it will tell you how many characters are in your phrase:</p>
        <input id="inputCharacterCounterElement" type="text" v-on:keyup="countStringCharacters()">
        <p id="characterCounterValue"></p>

        <hr>

        <h1>Computed Properties: First and Last Name</h1>
        <label>First Name: </label><input type="text" v-model="user.firstName">
        <br>
        <label>Last Name: </label><input type="text" v-model="user.lastName">
        <br>
        <!-- <h3>{{ fullName }}</h3> -->
    </div>
</template>

<script>
export default {
  name: 'testComponent',
  data() {
    return {
      titleText: 'Hiya there, ',
      titleHTML: '<p>Hey ho there, </p>',
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
    countStringCharacters: () => {
      document.querySelector('#characterCounterValue').innerHTML = `There are ${document.querySelector('#characterCounterInputElement').value.length} characters your phrase.`;
    },
  },
  computed: {
    fullName: () => {
      const concatFullName = `${this.user.firstName} ${this.user.lastName}`;

      return concatFullName;
    },
  },
};
</script>

<style scoped>
</style>
