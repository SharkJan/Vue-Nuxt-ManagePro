<template>
  <div class='allBooks'>
    <div class='details'>
      <ul
        v-for='(book, index) in details'
        :key='index'
        :index='index'
      >
        <li>
          <img
            :src='book.src'
            alt=""
            class='book'
          >
          <div class='bookDtal'>
            <div class='name'>书名：{{book.name}}</div>
            <div class='score'>评分：{{book.score}}</div>
            <div class='price'>价格：{{book.price}}</div>
          </div>
        </li>
      </ul>
    </div>
    <div class='choice'>
      <button>筛选</button>
      <input
        type="text"
        placeholder="请输入想看书的评分"
        v-model='searchScore'
      >
      <p>{{type}}</p>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      // Books
      details: [],
      searchScore: 0,
      type: ""
    };
  },
  created(){
    this.$axios.get('/books').
      then(res => {
        this.details = res.data
      })
  },
  watch: {
    // 监听评分
    searchScore(newVal, oldVal) {
      console.log(newVal);
      if (newVal >= 8 && newVal < 9) {
        this.type = "经典作品";
      } else if (newVal >= 9) {
        this.type = "高分作品";
      } else if (newVal < 8) {
        this.type = "优秀作品";
      }
    }
  }
};
</script>
<style lang='scss'>
.allBooks {
  position: absolute;
  left: 80px;
  top: 80px;
}
.details {
  ul {
    float: left;
    margin-left: 30px;
  }
}
.book {
  height: 200px;
}
.bookDtal {
  margin-top: 10px;
  font-size: 14px;
  text-align: left;
}
.score {
  color: rgb(21, 172, 96);
}
.price {
  color: rgb(179, 154, 16);
}
.name {
  color: rgb(16, 87, 128);
}
.choice {
  button {
    width: 60px;
    height: 30px;
    background: rgb(35, 119, 168);
    border: none;
    border-radius: 4px;
    font-size: 15px;
    color: #fff;
    cursor: pointer;
    margin-top: 30px;
  }
  input {
    padding-left: 10px;
    margin-top: 30px;
  }
  p {
    margin-top: 10px;
  }
}
</style>
