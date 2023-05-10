<template>
  <div class="project">
    <div class="actions" @click="showDetails = !showDetails">
      <h3>{{ project.title }}</h3>

      <div class="icons">
        <span class="material-icons">edit</span>
        <span @click="deleteProject" class="material-icons">delete</span>
        <span class="material-icons">done</span>
      </div>
      
    </div>
    <div v-if="showDetails" class="details" > 
      <p>{{ project.details }}</p>
    </div>
   
    
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    project: Object
  }
,
data(){
  return {
    showDetails: false,
    uri: "http://localhost:3000/projects/" + this.project.id
  }
},

methods:{
  deleteProject(){
     fetch((this.uri, {method: "DELETE"}))
     .then(() => this.$emit('delete', this.project.id))
     .catch(err => err.message)
  }
}
  // const handleDelete=(id)=>{
  //   this.projects = this.projects.filter((project) => {
  //     return project.id = !id
  //   })
  // }

}


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.project {
  margin: 20px auto;
  background: white;
  padding: 10px 20px;
  border-radius: 4px;
  box-shadow: 1px 2px 3px rgba(0,0,0,0.05);
  border-left:6px solid tomato
}

h3 {
  cursor: pointer;
}

.actions {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.material-icons {
  font-size: 24px;
  margin-left: 10px;
  color: #bbb;
  cursor: pointer;
}
.material-icons:hover{
  color:#777;
  font-size: 27pxx;
}
</style>
