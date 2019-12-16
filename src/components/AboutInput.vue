<template>
  <div class="aboutInput">
    <input
    type="text"
    class="input"
    :value="value"
    v-on="listeners"
  >
  <i class="fab fa-vuejs"></i>
  <section>
    <b-field>
        <b-select placeholder="Country" icon="fa-vuejs" icon-pack="fab">
            <option value="1">Option 1</option>
            <option value="2">Option 2</option>
        </b-select>
    </b-field>
  </section>
  </div>
</template>

<script>
export default {
  name: "AboutInput",
  components: {
  },
  props: {
    value: {
      type: String,
      default: '',
    },
    value1: {
      type: String,
      default: 'fuck',
    }
  },
  computed: {
    listeners () {
      return {
        // Pass all component listeners directly to input
        ...this.$listeners,
        // Override input listener to work with v-model
        input: event => this.$emit('input', event.target.value)
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
