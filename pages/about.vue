<template>
    <div>
        je suis about {{ title }}
    </div>
</template>

<script>
export default {
    data() {
        return {
            title: "A Propos 2"
        }
    },
    asyncData() {
        return {
            title1: "A Propos 1"
        }
    },
    head() {
        return {
            title: "A Propos",
            meta: [
                {hid: "description", name: "description", content: "Ma page a propos rasta"}
            ],
            script: [
                {
                    src: '/about.js'
                }
            ]
        }
    }
}
</script>