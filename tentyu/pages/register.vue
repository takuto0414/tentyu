<template>
  <div>
    <div class="register-all">
      <div v-show="!userConfirm">
        <div class="register-title">お客様情報登録</div>
        <v-card flat class="register--card">
          <div class="register-navi">
            メンテナンスにご加入のお客様は、<br />下記にてお客様情報、メンテナンスプランの登録をお願いします。
          </div>
          <div class="register-text">
            <ul class="register-list">
              <li>
                <v-text-field
                  v-model="user.storeName"
                  label="店舗名/会社名"
                  color="#0045AD"
                ></v-text-field>
              </li>
              <li>
                <v-text-field
                  v-model="user.phoneTel"
                  label="電話番号"
                  color="#0045AD"
                ></v-text-field>
              </li>
              <li>
                <v-text-field
                  v-model="user.name"
                  label="代表者名"
                  color="#0045AD"
                ></v-text-field>
              </li>
              <li>
                <v-text-field
                  v-model="user.kanaName"
                  label="かな"
                  color="#0045AD"
                ></v-text-field>
              </li>
              <li>
                <v-text-field
                  v-model="user.tel"
                  label="携帯電話"
                  color="#0045AD"
                ></v-text-field>
              </li>
              <li>
                <v-text-field
                  v-model="user.email"
                  label="メールアドレス"
                  color="#0045AD"
                ></v-text-field>
              </li>
              <li>
                <v-text-field
                  v-model="user.address"
                  label="住所"
                  color="#0045AD"
                ></v-text-field>
              </li>
              <li>
                <v-text-field
                  v-model="user.password"
                  label="パスワード"
                  color="#0045AD"
                ></v-text-field>
              </li>
            </ul>
          </div>
          <div class="register-card">
            <div class="register-prantitle">メンテナンスプラン</div>

            <div class="register-pran">
              <v-radio-group v-model="user.radios">
                <v-radio value="冷蔵庫プラン(厨房機器)">
                  <template v-slot:label>
                    <p class="register-pran-pran">冷蔵庫プラン(厨房機器)</p>
                  </template>
                </v-radio>
                <v-radio value="エアコンプラン">
                  <template v-slot:label>
                    <p class="register-pran-pran">エアコンプラン</p>
                  </template>
                </v-radio>
                <v-radio value="セットプラン">
                  <template v-slot:label>
                    <p class="register-pran-pran">セットプラン</p>
                  </template>
                </v-radio>
                <v-radio value="プロプラン">
                  <template v-slot:label>
                    <p class="register-pran-pran">プロプラン</p>
                  </template>
                </v-radio>
              </v-radio-group>
            </div>
          </div>
          <!-- <div class="register-bank"></div>
      <div class="card-label-container">
        <label for="card-number" data-tid="elements.form.card_number_label">
          カード番号
        </label>
      </div>
      <div id="card-number" class="input empty"></div>
      <div class="baseline"></div>
      <div class="card-label-container">
        <label for="card-expiry" data-tid="elements.form.card_expiry_label">
          有効期限
        </label>
      </div>
      <div id="card-expiry" class="input empty"></div>
      <div class="baseline"></div>
      <div class="card-label-container">
        <label for="card-cvc" data-tid="elements.form.card_cvc_label">
          セキュリティコード
        </label>
      </div>
      <div id="card-cvc" class="input empty"></div> -->

          <!-- for stripe -->
          <div class="container-">
            <stripe></stripe>
          </div>

          <div class="register-mko">
            <v-container fluid>
              <v-checkbox v-model="checkbox">
                <template v-slot:label>
                  <v-tooltip bottom>
                    <template v-slot:activator="{ on }">
                      <a target="_blank" @click.stop v-on="on">
                        <a target="_blank" href="/rule">利用規約</a>、<a
                          target="_blank"
                          href="/pri"
                          >プライバシーポリシー</a
                        >について同意する。
                      </a>
                    </template>
                    Opens in new window
                  </v-tooltip>
                </template>
              </v-checkbox>
            </v-container>
          </div>
          <div class="register-nji"></div>

          <div class="register-btn">
            <a @click="showConfirm">
              <v-btn class="mainte-btn-re" large depressed> 確認</v-btn></a
            >
          </div>
        </v-card>
      </div>
      <div v-show="userConfirm">
        <div class="form-ck">入力項目確認</div>

        <v-card class="register-card1" flat>
          <table class="table">
            <tbody>
              <tr>
                <td style="opacity: 0.6">店舗名/会社名</td>
                <td class="stcc-sub">{{ user.storeName }}</td>
              </tr>
              <tr>
                <td style="opacity: 0.6">電話番号</td>
                <td class="stcc-sub">{{ user.tel }}</td>
              </tr>
              <tr>
                <td style="opacity: 0.6">代表者名</td>
                <td class="stcc-sub">{{ user.name }}</td>
              </tr>
              <tr>
                <td style="opacity: 0.6">かな</td>
                <td class="stcc-sub">{{ user.kanaName }}</td>
              </tr>
              <tr>
                <td style="opacity: 0.6">携帯番号</td>
                <td class="stcc-sub">{{ user.phoneTel }}</td>
              </tr>
              <tr>
                <td style="opacity: 0.6">メールアドレス</td>
                <td class="stcc-sub">{{ user.email }}</td>
              </tr>
              <tr>
                <td style="opacity: 0.6">住所</td>
                <td class="stcc-sub">{{ user.address }}</td>
              </tr>
              <tr>
                <td style="opacity: 0.6">パスワード</td>
                <td class="stcc-sub">{{ user.password }}</td>
              </tr>
              <tr>
                <td style="opacity: 0.6">メンテナンスプラン</td>
                <td class="stcc-sub">{{ user.radios }}</td>
              </tr>
            </tbody>
          </table>
        </v-card>

        <v-btn
          class="mainte-btn-re"
          large
          depressed
          @click="userConfirm = false"
          >修正</v-btn
        >
        <v-btn class="mainte-btn-re" large depressed @click="submit"
          >送信</v-btn
        >
      </div>
    </div>
  </div>
