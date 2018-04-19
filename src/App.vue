<template>
  <div id="app">
    <div class="section">
      <img src="./assets/logo.png">
      <h1 v-html="msg"></h1>
      <p>Its purpose is to demonstrate how to use this loader and how to import components it builds.</p>
    </div>
    <div class="section">
      <h2>Main component, we'll use, is called <em>App</em>,</h2>
      <p>which is a <a target="_blank" href="https://vuejs.org/v2/guide/single-file-components.html">Vue single file
        component</a>.</p>
      <p>If you are reading this, it means <a target="_blank" href="https://vue-loader.vuejs.org/">vue-loader</a> and
        its
        <em>webpack</em> configuration works perfectly.</p>
      <p>Nothing extra ordinary happens here. Just usual <em>webpack</em> stuff.</p>
    </div>
    <separate-file-component></separate-file-component>
    <div class="section">
      <h2>Importing the separate files component</h2>
      <p>If you look closely to <em>App.vue</em> component, you'll notice that <em>SeparateFileComponent</em> is
        imported like:</p>
      <pre><code>import SeparateFileComponent from './SeparateFileComponent.vue';</code></pre>
      <p>That might confuse you, I agree.</p>
      <p class="em-par">"Hey, something fishy is happening here! <em>.vue</em> file <strong>is</strong> created, then
        deleted in some weird way."</p>
      <p>But don't be afraid. Nothing like that never happens. This line can also be written like this:</p>
      <pre><code>import SeparateFileComponent from './SeparateFileComponent.vue.js';</code></pre>
      <p>and still it will work perfectly.</p>
      <p>Because <em>webpack.config.js</em> configuration contains (not only):</p>
      <pre><code>resolve: {&#10;  extensions: ['.js']&#10;}</code></pre>
      <p>you're able to omit the <em>.js</em> extension.
        See <a target="_blank" href="https://webpack.js.org/configuration/resolve/#resolve-extensions">official
          docs</a>.<br>So some magic happens, but not on <em>vue-separate-files-webpack-loader</em>'s side.</p>
    </div>
    <div class="section">
      <h2>Little trick at the end</h2>
      <p>If you look even more closely to <em>webpack.config.js</em> configuration file,<br>especially at
        <em>resolve</em>
        part mentioned earlier, you'll notice that <em>extensions</em> property contains also <em>.vue.js</em>.</p>
      <p>This means, that you don't even need to use extension for importing component at all.</p>
      <p>Then you can do something like this:</p>
      <pre><code>import SeparateFileComponent from './SeparateFileComponent';</code></pre>
    </div>
    <div class="section inverted">
      <h2>That's it</h2>
      <p>I hope this example app shines more light on how to use this loader.</p>
    </div>
  </div>
</template>

<script>
  import SeparateFileComponent from './SeparateFileComponent.vue';

  export default {
    name: 'app',
    components: { SeparateFileComponent },
    data() {
      return {
        msg: 'Welcome to <em>vue-separate-files-webpack-loader</em> example app'
      }
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    padding: 1rem;
  }

  h1, h2 {
    font-weight: normal;
    margin: 1rem;
  }

  a {
    color: #42b983;
  }

  em {
    font-style: italic;
    color: #d14;
  }

  pre {
    padding: 1rem;
    overflow: auto;
    line-height: 1.45;
    background-color: #f6f8fa;
    border-radius: 3px;
    display: inline-block;
    text-align: left;
  }

  pre.inverted {
    background-color: #FFF;
  }

  pre code {
    display: inline;
    padding: 0;
    margin: 0;
    overflow: visible;
    word-wrap: normal;
    border: 0;
    font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, Courier, monospace;
    font-size: 100%;
    word-break: normal;
    white-space: pre;
    background: transparent;
  }

  .section {
    padding: 1.5rem;
  }

  .bg {
    background-color: #f6f8fa;
  }

  p {
    margin: 0;
    padding: 0;
  }

  p.em-par {
    margin: 1rem 0;
    padding: 0.2rem;
    display: inline-block;
    background-color: #bedb78;
  }
</style>
