    <template >
    <div class="">
        <router-link class="text-decoration-none" :to="'CategorieProduct/'+uuid">
            <div class="position-relative  m-0">
                <div class="position-absolute"
                    style="top: 0; bottom: 0; left: 0; right: 0; background: linear-gradient( rgba(255, 0, 0, 0.3), rgba(255, 0, 0, 0.3) );">
                 </div>
                <div class="">
                    <img class="shadow rounded"
                        src="https://images.pexels.com/photos/1483907/pexels-photo-1483907.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940"
                        alt="" width="100%" height="auto">
                </div>
                <div class="position-absolute" style="top: 0; bottom: 0; left: 0; right: 0; margin-top: 20px;">
                    <i class="ico text-white fas fa-bullhorn "></i>
                    <h2 class="text-white">{{name}}</h2>
                    <h6 class="text-white">12 listings</h6>
            </div>
            </div>
        </router-link>
    </div>
        
    </template>
    <script>
    export default {
        props: [
                'uuid',
                'name' 
        ]
    }
    </script>