</template>
<script>
import firebase from "~/plugins/firebase.js";
import axios from "axios";
export default {
  data() {
    return {
      userConfirm: false,
      user: {
        storeName: "",
        tel: "",
        name: "",
        kanaName: "",
        phoneTel: "",
        email: "",
        address: "",
        password: "",
        radios: ""
      },
      complete: false,
      number: false,
      expiry: false,
      cvc: false,
      checkbox: false,
      message: "",
      isEntered: false,
      isComplete: false
    };
  },
  methods: {
    showConfirm() {
      this.userConfirm = true;
    },
    showCardError(event) {
      if (event.error) {
        this.cardErrorMessage = event.error.message;
      } else {
        this.cardErrorMessage = "";
      }
    },
    submit() {
      // TODO 以下を参考にしつつ、paymentの実行をします
      // https://stripe.com/docs/payments/accept-a-payment
    },
    createUser() {
      console.log("createUser call");
      const db = firebase.firestore();
      db.collection("user")
        .add(this.user)
        .then(function(res) {
          console.log("user create success", res);
        })
        .catch(function(error) {
          console.log("error", error);
        });
    },
    register_success(res) {
      //this.dialog = true;
      console.log("sendSignInLinkToEmail ok");
      console.log(res);
      console.log(res.user);

      res.user
        .sendEmailVerification()
        .then(this.createUser)
        .catch(function(error) {
          console.log(error);
          // An error happened.
        });
    },
    submit() {
      console.log("submit call");
      firebase
        .auth()
        .createUserWithEmailAndPassword(this.user.email, this.user.password)
        .then(this.register_success)
        .catch(function(error) {
          console.log("error", error);
        });
      this.$router.push({ path: "/login-comp" });
    }
  },
  head() {
    return {
      title: this.title,
      script: [{ src: "//js.stripe.com/v3/" }]
    };
  }
};
</script>
<style>
li {
  list-style: none;
}
.mainte-btn-re {
  margin-top: 10px;
  margin-bottom: 12px;
  padding: 0px 12px;
  width: 80px !important;
  font-weight: bold;
  background-color: #0d47a1 !important;
  color: white !important;
}
.card-label-container {
  height: 1.5em;
  width: 100%;
  display: flex;
  margin: 10px 0;
  font-size: 0.8em;
  font-weight: 800;
  align-items: center;
}
.card-label-container ion-icon {
  font-size: 1.4em;
  margin: 0 6px;
}
.card-label-container label {
  pointer-events: none;
}
ion-row {
  margin: 10px 0;
}
.input {
  padding: 5px 0 6px 0;
  border-bottom: 1px solid #ddd;
}

