<template>

    <div>
        <b-navbar class="navbar" toggleable="md" type="dark" style="padding-right:100px;padding-left:100px;padding-top:200px" >
            <b-navbar-brand href="#">Doggy Style</b-navbar-brand>

            <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

            <b-collapse id="nav-collapse" is-nav >
            <b-navbar-nav>
                <!-- <b-nav-item style="color: rgba(2, 2, 2, 0.5);" href="#">Link</b-nav-item> -->
                <a style="color:grey;font-size:26px; margin-right:50px" class="navbar-brand" href="#">Home</a>
                <a style="color:grey;font-size:26px" class="navbar-brand" href="#">Favorites</a>

            </b-navbar-nav>

            <!-- Right aligned nav items -->
            <b-navbar-nav class="ml-auto">
                <b-nav-form @submit.prevent="login">
                <b-form-input v-if="isLogin === false && isRegister === true" v-model="username" size="md" class="mr-sm-2" placeholder="username"></b-form-input>
                <b-form-input v-if="isLogin === false" v-model="email" size="md" class="mr-sm-2" placeholder="email"></b-form-input>
                <b-form-input v-if="isLogin === false" v-model="password" size="md" type="password" class="mr-sm-2" placeholder="password"></b-form-input>
                <b-button v-if="isLogin == false && isRegister === false"  style="margin-right:10px;" size="md" class="my-2 my-sm-0" type="submit">login</b-button>
                <b-button v-if="isLogin == false && isRegister === false" @click.prevent="registerPage" size="md" class="my-2 my-sm-0" type="submit">register</b-button>
                <b-button v-if="isRegister == true && isLogin == false" size="md" @click.prevent="register" style="margin-right:10px;" class="my-2 my-sm-0" type="submit">submit</b-button>
                <b-button  v-if="isRegister === true && isLogin == false" @click.prevent="back" size="md" class="my-2 my-sm-0" type="submit">back</b-button>
                <button v-if="isLogin == true" type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModalCenter"><i style="font-size:18px;margin-right:10px" class="fas fa-plus-square">
                post
                </button>
                <b-button v-if="isLogin == true" style="margin-left:10px;" size="md" class="my-2 my-sm-0" @click="logout">logout</b-button>
                </b-nav-form>
            </b-navbar-nav>

            </b-collapse>
        </b-navbar>

        <!-- Modal -->
        <div class="modal fade" id="exampleModalCenter" tabindex="-1" role="dialog" aria-labelledby="exampleModalCenterTitle" aria-hidden="true">
        <div class="modal-dialog modal-dialog-centered" role="document">
                <div class="modal-content" style="width:1000px;padding:100px;border-radius:30px">
            <div>
                    <b-form @submit.prevent="onSubmit" v-if="show">
                    <div class="form-group">
                        <label for="exampleInputEmail1">Name</label>
                        <input v-model="name" type="text" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="name">
                    </div>

                    <div class="form-group">
                        <label for="exampleInputEmail1">Description</label>
                        <input v-model="description" type="text" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="description">
                    </div>

                     <div class="form-group">
                        <label for="exampleInputEmail1">Type</label>
                        <input v-model="type" type="text" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="type">
                    </div>

                     <div class="form-group">
                        <label for="exampleInputEmail1">Age</label>
                        <input v-model="age" type="text" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="age">
                    </div>

                    <div class="form-group">
                        <label for="exampleInputEmail1">Price</label>
                        <input v-model="price" type="text" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="price">
                    </div>

                     <div class="form-group">
                        <label for="exampleFormControlSelect1">Gender</label>
                        <select v-model="gender" class="form-control" id="exampleFormControlSelect1">
                        <option>Male</option>
                        <option>Female</option>
                        </select>
                    </div>

                    <b-form-file
                        v-model="file"
                        :state="Boolean(file)"
                        placeholder="Choose a file or drop it here..."
                        drop-placeholder="Drop file here..."
                        ></b-form-file>
                        <div class="mt-3">Selected file: {{ file ? file.name : '' }}</div>

    
                    <b-button type="submit" variant="primary">Submit</b-button>
                    </b-form>
                </div>
            </div>
        </div>
        </div>
    </div>
  
</template>

<script>

import axios from 'axios'
import Swal from 'sweetalert2'

export default {
    data() {
      return {
            username:'',
            email:'',
            password :'',
            name: '',
            description: '',
            type: '',
            age:'',
            gender: '',
            price: '',
            file:[],
            show: true,
            isLogin : true,
            isRegister : false,
            anjings : []
      }
    },
    methods: {
        registerPage(){
            this.isRegister = true
        },
        back(){
            this.isRegister = false
        },
        login(){
            axios({
                url : "http://localhost:3000/users/login",
                method : 'post',
                data : {
                    email : this.email,
                    password : this.password,
                }
            })
            .then(({data}) => {
                this.isLogin = true
                localStorage.setItem('token', data.access_token)
                Swal.fire(
                    'Good job!',
                    'You clicked the button!',
                    'success'
                )
            })
            .catch(({response}) => {
                Swal.fire({
                    icon: 'error',
                    title: 'Oops...',
                    text: 'Something went wrong!',
                    footer: '<a href>Why do I have this issue?</a>'
                })
             
                console.log(response)
            })
        },
        register(){
            axios({
                url : "http://localhost:3000/users/register",
                method : 'post',
                data : {
                    username : this.username,
                    email : this.email,
                    password : this.password,
                }
            })
            .then(({data}) => {
                this.isLogin = true
                localStorage.setItem('token', data.access_token)
                console.log(data)
                Swal.fire(
                    'Good job!',
                    'You clicked the button!',
                    'success'
                )
            })
            .catch(({response}) => {
                Swal.fire({
                    icon: 'error',
                    title: 'Oops...',
                    text: 'Something went wrong!',
                    footer: '<a href>Why do I have this issue?</a>'
                })
                console.log(response)
            })
        },
        logout(){
            localStorage.removeItem('token')
            this.isLogin = false

        },
        onSubmit() {
            const fd = new FormData()
            fd.append('file',this.file)
            fd.append('name',this.name)
            fd.append('description',this.description)
            fd.append('gender',this.gender)
            fd.append('price',this.price)
            fd.append('type',this.type)
            fd.append('age',this.age)
            
            axios({
                url : "http://localhost:3000/anjing/create",
                method : 'post',
                data : fd,
                headers : {
                    token : localStorage.getItem('token')
                }
            })
            .then(({data}) => {
                $('#exampleModalCenter').modal('hide')
                Swal.fire(
                    'Good job!',
                    'You clicked the button!',
                    'success'
                )
                this.$emit('addAnjing',data)
                console.log(data)
            })
            .catch(err => {
                console.log(err)
            })
        // alert(JSON.stringify(this.form))
      },
      
    },
    created(){
        if(localStorage.getItem('token')){
            
            this.isLogin = true
        }else{
            
            this.isLogin = false
        }
    }
  }
</script>

<style> 
    .navbar {
        background:url('../../dist/doggylovers.jpg');
        background-size:cover;
        background-size: 1300px;
        background-position:bottom;
        background-repeat: no-repeat;
        height:600px;
        width:auto;
        background-color: white
    }
        navbar-dark .navbar-nav .nav-link {
        color: rgba(2, 2, 2, 0.5);
}


</style>