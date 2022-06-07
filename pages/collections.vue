<template>
    <div>
        <div class=" animate-bounce p-6 max-w-sm mx-auto bg-white rounded-xl shadow-lg flex items-center space-x-4">
            <div class="shrink-0">
                <img class="h-12 w-12" src="/img/logo.svg" alt="ChitChat Logo">
            </div>
            <div>
                <div class="text-3xl font-medium text-black">ChitChat</div>
                <p class="text-slate-500">You have a new message!</p>
            </div>
        </div>
        <button class="bg-sky-600 hover:bg-sky-700">
            Save changes
        </button>
        <div>
            <article class="print:hidden">
                <h1>My Secret Pizza Recipe</h1>
                <p class="text-regal-blue font-bold">This recipe is a secret, and must not be shared with anyone</p>
                <!-- ... -->
            </article>
            <div class="hidden print:block">
                Are you seriously trying to print this? It's secret!
            </div>
        </div>
        <select>
            <option>Yes</option>
            <option>No</option>
            <option>Maybe</option>
        </select>
        <textarea name="" id="" cols="30" rows="10"></textarea>
        <article class="prose lg:prose-xl">
            ## Charles DZADU
        </article>
    </div>
</template>

<script>
</script>