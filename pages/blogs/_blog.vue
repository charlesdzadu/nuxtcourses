<template>
    <div>
         {{ path }} Je suis un post blog {{ slug }}
    </div>
</template>

<script>
export default {
    data(){
        return {
            slug: this.$route.params['blog'],
            path: this.$route.path
        }
    }
}
</script>