<script setup lang="ts">
type Props = {
  currentPosition?: number;
};

const { currentPosition = 0 } = defineProps<Props>();

const avatars = [
  { image: "adrieng.png", message: "Metz ça aurait été mieux." },
  { image: "alexandra.png", message: "On peut y aller en stop ?" },
  { image: "anthony.png", message: "Je veux aller faire pipi !!" },
  {
    image: "antoine.png",
    message: "Vous êtes sûrs que j'ai le droit de venir ?",
  },
  { image: "arnaud.png", message: "Y a Antoine qui m'embête." },
  { image: "benoit.png", message: "Vous êtes sûr qu'on va dans le bon sens ?" },
  { image: "caroline.png", message: "zu Hilfe !!" },
  { image: "cindy.png", message: "Je vais tous les doubler" },
  { image: "erwan.png", message: "Ils ont des murs d'escalade ?" },
  { image: "francois.jpg", message: "Un peu de calme derrière" },
  { image: "gildas.jpg", message: "J'ai des crampes." },
  { image: "guillaume.png", message: "C'est trop long." },
  { image: "guiom.png", message: "Vimenquonrive" },
  { image: "jeremie.jpg", message: "Je suis même pas là en vrai ..." },
  { image: "jibe.png", message: "On va où ?" },
  { image: "jonathan.png", message: "Youpi" },
  { image: "julio.jpg", message: "Quelqu'un a de quoi manger ?" },
  { image: "karen.jpg", message: "J'ai trop trop trop hâte <3 !!" },
  { image: "julienmaire.png", message: "zzzzzz" },
  { image: "thibault.png", message: "Y aura qui ?" },
  { image: "matthieu.png", message: "Mais qu'est-ce-que je fait là" },
];

const getRandomInt = (max: number) => {
  return Math.floor(Math.random() * max);
};

const choice = ref(getRandomInt(avatars.length));
const avatar = ref(avatars[choice.value].image);
const message = ref(avatars[choice.value].message);

const changingAvatar = () => {
  choice.value = getRandomInt(avatars.length);
  avatar.value = avatars[choice.value].image;
  message.value = avatars[choice.value].message;
  setTimeout(changingAvatar, 3000);
};

changingAvatar();
</script>

<template>
  <div class="bus" :style="`margin-left: calc(${currentPosition}% - 100px);`">
    <img alt="Bus" src="/assets/bus.png" />
    <div class="people">
      <img class="avatar" :alt="avatar" :src="`/avatars/${avatar}`" />
      <span>{{ message }}</span>
    </div>
  </div>
</template>

<style scoped>
.bus {
  position: absolute;
  margin-top: 0px;
  height: 100px;
  width: 200px;
}

@media (max-width: 1250px) {
  .bus {
    margin-top: 50px;
    width: 100px;
  }
}

.bus > img {
  width: 100%;
  animation-iteration-count: infinite;
  animation-duration: 0.5s;
  animation-name: oscillating;
}

@keyframes oscillating {
  0% {
    transform: rotate(3deg);
  }
  25% {
    transform: rotate(0deg);
  }
  50% {
    transform: rotate(-3deg);
  }
  75% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(3deg);
  }
}

.bus > .people {
  display: flex;
}

.bus:hover > .people {
  display: flex;
}

.people {
  background-color: white;
  border-radius: 20px;
  padding: 10px;
  font-weight: bold;
  width: 240px;
  margin-left: 0px;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

.people > span {
  min-width: 55%;
}

.people::before {
  content: "\A";
  border-style: solid;
  border-width: 0px 10px 15px 10px;
  border-color: transparent transparent white transparent;
  position: absolute;
  left: 125px;
  top: 97px;
}

.avatar {
  width: 50%;
  margin-bottom: -30px;
  border-radius: 50px;
  clip-path: polygon(100% 0%, 100% 70%, 0% 70%, 0% 0%);
  animation-iteration-count: infinite;
  animation-duration: 0.5s;
  animation-name: oscillating;
}
</style>
