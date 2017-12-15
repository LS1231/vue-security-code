<template>
  <div id="app">
    <h3>验证码输入组件</h3>
    <security-code class="security-code" v-model="code1"></security-code>
    <security-code class="security-code" v-model="code2" theme="line"></security-code>

    <security-code class="security-code" v-model="code3" placeholder="*"></security-code>
    <security-code class="security-code" v-model="code4" theme="line" placeholder="*"></security-code>

    <security-code class="security-code" v-model="code5" :number="6"></security-code>
    <security-code class="security-code" v-model="code6" theme="line" :number="6"></security-code>
  </div>
</template>

<script>
  import SecurityCode from '@/components/security-code'

  export default {
    name: 'app',
    data () {
      return {
        code1: '',
        code2: '',
        code3: '',
        code4: '',
        code5: '',
        code6: ''
      }
    },
    components: {
      SecurityCode
    }
  }
</script>

<style>
  * {
    text-decoration: none;
    -webkit-tap-highlight-color: transparent;
    outline: none;
    box-sizing: border-box;
  }

  html, body {
    width: 100%;
    height: 100%;
    padding: 0;
    margin: 0;
  }

  #app {
    width: 100%;
    height: 100%;
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
    background-color: #f7f7f7;
    padding-top: 50px;
  }

  .security-code {
    margin-bottom: 20px;
  }
</style>
