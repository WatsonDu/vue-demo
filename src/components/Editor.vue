<template>
<div id = "editor">
<nav>
<ol>
<li v-for=" i in [0,1,2,3,4,5]"
    v-bind:class="{active:currentTab === i}"
    v-on:click="currentTab = i">
<svg class="icon" aria-hidden="true">
    <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
</svg>
</li>
</ol>
</nav>
<ol class="panes">
<li v-bind:class="{active:currentTab === 0}">
<ProfileEditor v-bind:profile="resume.profile"/>
</li>
<li v-bind:class="{active:currentTab === 1}">
<ArrayEditor v-bind:items="resume.workHistory" v-bind:labels="{company:'公司',content:'工作内容'}" v-bind:title="'工作经历'"/>
</li>
<li v-bind:class="{active:currentTab === 2}">
<ArrayEditor v-bind:items="resume.studyHistory" v-bind:labels="{school:'学校',duration:'学校时间',degree:'学位'}" v-bind:title="'学习经历'"/>
</li>
<li v-bind:class="{active:currentTab === 3}">
<ArrayEditor v-bind:items="resume.awards" v-bind:labels="{name:'奖项'}" v-bind:title="'获奖情况'"/>
</li>
<li v-bind:class="{active:currentTab === 4}">
<ArrayEditor v-bind:items="resume.projects" v-bind:labels="{name:'兴趣',content:'人生目标'}" v-bind:title="'个人兴趣'"/>
</li>

<li v-bind:class="{active:currentTab === 5}"><ContactsEditor v-bind:contacts="resume.contacts"/></li>
</ol>
</div>
</template>
<script>
 import ProfileEditor from './ProfileEditor'
 import ArrayEditor from './ArrayEditor'
 import ContactsEditor from './ContactsEditor'
  export default{
  components:{ ProfileEditor,ArrayEditor,ContactsEditor},
  props:['resume'],
      data(){
      return {
      currentTab:0,
      icons:['shenfenzhengzhengjian','wo','edu-line','huojiangzuopin','aihao','lianxidianhua'],
      }
      },
      methods:{
      },
      created(){}
      }
</script>
<style>
#editor{
min-height:100px;
display:flex;
}
nav{
background:black;
width:80px;
height:100%;
}
nav>ol>li{
padding:16px 0;
text-align:center;
}
li.active{
background:white;
}
li.active>.icon{
fill:black;
}
nav>ol>li>.icon{
width:24px;
height:24px;
fill:white;
}
.panes{flex:1;}
.panes>li{
   display:none;
   padding:32px;
   overflow:auto;
   height:100%;
}
.panes>li.active{display:block}
</style>
