<!--四位验证码输入框组件-->
<template>
  <div class="security-code-wrap">
    <label :for="`code-${uuid}`">
      <ul :class="`${theme}-container`">
        <li class="field-wrap" v-for="(item, index) in number" :key="index">
          <i class="char-field">{{value[index] || placeholder}}</i>
        </li>
      </ul>
    </label>
    <input ref="input" class="input-code" @keyup="handleInput($event)" v-model="value"
           :id="`code-${uuid}`" :name="`code-${uuid}`" type="tel" :maxlength="number"
           autocorrect="off" autocomplete="off" autocapitalize="off">
  </div>
</template>

<script>
  export default {
    name: 'SecurityCode',
    // component properties
    props: {
      number: {
        type: Number,
        default: 4
      },
      placeholder: {
        type: String,
        default: '-'
      },
      theme: {
        type: String,
        default: 'block'
      }
    },
    // variables
    data () {
      return {
        value: ''
      }
    },
    computed: {
      uuid () {
        return Math.random().toString(36).substring(3, 8)
      }
    },
    methods: {
      hideKeyboard () {
        // 输入完成隐藏键盘
        document.activeElement.blur() // ios隐藏键盘
        this.$refs.input.blur() // android隐藏键盘
      },
      handleSubmit () {
        this.$emit('input', this.value)
      },
      handleInput (e) {
        this.$refs.input.value = this.value
        if (this.value.length >= this.number) {
          this.hideKeyboard()
        }
        this.handleSubmit()
      }
    }
  }
</script>

<style scoped lang="less">
  .security-code-wrap {
    overflow: hidden;
  }

  .block-container {
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
    .field-wrap {
      list-style: none;
      display: block;
      width: 40px;
      height: 40px;
      line-height: 40px;
      font-size: 16px;
      background-color: #fff;
      margin: 2px;
      color: #000;
      .char-field {
        font-style: normal;
      }
    }
  }

  .line-container {
    display: flex;
    position: relative;
    background-color: #fff;
    margin: 0;
    padding: 0;
    &:after {
      box-sizing: border-box;
      content: "";
      width: 200%;
      height: 200%;
      transform: scale(.5);
      position: absolute;
      border: 1px solid #d9d9d9;
      top: 0;
      left: 0;
      transform-origin: 0 0;
      border-radius: 4px;
    }
    .field-wrap {
      flex: 1;
      position: relative;
      display: block;
      height: 40px;
      width: 40px;
      line-height: 40px;
      font-size: 16px;
      &:not(:last-child):after {
        content: "";
        width: 1px;
        height: 50%;
        position: absolute;
        right: 0;
        top: 25%;
        background-color: #d9d9d9;
        transform: scaleX(.5);
      }
      .char-field {
        font-style: normal;
      }
    }
  }

  .input-code {
    position: absolute;
    left: -9999px;
    top: -99999px;
    width: 0;
    height: 0;
    opacity: 0;
    overflow: visible;
    z-index: -1;
  }

</style>
