<template>
  <div class="hello">
        <b-menu>
          <b-menu-list v-for="device in deviceList" :key="device.name">
            <b-menu-item style="width:100%" :label="device.name" v-on:click="goToPage(device.device)"></b-menu-item>
          </b-menu-list>
        </b-menu>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "HelloWorld",
  props: {
    msg: String,
    selected: Object
  },
  data() {
    return {
      deviceList: [],
      device: "",
      host: window.location.protocol + "//" + window.location.hostname + ':8990/rcm/device_list.json'
    };
  },
  mounted: function () {
    this.getDeviceList();
  },
  methods: {
    getDeviceList() {
      let url = this.host;
      console.log(url);
      axios.get(url)
        .then(response => {
          this.deviceList = response.data;
        })
        .catch(error => {
          console.log(error)
        })
    },
    goToPage(device) {
      window.location.href = "./command-box.html?device=" + device;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
