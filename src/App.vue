<script setup>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import TodoBoard from './components/TodoBoard.vue'
</script>

<template>
  <div class="page">
    <Header />
    <main>
      <h2 class="title">TODO管理</h2>
      <TodoBoard />
    </main>
    <Footer />
  </div>
</template>

<style scoped>
.page {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}
main {
  flex: 1; /* この１行で下記３行を表す */
  /* flex-grow: 1;
  flex-shrink: 1;　 スペースが足りないなら、縮むことを許可する（true みたいなイメージの1）
  flex-basis: 0%; 余ったスペースを分配するときの、最初の基準サイズを0として考える*/
}
</style>
