<template>
  <div class="musik">
    <header>
      <h1>Musik</h1>
    </header>
    <main>
      <section class="player">
        <h2 class="song-title">{{ current.title }} - <span>{{ current.artist }}</span></h2>
        <div class="controls">
          <button class="prev" @click="prev">Prev</button>
          <button class="play" v-if="!isPlaying" @click="play">Play</button>
          <button class="pause" v-else @click="pause">Pause</button>
          <button class="next" @click="next">Next</button>
        </div>
      </section>
    </main>
  </div>
</template>

<script>
export default {
  name: 'Musik',
  data () {
    return {
      current: {},
      index: 0,
      isPlaying: true,
      songs: [
        {
          title: 'Bánh Mì Không',
          artist: 'Đạt G ft Du Uyên',
          src: require('../assets/Banh-Mi-Khong-Dat-G-DuUyen.mp3')
        },
        {
          title: 'Beautiful In White',
          artist: 'Shayne Ward',
          src: require('../assets/Beautiful-In-White-Shayne-Ward.mp3')
        },
        {
          title: 'The River',
          artist: 'Alex Johansson',
          src: require('../assets/The-River-Axel-Johansson.mp3')
        },
        {
          title: 'Chống Dịch Như Chống Giặc',
          artist: 'Ưng Đại Vệ',
          src: require('../assets/Chong-Dich-Nhu-Chong-Giac-Ung-Dai-Ve.mp3')
        },
        {
          title: 'Phía sau em',
          artist: 'Kay Trần ft Binz',
          src: require('../assets/Phia-Sau-Em-Kay-Tran-Binz.mp3')
        }
      ],
      player: new Audio()
    }
  },
  methods: {
    play (song) {
      if (typeof song.src != "undefined") {
        this.current = song;

        this.player.src = this.current.src;
      }

      this.player.play();
      this.isPlaying = true;
    },
    pause () {
      this.player.pause();
      this.isPlaying = false;
    },
    next () {
      this.index++;
      if (this.index > this.songs.length - 1) {
        this.index = 0;
      }

      this.current = this.songs[this.index];
      this.play(this.current);
    },
    prev () {
      this.index--;
      if (this.index < 0) {
        this.index = this.songs.length - 1;
      }

      this.current = this.songs[this.index];
      this.play(this.current);
    }
  },
  created () {
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  font-family: sans-serif;
}
header {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 15px;
  background-color: #212121;
  color: #FFF;
}
main {
  width: 100%;
  max-width: 768px;
  margin: 0 auto;
  padding: 25px;
}
</style>
