<template>
  <div class="Container">
    <div class="header-text">
      <h1 style="color:rgb(222, 105, 105)">
        Find the
        <span style="color:rgb(152, 141, 87)">same fruit</span>
      </h1>
      <p
        style="color:rgb(137, 185, 101)"
      >After selecting one of the open cards, select the card that is off.</p>
    </div>

    <p>{{customCard.Id}}</p>
    <div>
      <transition-group appear name="rotate-all-closed-cards" class="game-cards">
        <app-game-card
          @click.native="SelectAnswer(card.Id, $event)"
          :class="{'shadow' : selectedCard == card.Id}"
          v-for="card in cardList"
          :key="card.Id"
          :card="card"
        ></app-game-card>
      </transition-group>
    </div>
    <div>
      <transition mode="out-in" name="rotate-answer">
        <app-custom-card v-if="!getAnswer" @click.native="ShowAnswer"></app-custom-card>
        <app-game-card
          :style="{'margin-left' : 'auto', 'margin-right' : 'auto'}"
          v-else
          :card="customCard"
        ></app-game-card>
      </transition>
    </div>
  </div>
</template>
<script>
import GameCard from "./GameCard";
import CustomCard from "./CustomCard";
export default {
  data() {
    return {
      cardList: [
        { Id: 1, Image: "../src/images/onion.png" },
        { Id: 2, Image: "../src/images/apple.png" },
        { Id: 3, Image: "../src/images/pear.png" },
        { Id: 4, Image: "../src/images/pumpkin.png" },
        { Id: 5, Image: "../src/images/watermelon.png" }
      ],
      selectedCard: -1,
      customCard: null,
      getAnswer: false
    };
  },
  components: {
    appGameCard: GameCard,
    appCustomCard: CustomCard
  },
  methods: {
    SelectAnswer(cardId) {
      this.selectedCard = cardId;
    },
    ShowAnswer() {
      if (this.selectedCard === -1) {
        alert("please select a card <3 ...");
        return;
      }
      this.getAnswer = true;

      setTimeout(() => {
        if (this.selectedCard === this.customCard["Id"])
          this.$emit("changeComponent", "AppClap");
        else
          this.$emit('changeComponent','AppMistake')
        }, 2000);
    }
  },
  created() {
    let index = Math.floor(Math.random() * this.cardList.length);
    this.customCard = this.cardList[index];
  }
};
</script>

<style>
.game-cards {
  margin-top: 20px;
  margin-bottom: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.game-card {
  width: 128px;
  height: 128px;
  margin-right: 10px;
  margin-left: 10px;
  border-radius: 5px;
  padding: 25px;
  cursor: pointer;
}
.game-cards > .game-card:hover {
  box-shadow: 3px 5px 7px 2px #524343;
}
.game-card > img {
  width: 100%;
  height: 100%;
}
.shadow {
  box-shadow: 2px 0px 20px 12px #ddd !important;
}
.rotate-all-closed-cards-enter-active {
  animation: rotate-closed-cards 2s ease-in-out;
}
.rotate-answer-enter-active {
  animation: answer-enter 1s ease-in-out;
}
.rotate-answer-leave-active {
  animation: answer-leave 1s ease-in-out;
}
@keyframes rotate-closed-cards {
  from {
    transform: rotateY(0deg);
  }
  to {
    transform: rotateY(720deg);
  }
}

@keyframes answer-enter {
  from {
    transform: rotateY(90deg);
  }
  to {
    transform: rotateY(0deg);
  }
}
@keyframes answer-leave {
  form {
    transform: rotateY(0);
  }
  to {
    transform: rotateY(90deg);
  }
}
</style>