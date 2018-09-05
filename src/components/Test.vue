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
    </div>
</template>

<script>
export default {
  name: 'test',
  data() {
    return {
      titleText: 'Hiya there, ',
      titleHTML: '<h1>Hey ho there, </h1>',
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
};
</script>

<style scoped>

</style>
