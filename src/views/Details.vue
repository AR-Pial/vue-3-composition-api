<template>
    <div>
        <div v-if="error" class="error">
            {{ error }}
        </div>
        <div v-if="post">
            <h1>{{ post.title }}</h1>
            <p>{{ post.body }}</p>
            <div class="tags">
                <span v-for="tag in post.tags" :key="tag">
                    #{{ tag }}
                </span>
            </div>
        </div>
    </div>
</template>

<script>
import getPost from '@/composables/getPost';

export default{
    props: ['id'],

    setup(props){
        const { post, error, load } = getPost(props.id);

        // Load the post when the component is created
        load();
        console.log(post);
        return { post, error };

    }
}
</script>

<style scoped>

</style>