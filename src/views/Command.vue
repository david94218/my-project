<template>
  <div class="command">
    <CommandBox/>
  </div>
</template>

<script>
// @ is an alias to /src
import CommandBox from "@/components/CommandBox.vue";

export default {
  name: "command",
  components: {
    CommandBox
  }
};
</script>
