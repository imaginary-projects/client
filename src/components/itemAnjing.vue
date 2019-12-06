<template>
    <div class="card" style="width: 30%;margin:20px">
        <div class="images" :style="`height:300px;width:auto;background-image: url('${anjing.image_url}'); background-size:cover`">
        </div>
        <div class="card-body" style="padding:40px;">
          <h4 class="card-title">{{anjing.name}}</h4>
          <p class="card-text">{{anjing.description}}</p>
          <a href="#" class="btn btn-primary">details</a>
        </div>
    </div>
</template>

<script>


export default {
    data(){
        return {
            
        }
    },
    props: ['anjing'],
    methods:{
      
    }
}
</script>