<template>
    <div class="post">
        <router-link :to="{ name: 'Details', params: { id: post.id } }">
            <h3>{{ post.title }}</h3>
        </router-link>
        <p>{{ snippet }}</p>
        <span v-for="tag in post.tags" :key="tag">
            #{{ tag }}
        </span>
    </div>
</template>

<script>
import { computed } from 'vue';
export default{
    props: ['post'],
    setup(props){
        const snippet = computed(() =>{
            return props.post.body.substring(0, 100) + '...';	
        })

        return { snippet };
    }
}
</script>

<style scoped>
/* Single post card styles */
.post {
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.07);
  padding: 2rem;
  text-align: left;
  transition: box-shadow 0.2s;
}
.post:hover {
  box-shadow: 0 4px 16px rgba(0,0,0,0.13);
}
.post h3 {
  margin: 0 0 0.5rem 0;
  color: #0077cc;
  font-size: 1.5rem;
}
.post p {
  color: #444;
  margin-bottom: 1rem;
}
.post span {
  display: inline-block;
  background: #e3f2fd;
  color: #1976d2;
  border-radius: 6px;
  padding: 0.2em 0.7em;
  margin-right: 0.5em;
  font-size: 0.95em;
  margin-bottom: 0.3em;
}
</style>