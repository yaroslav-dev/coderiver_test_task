<template>
  <div class="container">
    <div class="page">
      <Header />
      <div class="cards">
        <template v-for="(idx, i) in cards">
          <CounterCard :key="i" :card="idx" />
        </template>
      </div>
      <div class="user-card">
        <div class="cover"></div>
        <div class="avatar-frame">
          <img class="avatar" src="../assets/avatar.png" alt="" />
        </div>
        <div class="user-name">{{ userData.name }}</div>
        <div class="user-phrase">{{ userData.company.catchPhrase }}</div>
        <div class="user-info-block">
          <div class="address">
            <div class="user-info-header">Address</div>
            <div class="user-info">{{ getAddress(userData.address) }}</div>
          </div>
          <div class="phone">
            <div class="user-info-header">Phone</div>
            <div class="user-info">{{ userData.phone }}</div>
          </div>
          <div class="website">
            <div class="user-info-header">Website</div>
            <div class="user-info">
              <a :href="userData.website">{{ userData.website }}</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "@/components/header.vue";
import CounterCard from "@/components/counterCard.vue";

export default {
  data() {
    return {
      userData: {
        id: 0,
        name: "",
        username: "",
        email: "",
        address: {
          street: "",
          suite: "",
          city: "",
          zipcode: "",
          geo: {
            lat: "",
            lng: "",
          },
        },
        phone: "",
        website: "",
        company: {
          name: "",
          catchPhrase: "",
          bs: "",
        },
      },
      cards: {
        active: {
          title: "Active",
          value: 60,
        },
        online: {
          title: "Online",
          value: 16,
        },
        filtered: {
          title: "Filtered",
          value: 43,
        },
        banned: {
          title: "Banned",
          value: 64,
        },
      },
    };
  },
  components: {
    Header,
    CounterCard,
  },
  mounted() {
    this.getUsers();
  },
  methods: {
    async getUsers() {
      let response = await fetch(
        "https://jsonplaceholder.typicode.com/users?_limit=8"
      );
      if (response.status == 200) {
        let userInfo;
        userInfo = await response.json();
        this.userData = userInfo.filter(
          (u) => u.id == this.$route.params.id
        )[0];
      } else {
        this.userData = null;
        console.warn(response.status);
      }
    },
    getAddress(address) {
      let res = [];
      Object.values(address).forEach((item) => {
        if (typeof item == "string") {
          res.push(item);
        }
      });
      return res.join(", ");
    },
  },
  computed: {},
};
</script>

<style lang="scss" scoped>
.container {
  width: 100%;
  margin-bottom: 296px;
  display: flex;
  flex-direction: column;
  // justify-content: center;
  align-items: center;
  .page {
    flex: 1;
    width: 1099px;
    .cards {
      display: flex;
      justify-content: stretch;
      margin: 0 2px 10px -1px;
    }
    .user-card {
      background-color: #fff;
      border: 1px solid #dfe0eb;
      border-radius: 0 0 8px 8px;
      display: flex;
      flex-direction: column;
      align-items: center;
      margin-right: 2px;
      padding-bottom: 106px;
      .cover {
        height: 230px;
        width: 100%;
        background-image: url("../assets/user_cover.png");
      }
      .avatar-frame {
        height: 155px;
        width: 155px;
        margin-top: -101px;
        margin-left: 54px;
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: #fff;
        border-radius: 50%;
        .avatar {
          height: 145px;
          width: 145px;
          border-radius: 50%;
        }
      }
      .user-name {
        margin-left: 45px;
        font-weight: 700;
        font-size: 36px;
        line-height: 45px;
        letter-spacing: 0.4px;
        color: #252733;
      }
      .user-phrase {
        margin-top: 5px;
        margin-left: 44px;
        margin-bottom: 50px;
        font-weight: 700;
        font-size: 24px;
        line-height: 30px;
        letter-spacing: 0.4px;
        color: #797a84;
      }
      .user-info-block {
        padding-top: 20px;
        align-self: flex-start;
        display: flex;
        flex-direction: column;
        .user-info-header {
          margin-left: 52px;
          margin-bottom: 15px;
          text-align: left;
          font-weight: 700;
          font-size: 36px;
          line-height: 45px;
          letter-spacing: 0.4px;
          color: #000000;
        }
        .user-info {
          width: 280px;
          margin-left: 52px;
          margin-bottom: 23px;
          text-align: left;
          font-weight: 500;
          font-size: 16px;
          line-height: 20px;
          letter-spacing: 0.4px;
          color: #000000;
        }
        .website {
          .user-info {
            text-decoration: underline;
          }
        }
      }
    }
  }
}
</style>