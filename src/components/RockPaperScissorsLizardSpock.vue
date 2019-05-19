<template lang="html">
  <div class="main-game">
    <div v-for="(defeated_by, hand, index) in hands" @click="user_hand = hand">
      {{ index }}. {{ hand }}: {{ defeated_by }}
    </div>
    <div>
      You picked {{user_hand}}
    </div>
    <button class="play-game" @click="computer_picks()">Computer picks</button>
    <div>
      Computer picked {{computer_hand}}
    </div>
    <button class="compute-winner" @click="compute_winner()">Play the Computer!</button>
    <div>
      The winner is {{winning_hand}}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      hands: {
        paper: ["scissors", "lizard"],
        rock: ["paper", "spock"],
        lizard: ["rock", "scissors"],
        spock: ["lizard", "paper"],
        scissors: ["spock", "rock"]
      },
      user_hand: null,
      computer_hand: null,
      winning_hand: null
    };
  },
  methods: {
    computer_picks() {
      var keys = Object.keys(this.hands)
      console.log(keys);
      // this.computer_hand = this.hands[keys[keys.length * Math.random() << 0]];
      this.computer_hand = keys[keys.length * Math.random() << 0];
    },
    compute_winner() {
      console.log("user hand:", this.user_hand, this.hands[this.user_hand]);
      console.log("computer hand:", this.computer_hand, this.hands[this.computer_hand]);
      if (this.user_hand === this.computer_hand) {
        this.winning_hand = "It's a draw!"
      };
      if (this.hands[this.user_hand].includes(this.computer_hand)) {
        this.winning_hand = "COMPUTER!"
      };
      if (this.hands[this.computer_hand].includes(this.user_hand)) {
        this.winning_hand = "YOU!"
      };
    }
  }
}
</script>

<style lang="css" scoped>
</style>
