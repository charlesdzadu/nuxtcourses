<template>
    <div>
        <h1>Canvas dem0</h1>
        <canvas ref="canvas" id="drawing-pad" width="300" height="300">
            Un tableau de dessin ineractive
        </canvas>
        <div>
            <button @click="resetCanvas"> Reset Canvas</button>
            <button @click="saveImage"> Save Image</button>
            <button @click="replay"> Replay</button>
        </div>
        <hr>
        <img src="" alt="" ref="img" id="canvas-image">
        <small>Right Click to save image</small>
    </div>
</template>



<script>

export default {
    data(){
        return {
            canvas: null,
            context: null,
            isDrawing: false,
            startX: 0,
            startY: 0,
            points: [],
        }
    },
    methods:{
        resetCanvas(){},
        saveImage(){},
        replay(){},


        mousedown(e){
            var vm = this;
            var rect = vm.canvas.getBoundingClientRect();
            var x = e.clientX - rect.left;
            var y = e.clientY - rect.top;

            vm.isDrawing = true;
            vm.startX = x;
            vm.startY = y;
            vm.points.push({
                x: x,
                y:y
            });
        },

        mouvemove(e){
            var vm = this;
            var rect = vm.canvas.getBoundingClientRect();
            var x = e.clientX - rect.left;
            var y = e.clientY - rect.top;
            if(vm.isDrawing){
                
            }
        }
    },

    mounted(){
        var vm = this;
        vm.canvas = vm.$refs.canvas;
        vm.context = vm.canvas.getContext("2d");
        vm.canvas.addEventListener('mousedown', vm.mousedown);
        vm.canvas.addEventListener('mousemove', vm.mousemove);
        document.addEventListener('mouseup', vm.mouseup);
    }

}
</script>

<style>
canvas {
    border: 1px solid red;
    cursor: crosshair;
}

body{
    padding: 2em;
}
</style>