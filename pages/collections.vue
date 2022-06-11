<template>
    <div>
        <h1>Collections</h1>
        <a @click="download"> Telecharger ce fichier </a>
    </div>
</template>

<script>
export default {
    layout: "InspireLayout",
    middleware: ["auth"],
    methods: {
        download() {
            var url = "https://images.pexels.com/photos/12250627/pexels-photo-12250627.jpeg";
            var filename = "Garçon d'afrique garçon.jpeg";
            console.log("runing")
            fetch(url)
                .then(response => response.blob())
                .then(blob => {
                    console.log("download ready")
                    const link = document.createElement("a");
                    link.href = URL.createObjectURL(blob);
                    link.download = filename;
                    link.click();
                })
                .catch(console.error);
        },
        downloadFile() {
            // Create a link and set the URL using `createObjectURL`
            const file = new File([`${new Date()}: Meow!`], 'my-cat.txt');
            const link = document.createElement('a');
            link.style.display = 'none';
            link.href = URL.createObjectURL(file);
            link.download = file.name;

            // It needs to be added to the DOM so it can be clicked
            document.body.appendChild(link);
            link.click();

            // To make this work on Firefox we need to wait
            // a little while before removing it.
            setTimeout(() => {
                URL.revokeObjectURL(link.href);
                link.parentNode.removeChild(link);
            }, 0);
        },
    }
}
</script>