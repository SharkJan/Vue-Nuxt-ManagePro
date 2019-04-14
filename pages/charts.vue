<template>
  <div class='contentTrap'>
    <div
      v-for='(item, index) in imgs'
      :key='index'
    >
      <img
        :src='item'
        alt=""
        ref='imgKey'
      >
    </div>
  </div>

</template>
<script>
export default {
  data() {
    return {
      imgs: [
        "img/hk.jpeg",
        "img/hk.jpeg",
        "img/hk.jpeg",
        "img/hk.jpeg",
        "img/hk.jpeg",
        "img/hk.jpeg",
        "img/hk.jpeg",
        "img/hk.jpeg",
        "img/hk.jpeg",
        "img/hk.jpeg"
      ],
      isKey: false
    };
  },
  created() {
    this.init();
  },
  methods: {
    init() {
      var docHeight = document.documentElement.offsetHeight;
      console.log(docHeight);
      var imgHeight = this.$refs.imgKey;
      imgHeight.onclick = function(){
          alert(2233)
      }
    }
  }
};
</script>
<style>
.contentTrap {
  background: rgb(233, 230, 230);
  padding: 10px 10px;
  width: 94%;
  position: absolute;
  left: 70px;
  top: 70px;
}
img {
  width: 400px;
}
</style>
