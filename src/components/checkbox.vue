<template>
  <label class="checkbox">
    <span class="checkbox-input">
      <span
        class="checkbox-inner"
        :class="{
          'disabled': disabled,
          'checked': checked,
          'focus': focus
        }"
      ></span>
      <input
        class="checkbox-original"
        type="checkbox"
        :disabled="disabled"
        :name="name"
        v-model="model"
        @change="$emit('change', $event)"
        @focus="focus = true"
        @blur="focus = false">
    </span>
    <span class="checkbox-label" v-if="label">
     {{ text }}
    </span>
  </label>
</template>
<script>
  export default {
    name: 'VueCheckbox3',
    props: {
      value: {},
      label: {},
      disabled: Boolean,
      checked: Boolean,
      name: String
    },
    data() {
      return {
        focus: false
      };
    },
    computed: {
      text() {
        if (typeof this.label === 'string') {
          return this.label;
        }
        if (typeof this.label === 'object') {
          return this.model ? this.label.yes : this.label.no;
        }
      },
      checked() {
        return this.model;
      },
      model: {
        get() {
          return this.value;
        },
        set(val) {
          console.log(val);
          this.$emit('input', val);
        }
      }
    }
  };
</script>

<style lang="scss">
  .checkbox, .checkbox-input {
    white-space: nowrap;
    cursor: pointer
  }

  .checkbox, .checkbox-inner, .checkbox-input {
    display: inline-block;
    position: relative
  }

  .checkbox {
    color: #1f2d3d;
    -moz-user-select: none;
    -webkit-user-select: none;
    -ms-user-select: none
  }

  .checkbox + .checkbox {
    margin-left: 15px
  }

  .checkbox-input {
    outline: 0;
    line-height: 1;
    vertical-align: middle
  }

  .checkbox-inner {
    border: 1px solid #ccc;
    box-shadow: 0 1px 1px rgba(0, 0, 0, 0.075) inset;
    border-radius: 4px;
    box-sizing: border-box;
    width: 20px;
    height: 20px;
    background-color: #fff;
    z-index: 1;
    transition: border-color .25s cubic-bezier(.71, -.46, .29, 1.46), background-color .25s cubic-bezier(.71, -.46, .29, 1.46)
  }

  .checkbox-inner:not(.disabled):hover {
    border-color: #FF9901
  }

  .checkbox-inner::after {
    box-sizing: content-box;
    content: "";
    border: 2px solid #fff;
    border-left: 0;
    border-top: 0;
    width: 4px;
    height: 5px;
    left: 6px;
    position: absolute;
    top: 5px;
    -ms-transform: rotate(45deg) scaleY(0);
    transform: rotate(45deg) scaleY(0);

    transition: transform .15s cubic-bezier(.71, -.100, .88, .6) .05s;
    -ms-transform-origin: center;
    transform-origin: center
  }

  .checkbox-inner.disabled.checked {
    background-color: #D3DCE6;
    border-color: #D3DCE6;
  }

  .checkbox-inner.disabled.checked::after {
    border-color: #fff;
  }

  .checkbox-inner.disabled {
    background-color: #D3DCE6;
    border-color: #D3DCE6;
  }

  .checkbox-inner.disabled {
    border-color: #fff;
  }

  .checkbox-inner.focus {
    border-color: #FF9901;
    box-shadow: 0 1px 1px rgba(0, 0, 0, 0.075) inset, 0 0 8px rgba(255, 153, 1, 0.6);
  }

  .checkbox-inner.checked {
    background-color: #FF9901;
    border-color: #FF9901;
  }

  .checkbox-inner.checked::after {
    -ms-transform: rotate(45deg) scaleY(1);
    transform: rotate(45deg) scaleY(1)
  }

  .checkbox-inner.disabled {
    background-color: #EFF2F7;
    border-color: #D3DCE6;
    cursor: not-allowed
  }

  .checkbox-inner.disabled::after {
    cursor: not-allowed;
    border-color: #EFF2F7
  }

  .checkbox-inner.disabled + .checkbox-label {
    cursor: not-allowed
  }

  .checkbox-original {
    opacity: 0;
    outline: 0;
    position: absolute;
    margin: 0;
    left: -999px
  }

  .checkbox-label {
    font-size: 14px;
    padding-left: 5px
  }
</style>
