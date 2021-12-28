<template>
  <button :class="`key ${clicked ? 'clicked' : ''}`" @click="play">
    {{ sound.letter }}
  </button>
</template>

<script>
export default {
  name: 'key',
  props: ['sound'],
  data() {
    return {
      clicked: false
    }
  },
  methods: {
    play() {
      this.clicked = true;
      new Audio(this.sound.audio).play();

      setTimeout(() => {
        this.clicked = false;
      }, 200);
    }
  },
  mounted() {
    document.addEventListener('keydown', e => {
      if (e.key.toLowerCase() === this.sound.letter.toLowerCase()) {
        this.play();
      }
    });
  }
}
</script>

<style>
  button {
    display: block;
    width: 100px;
    height: 100px;
    font-family: 'Poppins';
    font-size: 2.5rem;
    margin: 0 0.5rem;
    background: none;
    outline: none;
    border: solid 5px black;
    border-radius: 1.5rem;
    cursor: pointer;
    color: white;
    font-weight: 700;
    background-color: mediumaquamarine;
    transition: .4s;
  }

  button:hover {
    opacity: .7;
    transform: scale(.9);
  }

  button:active,
  button.clicked {
    transform: scale(1.1);
  }
</style>