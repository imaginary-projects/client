<template>

    <div class="mainPage">

        <navbar v-on:addAnjing="addAnjing"  ></navbar>

        <bodyContent v-on:show-detail="showDetail" :newAnjing="newAnjing" v-if="isDetailContent === false"></bodyContent>

        <detailContent :dog="detailDog" v-if="isDetailContent === true" @detail-page=detailPage></detailContent>

    </div>
</template>

<script>

import navbar from '../components/navbar'
import bodyContent from '../components/bodyContent'
import detailContent from '../components/detailContent'

export default {
    components : {
        navbar,
        bodyContent,
        detailContent
    },
    data() {
        return {
            
            isDetailContent : false,
            detailDog : '',
            newAnjing : ''
        }
  },
    methods : {
        showDetail(data){
            // $props['showDogDetail',data]
            this.isDetailContent = true
            this.detailDog = data
        },
        addAnjing(anjing){
            this.newAnjing = anjing
        },
        detailPage(value){
            console.log(value,'muncul gaaaa')
            this.isDetailContent = value
        }


  }

}
</script>

<style>

</style>