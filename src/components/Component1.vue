<script>
export default {};
</script>

<template>
  <div id="container">
    <div>
      <ul>
        <h3>關於我們</h3>
        <li><a href="brand.html">品牌故事</a></li>
      </ul>
    </div>
    <div>
      <ul>
        <a href="privacy.html"><h3>隱私權條款</h3></a>
      </ul>
    </div>
    <div>
      <ul>
        <h3>聯絡我們</h3>
        <li><a href="service.html">聯絡客服</a></li>
      </ul>
    </div>
  </div>
  <div>
    <p>COPYRIGHT@ WAV.ALL RIGHTS RESERVED.</p>
  </div>
</template>

<style scoped>
#container {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  background-color: grey;
  padding: 3em 0 17em;
}

#container li {
  list-style-type: none;
}
#container h3 {
  font-size: 1.5rem;
}
#container a {
  font-size: 1.2rem;
}
p {
  text-align: center;
  background-color: rgba(0, 0, 0, 0.911);
  color: white;
}
@media screen and (max-width: 1200px) {
  #container {
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 1.5em 0 8.5em;
  }
  #container h3 {
    font-size: 2.5rem;
    margin: 0.5em 0;
  }
  #container a {
    font-size: 1.8rem;
    padding-left: 0.3em;
  }
  #container ul {
    padding: 0;
  }
}
</style>
