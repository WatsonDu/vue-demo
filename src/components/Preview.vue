<template>
<div id = "preview">
<h1>{{resume.profile.name || ''}}</h1>
<p>{{resume.profile.birth || ''}} | {{resume.profile.city || ''}}</p>
<div v-if="filter(resume.workHistory).length > 0">
  <h2>工作经历</h2>
  <ol>
     <li v-for="work in filter(resume.workHistory)">
       {{work.company}}
       {{work.content}}
     </li>
  </ol>
</div>
<div v-if="filter(resume.studyHistory).length > 0">
  <h2>学习经历</h2>
  <ol>
     <li v-for="study in filter(resume.studyHistory)">
       {{study.school}}
       {{study.duration}}
       {{study.degree}}
     </li>
  </ol>
</div>
<div v-if="filter(resume.awards).length > 0">
  <h2>奖项</h2>
  <ol>
     <li v-for="award in filter(resume.awards)">
       {{award.name}}
     </li>
  </ol>
</div>
<div v-if="filter(resume.projects).length > 0">
  <h2>爱好</h2>
  <ol>
     <li v-for="project in filter(resume.projects)">
       {{project.name}}
       {{project.content}}
     </li>
  </ol>
</div>
<div>

{{resume.contacts.phone || ''}}
{{resume.contacts.wechat || ''}}
{{resume.contacts.email || ''}}
</div>
</div>
</template>
<script>
export default {
props:['resume'],
 methods:{
    filter(array){
      return array.filter(item=> !this.isEmpty(item))
   },
   isEmpty(object){
      let empty = true
      for (let key in object){
          if(object[key]){
             empty = false
             break
          }
      }
    return empty
   }
 }

}
</script>
<style>
#preview{
min-height:100px;
}
</style>
