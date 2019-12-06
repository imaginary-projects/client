<template>
    <div style="display:flex;justify-content:center">
        <b-card no-body class="overflow-hidden" style="width: 75vw;height:90vh">
        <b-row no-gutters>
            <b-col md="6">
            <div class="images"
            :style="`height:100%;width:auto;background-position:center;background-image: url('${dog.image_url}'); background-size:cover`">
            </b-col>
            <b-col md="6" style="display:flex;justify-content:center;align-items:center;padding:50px">
            <b-card-body>
                <h1>{{dog.name}}</h1>
                <b-card-text>
                    {{dog.description}}
                </b-card-text>
                <br>
                <hr>
                <br>
                 <b-card-text style="display:flex; flex-direction:row">
                    <i style="font-size:24px;margin-right:20px;" class="fas fa-paw"></i>
                    <p>{{dog.type}}</p>
                </b-card-text>
                <b-card-text style="display:flex; flex-direction:row">
                    <i style="font-size:24px;margin-right:20px;" class="far fa-calendar-alt"></i>
                    <p>{{dog.age}}thn</p>
                </b-card-text>
                <b-card-text style="display:flex; flex-direction:row">
                    <i style="font-size:24px;margin-right:20px;" class="fas fa-venus-mars"></i>
                    <p>{{dog.sex}}</p>
                </b-card-text>
                <b-card-text style="display:flex; flex-direction:row">
                    <i style="font-size:24px;margin-right:20px;" class="fas fa-money-bill-wave"></i>
                    <p><p>{{dog.price}}</p>
                </b-card-text>
                <b-card-text style="display:flex; flex-direction:row">
                    <i style="font-size:24px;margin-right:20px;" class="far fa-envelope-open"></i>
                    <p>{{dog.userId.email}}</p>
                </b-card-text>
                <button type="submit" class="btn btn-primary" @click="backToPage" style="margin-top:50px">Back</button>
                <!-- <button :href=tweetUrl type="submit" class="btn btn-primary" style="margin-top:50px">Tweet</button> -->
                <a :href=tweetUrl class="btn btn-primary" style="margin-top:50px">Tweet</a>
            </b-card-body>
            </b-col>
        </b-row>
        </b-card>
    </div>
</template>

<script>

export default {
    data(){
        return {
            name: '',
            tweetUrl: '',
            picUrl: '',
            dogName : '',
            dogUrl : ''
        }
    },
    props : ['dog'],
    methods : {
        backToPage(){
            console.log('button triggered')
            this.$emit('detail-page',false)
        },
        generateUrl() {
            console.log(this.dog)
            // console.log('dari twit button')
            // console.log(dog.image_url)
            this.tweetUrl = `https://twitter.com/intent/tweet?text=Buruan%20beli%20${this.dog.name}%20click%20linknya%20sekarang!&url=${this.dog.image_url}`
      },
    },
    mounted(){
        this.generateUrl()
    },
    
}
</script>

<style>

</style>