.register-mko {
  text-align: left;
}

.span-title2 {
  text-align: left;
}
.register-card1 {
  margin: 0px 400px;
  padding: 16px;
}

.register-title {
  font-size: 30px;
  padding-top: 12px;
  font-weight: bold;
  padding-bottom: 12px;
  text-align: left;
  opacity: 0.8;
}

.register-pran {
  padding: 6px 0px;
}

.register-pran-pran {
  font-size: 18px;
  padding: 12px 0px 12px 12px;
}
.register-text {
  height: 650px;
}
.register-text ul li {
  padding-top: 10px;
  text-align: left;
  height: 70px;
  width: 100% !important;
}

.register-prantitle {
  font-size: 20px;
  font-weight: bold;
  text-align: left;
  opacity: 0.8;
}
.form-ck-li li {
  margin: 5px 5px;
  text-align: left;
  padding: 2px;
}

.form-ck {
  font-size: 30px;
  padding-top: 12px;
  padding-bottom: 12px;
  text-align: left;
  font-weight: bold;
  opacity: 0.8;
}

.register--card {
  padding: 16px;
  margin: 12px 6px;
}
.register-card1 {
  padding: 16px;
  margin: 12px 6px;
  text-align: left;
}

.register-navi {
  font-size: 18px !important;
  text-align: left;
  padding-bottom: 12px;
  padding-top: 12px;
  opacity: 0.6;
}
.register-mko a {
  font-size: 18px;
  padding: 12px 0px;
}
.v-icon {
  font-size: 16px !important;
}
.v-label {
  font-size: 16px !important;
}
.v-input {
  font-size: 16px !important;
}
.register-all {
  padding: 0px 50px;
}

@media (max-width: 480px) {
  .register-title {
    font-size: 20px;
    padding-bottom: 12px;
    text-align: left;
    opacity: 0.8;
  }
  .register-pran {
    padding: 6px 0px;
  }

  .register-pran-pran {
    font-size: 12px;
  }
  .register-text {
    padding-right: 50px;
    height: 400px;
  }

  .register-text ul li {
    height: 45px;
    width: 100% !important;
  }
  .register-prantitle {
    font-size: 18px;
    font-weight: bold;
    text-align: left;
    opacity: 0.8;
  }
  .form-ck {
    font-size: 20px;
    padding-top: 12px;
    padding-bottom: 12px;
    text-align: left;
    font-weight: bold;
    opacity: 0.8;
  }
  .register--card {
    padding: 16px !important;
    margin: 0px;
  }
  .register-card1 {
    padding: 16px;
    margin: 0px;
    font-size: 12px;
  }
  .register-navi {
    font-size: 12px !important;
    text-align: left;
    padding-bottom: 12px;
    opacity: 0.8;
  }
  .register-mko a {
    font-size: 12px;
  }
  .v-icon {
    font-size: 10px !important;
  }
  .v-label {
    font-size: 12px !important;
  }
  .v-input {
    font-size: 12px !important;
  }
  .register-all {
    padding: 0px 30px;
  }

  .container {
    padding: 0px;
  }
}
</style>
