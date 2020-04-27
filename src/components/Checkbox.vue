<template>
  <div class="checkbox">
    <div class="wrapper">
      <div
          class="icon"
          tabindex="1"
          @click="changeValue"
          @keyup.space="changeValue"
      >
        <font-awesome-icon
            size="1x"
            :style="{ color: disabled ? 'gray' : 'blue' }"
            :icon="checked ? 'check-square' : 'square'"
        />
      </div>

      <input
          tabindex="-1"
          type="checkbox"
          :id="name"
          :name="name"
          :disabled="disabled"
          :checked="checked"
          @change="changeValue"
      />
    </div>
    <label :for="name">
      <slot></slot>
    </label>
  </div>
</template>

<script>
export default {
    name: 'Checkbox',
    props: {
        checked: {
            type: Boolean,
            required: true
        },
        name: {
            type: String,
            required: true
        },
        change: {
            type: Function,
            required: true
        },
        disabled: {
            type: Boolean,
            required: false,
            default: false
        }
    },
    methods: {
        changeValue(){
            !this.disabled && this.change()
        }
    }
}
</script>

<style scoped src="./style.css">
</style>
