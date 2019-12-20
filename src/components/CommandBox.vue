<template>
  <div class="hello">
        <textarea id="textarea_id" ng-model="commandString" style="height: 500px; width: 100%; resize: none; font-family: 'Courier New'; font-weight: bold;" disabled></textarea>
        <form style="margin-top: 10px;">
            <md-input-container style="width: 49%;">
                <label>Enter Command</label>
                <input ng-model="command" placeholder="Enter to commit command">
            </md-input-container>
            <md-input-container style="width: 49%;">
                <label>Enter Timeout Value</label>
                <input type="number" v-model="timeoutValue" placeholder="Enter to timeout value">
            </md-input-container>
            <md-button type="submit" name="submit" v-on:click="sendCommand(command)" style="width: 100%">Enter</md-button>
        </form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "CommandBox",
  props: {
    msg: String,
    selected: Object
  },
  data() {
    return {
      command: '',
      commandList: [],
      commandString: '',
      version: 0,
      timeoutValue: 1000,
      device: '',
      host: ''
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
      window.location.href = "./command?device=" + device;
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
