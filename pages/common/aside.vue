<template>
  <!-- 侧边 -->
  <div class='aside'>
    <ul>
      <li>
        <router-link to="/">
          <img
            src="../../static/img/home.png"
            alt=""
          >
        </router-link>
      </li>
      <li>
        <router-link to="/books">
          <img
            src="../../static/img/form.png"
            alt=""
          >
        </router-link>
      </li>
    </ul>
  </div>
</template>
<script>
export default {

};
</script>
<style lang='scss'>
// aside

.aside {
  width: 70px;
  height:100%;
  background: rgb(50, 65, 87);
  img {
    width: 20px;
    height: 20px;
  }
  li {
    width: 70px;
    height: 70px;
    padding: 20px 25px;
  }
  li:hover {
    background: rgba(23, 30, 41, 0.8);
  }
}

/* 媒体查询 */
@media screen and (max-width: 420px) {
  // aside
  .aside{
    width:40px;
  }
  .aside li {
  width: 40px;
  height: 40px;
  padding: 6px 12px;
}
.aside li img {
  width: 15px;
  height: 15px;
}
}
</style>
