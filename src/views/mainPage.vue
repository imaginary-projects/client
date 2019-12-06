<template>

    <div class="mainPage">
        <navbar></navbar>
        <bodyContent></bodyContent>
        <detailContent></detailContent>
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
    }

}
</script>

<style>

</style>