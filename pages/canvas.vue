<template>
    <div>
        <button @click="drawRect"> Créer un rectante</button>
        <canvas id="c"></canvas>
        <button @click="subWidth"> enlever </button>
        <button @click="addWidth"> Ajouter </button>
    </div>
</template>


<script>
export default {
    methods: {
        drawRect() {
            console.log("creation en cours");
            // clear canvas
            this.vueCanvas.clearRect(0, 0, 400, 200);

            // draw rect
            this.vueCanvas.beginPath();
            this.vueCanvas.rect(20, 20, this.rectWidth, 100);
            this.vueCanvas.stroke();
        },

        addWidth() {
            console.log("Ajout en cours");
            this.rectWidth += 10
            this.drawRect()
        },

        subWidth() {
            console.log("Enlever en cours");
            this.rectWidth -= 10
            this.drawRect()
        }
    },
    mounted() {
        console.log("mounted")
        var c = document.getElementById("c");
        var ctx = c.getContext("2d");
        this.vueCanvas = ctx;
        console.log("going")

    }
}
</script>