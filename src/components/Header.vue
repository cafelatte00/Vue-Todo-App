<template>
  <header>
    <h1 class="logo">Todoリスト</h1>
    <nav>
      <ul class="global-nav">
        <li>HOME</li>
        <li>NEWS</li>
        <li>BLOG</li>
      </ul>
    </nav>
  </header>
</template>
<style scoped>
header {
  height: 40px;
  background-color: purple;
  color: white;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.global-nav {
  display: flex;
  justify-content: space-between;
}

.global-nav li {
  margin-right: 30px;
}
.logo {
  font-size: 20px;
  font-weight: normal;
}
</style>
