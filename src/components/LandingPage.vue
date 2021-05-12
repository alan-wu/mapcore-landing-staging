<template>
  <el-container class="container">
    <el-header class="header" height="40px">List of staging demos</el-header>
    <el-main>
      <el-row>
        <el-col :span="6">
          <div class="text title">Title</div>
        </el-col>
        <el-col :span="14">
          <div class="text">Description</div>
        </el-col>
        <el-col :span="4">Link</el-col>
      </el-row>
      <el-row v-for="item in input" :key="item.title" class="row">
        <el-col :span="6">
          <div class="text title">{{ item.title }}</div>
        </el-col>
        <el-col :span="14">
          <div class="text">{{ item.description }}</div>
        </el-col>
        <el-col :span="4">
          <a :href="item.link">
            <el-button
              size="mini"
              round
              type="primary"
              icon="el-icon-caret-right"
            ></el-button>
          </a>
        </el-col>
      </el-row>
    </el-main>
  </el-container>
</template>

<script>
/* eslint-disable no-alert, no-console */
import Vue from "vue";
import { Button, Col, Container, Header, Icon, Main, Row } from "element-ui";
import lang from "element-ui/lib/locale/lang/en";
import locale from "element-ui/lib/locale";
locale.use(lang);
Vue.use(Button);
Vue.use(Col);
Vue.use(Container);
Vue.use(Header);
Vue.use(Icon);
Vue.use(Main);
Vue.use(Row);

export default {
  name: "LandingPage",
  methods: {
    onlinkClick: function(action) {
      this.$emit("onActionClick", action);
    }
  },
  props: {
    inputFile: {
      type: String,
      default: "index.json"
    }
  },
  data: function() {
    return {
      input: [
        { title: "MyTitle", description: "MyDescription", link: "./here" }
      ]
    };
  },
  created: function() {
    fetch(this.inputFile)
    .then(
      response => {
        if (response.status !== 200) {
          console.log('Encounter a problem: ' +
            response.status);
          return;
        }
        // Examine the text in the response
        response.json().then(data => {
          this.input = data;
        });
      }
    )
    .catch(err => {
      console.log('Fetch Error :-S', err);
    });
  }
};
</script>

<!-- Add "scop  height:40px; to this component only -->
<style scoped>
.container {
  text-align: justify;
  width: 100%;
  border-radius: 4px;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
  padding: 1em;
  background: #fff;
}

.row {
  padding-top: 30px;
}

.text {
  padding-top: 4px;
}

.title {
  font-weight: 700;
}

.header {
  font-size: 20px;
}
</style>
