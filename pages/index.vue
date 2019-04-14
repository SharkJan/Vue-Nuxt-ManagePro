<template>
  <div class='contentTrap clearfix'>
    <div class='leftBox'>
      <div class='adminManage'>
        <div class='adminAvater clearfix'>
          <img
            src="../static/img/kudo.png"
            alt=""
            class='adminKudo'
          >
          <div class='tracyName superOver'>
            <div class='tracy'>Tracy</div>
            <div>超级管理员</div>
          </div>
        </div>
        <div class='loginTime'>
          <div class='address'>上次登录地点: <div class='rightAdd'>中国-上海</div>
          </div>
          <div class='addTime'>上次登录时间: <div class='rightTime'>2018-12-01</div>
          </div>
        </div>
      </div>
      <div class='bookProgress'>
        <div class='detail_text'>书籍详情</div>
        <div class='book_deatail'>
          <div class='book'>万历十五年</div>
          <b-progress
            :value="36"
            variant="warning"
            :striped="striped"
            class="mb-2 book1"
          >
          </b-progress>
          <div class='book'>月亮与六便士</div>
          <b-progress
            :value="68"
            variant="success"
            :striped="striped"
            class="mb-2 book1"
          >
          </b-progress>
          <div class='book'>雪人</div>
          <b-progress
            :value="52"
            variant="primary"
            :striped="striped"
            class="mb-2 book1"
          >
          </b-progress>
          <div class='book'>倒悬的地平线</div>
          <b-progress
            :value="86"
            variant="info"
            :striped="striped"
            class="mb-2 book1"
          >
          </b-progress>
        </div>
      </div>
    </div>

    <div class='rightBox'>
      <div class='userCount'>
        <div class='visitUsr'>
          <div class='avaterIcon'>
            <img
              src="../static/img/user.png"
              alt=""
              class='usrIcon'
            >
          </div>
          <div class='visitCount'>
            <div class='numZo'>1234</div>
            <div class='usrVi'>用户访问量</div>
          </div>
        </div>
        <div class='visitUsr'>
          <div class='avaterIcon bell'>
            <img
              src="../static/img/bell.png"
              alt=""
              class='usrIcon'
            >
          </div>
          <div class='visitCount'>
            <div class='numZo set'>666</div>
            <div class='usrVi'>系统消息</div>
          </div>
        </div>
        <div class='visitUsr'>
          <div class='avaterIcon car'>
            <img
              src="../static/img/car.png"
              alt=""
              class='usrIcon'
            >
          </div>
          <div class='visitCount'>
            <div class='numZo cou'>8000</div>
            <div class='usrVi'>数量</div>
          </div>
        </div>
      </div>
      <!-- 加载图片 -->
       <div class='loaddiv' v-show='!isLoad'>
          <img
            src="img/loading.png"
            alt=""
            class='loadimg'
          >
          <div class='loadtext'>正在加载...</div>
        </div>
      <div
        class='userList'
        v-show='isLoad'
      >
        <div class='titleRead'>
          <div class='waitRead' v-changel>待看书籍</div>
          <input
            v-model='booksRead'
            placeholder="请输入要看的书"
            class='readInput'
          >
          <div
            class='addBtn'
            @click='addLi'
          >添加</div>
          <div
            class='rmBtn'
            @click='allDel'
          >删除</div>
        </div>
        <div
          class='readContent'
          v-for='(item, index) in books'
          :key='index'
          :index='index'
        >
          <input
            type="checkbox"
            v-model='item.checked'
            @click='checkIn(index)'
          >
          <span
            v-text='item.text'
            :class='{line:item.status}'
          ></span>
          <img
            src="../static/img/del.png"
            alt=""
            class='delIcon'
            @click='books.splice(index, 1)'
          >
        </div>
      </div>
    </div>

  </div>

</template>
<script>
export default {
  data() {
    return {
      booksRead: "大国大城",
      books: [
        {
          id: 1,
          text: "Node.js实战",
          status: false,
          checked: false
        }
      ],
      isLoad: false
    };
  },
  created() {
    this.load();
  },
  directives: {
  changel: {
    // 指令的定义
    inserted: function (el) {
      el.onclick = function(){
        this.style.color = 'hotpink'
      }
    }
  }
},
  methods: {
    // 正在加载效果
    load() {
      setTimeout(() => {
        this.isLoad = true;
      }, 500);
    },
    // 增删改查
    addLi() {
      if (this.booksRead.trim() !== "") {
        this.books.push({
          id: this.books.id++,
          text: this.booksRead,
          status: false,
          checked: false
        });
        this.booksRead = "";
      }
    },
    checkIn(index) {
      this.books[index].status = !this.books[index].status;
      this.books[index].checked = !this.books[index].checked;
    },
    allDel() {
      var books = this.books;
      for (var i = 0; i < books.length; i++) {
        if (books[i].checked === true) {
          books.splice(i, 1);
          i--;
        }
      }
    }
  }
};
</script>
<style lang='scss'>
@import "../static/css/common";
.contentTrap {
  background: rgb(233, 230, 230);
  padding: 10px 10px;
  width: 94%;
  position: absolute;
  left: 70px;
  top: 70px;
}
.leftBox {
  width: 28%;
  height: 620px;
}
.adminManage {
  background: #fff;
  border-radius: 8px;
  padding: 20px 20px;
  margin-bottom: 15px;
  .adminKudo {
    width: 160px;
    height: 160px;
    border-radius: 50%;
    float: left;
  }
  .tracy {
    margin-bottom: 20px;
  }
  .tracyName {
    position: absolute;
    right: 20px;
    top: 25px;
    color: rgb(88, 86, 86);
  }
  .adminAvater {
    position: relative;
    border-bottom: 2px rgb(233, 230, 230) solid;
    height: 180px;
  }
  .loginTime {
    color: rgb(88, 86, 86);
    height: 40px;
    margin-top: 10px;
    position: relative;
  }
  .rightAdd {
    position: absolute;
    right: 20px;
    bottom: 14px;
  }
  .rightTime {
    position: absolute;
    right: 20px;
    bottom: -7px;
  }
}
// 加载图片
  .loadimg{
    width:80px;
  }
  .loaddiv{
    width: 100px;
    height:100px;
    position: absolute;
    right:360px;
    top:200px;
    z-index:999
  }
  .loadtext{
    color:#555;
    font-size:15px;
    margin:5px;
  }
