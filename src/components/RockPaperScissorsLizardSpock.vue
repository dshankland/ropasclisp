<template lang="html">
  <div class="main-game">
    <div v-if="!user_hand">
      Please click a hand to play <br>
      <br>
    </div>
    <div v-if="!user_hand" v-for="(defeated_by, hand, index) in hands" @click="user_hand = hand">
      {{ hand }}
    </div>
    <div v-if="user_hand">
      You picked {{user_hand}}
    </div>
    <br>
    <button v-if="user_hand && !game_in_play" class="play-game" @click="play_game()">Play the Computer!</button>
    <div v-if="game_in_play">
      Computer picks... <span v-if="computer_hand">{{computer_hand}}</span>
      <br>
    </div>
    <div v-if="winning_hand">
      {{winning_hand}} <br>
      {{ this.winning_statement }}
    </div>
    <button v-if="winning_hand" class="play-again" @click="reset_game()">Play again?</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      hands: {
        Paper: ["Scissors", "cuts", "Lizard", "eats"],
        Rock: ["Paper", "covers", "Spock", "vaporizes"],
        Lizard: ["Rock", "crushes", "Scissors", "decapitates"],
        Spock: ["Lizard", "poisons", "Paper", "disproves"],
        Scissors: ["Spock", "smashes", "Rock", "crushes"]
      },
      user_hand: null,
      computer_hand: null,
      winning_hand: null,
      winning_verb: "",
      winning_statement: "",
      game_in_play: false
    };
  },
  methods: {
    reset_game() {
      this.user_hand = null;
      this.computer_hand = null;
      this.winning_hand = null;
      this.winning_verb = "";
      this.winning_statement = "";
      this.game_in_play = false;
    },
    play_game() {
      this.game_in_play = true;
      setTimeout(this.computer_picks, 2000);
      setTimeout(this.compute_winner, 3000);
    },
    computer_picks() {
      var keys = Object.keys(this.hands)
      // console.log(keys);
      // this.computer_hand = this.hands[keys[keys.length * Math.random() << 0]];
      this.computer_hand = keys[keys.length * Math.random() << 0];
    },
    compute_winner() {
      // console.log("user hand:", this.user_hand, this.hands[this.user_hand]);
      // console.log("computer hand:", this.computer_hand, this.hands[this.computer_hand]);
      if (this.user_hand === this.computer_hand) {
        this.winning_hand = "It's a DRAW!"
      };
      if (this.hands[this.user_hand].includes(this.computer_hand)) {
        this.winning_hand = "The COMPUTER wins!"
        this.winning_verb = this.hands[this.user_hand][this.hands[this.user_hand].indexOf(this.computer_hand) + 1];
        this.winning_statement = `${this.computer_hand} ${this.winning_verb} ${this.user_hand}!`
      };
      if (this.hands[this.computer_hand].includes(this.user_hand)) {
        this.winning_hand = "YOU won!"
        this.winning_verb = this.hands[this.computer_hand][this.hands[this.computer_hand].indexOf(this.user_hand) + 1];
        this.winning_statement = `${this.user_hand} ${this.winning_verb} ${this.computer_hand}!`
      };
    }
  }
}
</script>

<style lang="css" scoped>
</style>
