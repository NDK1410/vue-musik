<template>
  <div class="musik">
    <header>
      <h1>Musik</h1>
    </header>
    <main>
      <section class="player">
        <h2 class="song-title">{{ current.title }} - <span>{{ current.artist }}</span></h2>
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
  created () {
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
    this.player.play();
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
