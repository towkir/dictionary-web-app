<template>
  <div class="audio-and-control">
    <div
      class="big-button"
      :class="{playing : playing}"
      @click="playAudio"
    >
      <div class="play-icon"></div>
      <div class="pause-icon"></div>
    </div>
    <audio id="wordPlayer">
      <source :src="url">
    </audio>
  </div>
</template>

<script>
export default {
  props: {
    url: {
      type: String,
    }
  },
  data() {
    return {
      playing: false,
    }
  },
  methods: {
    stop() {
      this.playing = false;
    },
    playAudio() {
      const player = document.getElementById('wordPlayer');
      if (!this.playing) {
        player.play();
      } else {
        player.pause();
      } 
      this.playing = !this.palying;
    }
  },
  mounted() {
    document.getElementById('wordPlayer').addEventListener('ended', this.stop);
  }
};
</script>

<style>
.audio-and-control #player {
  display: none;
}

.audio-and-control .big-button {
  width: 75px;
  height: 75px;
  border-radius: 50%;
  background-color: var(--purple-alpha);
  transition: 0.3s ease-in-out;
  cursor: pointer;
  position: relative;
  user-select: none;
}

.audio-and-control .big-button:hover {
  background-color: var(--purple);
}

.audio-and-control .big-button .play-icon {
  position: absolute;
  left: 50%;
  top: 50%;
  width: 0;
  height: 0;
  border: 0 solid transparent;
  border-left-color: var(--purple);
  border-left-width: 21px;
  border-top-width: 10.5px;
  border-bottom-width: 10.5px;
  transform: translate(calc(-50% + 2px), -50%);
  transition: 0.3s ease-in-out;
}

.audio-and-control .big-button:hover .play-icon {
  border-left-color: var(--white);
}

.audio-and-control .big-button .pause-icon {
  position: absolute;
  left: 50%;
  top: 50%;
  width: 5px;
  height: 21px;
  border: 0 solid var(--purple);
  border-left-width: 8px;
  border-right-width: 8px;
  transform: translate(-50%, -50%);
  transition: 0.3s ease-in-out;
  display: none;
}

.audio-and-control .big-button:hover .pause-icon {
  border-color: var(--white);
}

.audio-and-control .big-button.playing .play-icon {
  display: none;
}

.audio-and-control .big-button.playing .pause-icon {
  display: block;
}

@media screen and (max-width: 570px) {
  .audio-and-control .big-button {
    width: 48px;
    height: 48px;
  }
  .audio-and-control .big-button .play-icon {
    border-left-width: 13px;
    border-top-width: 6.5px;
    border-bottom-width: 6.5px;
  }
  .audio-and-control .big-button .pause-icon {
    width: 3px;
    height: 13px;
    border-left-width: 5px;
    border-right-width: 5px;
  }
}
</style>