.userCount {
  position: absolute;
  right: 0;
  top: 10px;
  width: 69%;
  height: 100px;
  margin-bottom: 15px;

  .visitUsr {
    width: 31%;
    height: 100px;
    margin-right: 15px;
    float: left;
    .avaterIcon {
      background: rgb(31, 116, 196);
      width: 40%;
      height: 100px;
      float: left;
      border-radius: 8px 0 0 8px;
    }
    .bell {
      background: rgb(219, 132, 33);
    }
    .car {
      background: rgb(14, 161, 112);
    }
  }
  .visitCount {
    width: 60%;
    height: 100px;
    background: #fff;
    float: left;
    border-radius: 0 8px 8px 0;
  }
  .usrIcon {
    width: 50px;
    height: 50px;
    margin: 20px auto;
    display: block;
  }
  .numZo {
    color: rgb(31, 116, 196);
    font-size: 30px;
    font-weight: 700;
    text-align: center;
    margin-top: 13px;
  }
  .usrVi {
    margin-bottom: 13px;
    color: #666;
    font-family: "微软雅黑";
    text-align: center;
  }
  .set {
    color: rgb(219, 132, 33);
  }
  .cou {
    color: rgb(14, 161, 112);
  }
}
.bookProgress {
  width: 100%;
  background: #fff;
  height: 330px;
  border-radius: 8px;
}
.detail_text {
  padding: 20px;
  border-bottom: 1px solid #cdcdcd;
}
.book_deatail {
  padding: 20px;
  .book {
    margin-bottom: 10px;
  }
}
// 待办事项
.userList {
  background: #fff;
  position: absolute;
  right: 32px;
  top: 120px;
  height: 504px;
  width: 67%;
  // min-width:60%;
  border-radius: 8px;
}
.readInput {
  height: 20px;
  font-size: 13px;
  float: left;
}
.titleRead {
  font-size: 14px;
  height: 50px;
  margin: 0 10px;
  padding: 15px 10px;
  position: relative;
  border-bottom: 1px solid #999;
  div {
    float: left;
  }
  .addBtn {
    color: red;
    position: absolute;
    right: 60px;
    top: 15px;
    cursor: pointer;
  }
  .rmBtn {
    color: #1f74c4;
    position: absolute;
    right: 25px;
    top: 15px;
    cursor: pointer;
  }
  .waitRead {
    margin-right: 10px;
    cursor: pointer;
  }
}
.readContent {
  font-size: 16px;
  height: 25px;
  margin: 0 10px;
  padding: 15px 10px;
  position: relative;
  span {
    margin-left: 10px;
  }
  .line {
    text-decoration: line-through;
  }
}
.delIcon {
  width: 18px;
  position: absolute;
  top: 15px;
  right: 30px;
  cursor: pointer;
}

// 媒体查询
@media screen and (max-width: 420px) {
  .contentTrap {
    float: left;
    width: 90%;
    padding: 10px;
    left: 40px;
    top: 50px;
  }
  .adminManage {
    height: 180px;
    width: 350px;
    padding: 10px 30px;
    font-size: 14px;
    .adminKudo {
      width: 90px;
      height: 90px;
      border-radius: 50%;
      float: left;
      margin-top: 10px;
    }
    .tracy {
      margin-bottom: 10px;
    }
    .tracyName {
      width: 90px;
      position: absolute;
      right: 10px;
      color: rgb(88, 86, 86);
    }
    .adminAvater {
      border-bottom: 1px rgb(233, 230, 230) solid;
      height: 120px;
    }
    .address {
      display: block;
    }
    .addTime {
      display: none;
    }
    .rightAdd {
      position: absolute;
      right: 30px;
      bottom: 19px;
    }
  }
  .rightBox {
    display: none;
  }
  .bookProgress {
    width: 350px;
  }
}
@media screen and (max-width: 380px) {
  .adminManage {
    width: 315px;
  }
  .bookProgress {
    width: 315px;
  }
}
@media screen and (max-width: 325px) {
  .adminManage {
    width: 265px;
  }
  .tracy {
    margin-bottom: 10px;
  }
  .adminManage .tracyName {
    width: 80px;
    position: absolute;
    right: 10px;
    color: rgb(88, 86, 86);
  }
  .adminManage .loginTime .address > div {
    margin-left: 20%;
  }
  .contentTrap {
    width: 88%;
    top: 40px;
  }
  .bookProgress {
    width: 265px;
  }
}
</style>
