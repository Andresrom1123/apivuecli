<template>
    <div>
       <div class=" border-top-0 shadow">
            <div class="scroll" style="overflow: auto;  height: 200px" >
                <a class="text-decoration-none" :href="'../Product-page/'+uuid">
                    <img  class="" :src="image" width="100%"><img>
                </a>    
            </div>
                <h5 class="pl-3 pt-2">{{ name }}</h5>
            <div class="mb-4 scroll" style="height: 160px; overflow: auto;">
                <p class="mt-3  pl-3 pr-3">{{ description }}</p>
            </div>
            <div class="mr-3 ml-3 pb-4">
                <a class="text-decoration-none" target="_blank" :href="url">
                    <button type="button" class="btn btn-outline-secondary btn-block text-dark border-secondary">
                        Ver la web</button>
                </a>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    props: [
        'uuid', 
        'image',
        'name',
        'description',
        'url'
    ]
}
</script>