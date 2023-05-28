<template>
    <div class="app">
        <form class="form" @submit.prevent>
            <h4>Create post</h4>
            <input
                    v-bind:value="title"
                    @input="title = $event.target.value"
                    class="form__input"
                    type="text"
                    placeholder="Title">
            <input
                    v-bind:value="description"
                    @input="description = $event.target.value"
                    class="form__input"
                    type="text"
                    placeholder="description">
            <button class="form__btn" @click="createPost">Add</button>
        </form>
        <div class="post" v-for="post in posts">
            <div class="post__title">{{ post.title }}</div>
            <div class="post__description">{{ post.description }}</div>
        </div>
    </div>

</template>

<script>
export default {
    data() {
        return {
            posts: [
                {
                    id: 1,
                    title: 'JS 1',
                    description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ad, aspernatur!'
                },
                {
                    id: 2,
                    title: 'JS 2',
                    description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ad, aspernatur!'
                },
                {
                    id: 3,
                    title: 'JS 3',
                    description: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ad, aspernatur!'
                },
            ],
            title: '',
            description: '',
        }
    },
    methods: {
        createPost() {
            const newPost = {
                id: Date.now(),
                title: this.title,
                description: this.description,
            }

            this.posts.push(newPost);
            this.title = '';
            this.description = '';
        },
    }
}
</script>

<style scoped>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.app {
    padding: 20px;
}

.post {
    border: 1px solid #c3c3c3;
    padding: 20px;
    margin-top: 20px;
}

.form {
    display: flex;
    flex-direction: column;
}

.form__input {
    width: 100%;
    border: 1px solid #c3c3c3;
    padding: 10px 15px;
    margin-top: 15px;
}

.form__btn {
    align-self: end;
    background: rebeccapurple;
    padding: 10px 25px;
    color: #fff;
    border: none;
    border-radius: 5px;
}

.form__btn:hover {
    cursor: pointer;
    opacity: 0.8;
}
</style>