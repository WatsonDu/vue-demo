<template>
  <div id="app">
    <Topbar class="topbar"/>
    <main>
    <Editor class="editor"/>
    <Preview class="preview"/>
    </main>
  </div>
</template>

<script>
import Editor from './components/Editor'
import Topbar from './components/Topbar'
import Preview from './components/Preview'
export default {
  components: {
  Topbar,Editor,Preview,
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.topbar{

}
main{
display:flex;
}
</style>
