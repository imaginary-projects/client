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
                <b-nav-form>
                <b-form-input size="md" class="mr-sm-2" placeholder="email"></b-form-input>
                <b-form-input size="md" class="mr-sm-2" placeholder="password"></b-form-input>
                <b-button style="margin-right:10px;" size="md" class="my-2 my-sm-0" type="submit">login</b-button>
                <b-button size="md" class="my-2 my-sm-0" type="submit">register</b-button>
                <b-button style="margin-right:10px;" size="md" class="my-2 my-sm-0" type="submit">logout</b-button>
                <button type="submit" class="btn btn-primary" data-toggle="modal" data-target="#exampleModalCenter"><i style="font-size:18px;margin-right:10px" class="fas fa-plus-square"></i>Post</button>
                </b-nav-form>
            </b-navbar-nav>

            </b-collapse>
        </b-navbar>


        <!-- Modal -->
        <div class="modal fade" id="exampleModalCenter" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog modal-dialog-centered"  role="document">
            <div class="modal-content" style="width:1000px;padding:100px;border-radius:30px">
            <div>
                    <b-form @submit="onSubmit" @reset="onReset" v-if="show">
                    <b-form-group
                        id="input-group-1"
                        label="Email address:"
                        label-for="input-1"
                        description="We'll never share your email with anyone else."
                    >
                        <b-form-input
                        id="input-1"
                        v-model="form.email"
                        type="email"
                        required
                        placeholder="Enter Name"
                        ></b-form-input>
                    </b-form-group>

                    <b-form-group id="input-group-2" label="Your Name:" label-for="input-2">
                        <b-form-input
                        id="input-2"
                        v-model="form.name"
                        required
                        placeholder="Enter Type"
                        ></b-form-input>
                    </b-form-group>

                    <b-form-group id="input-group-2" label="Your Name:" label-for="input-2">
                        <b-form-input
                        id="input-2"
                        v-model="form.name"
                        required
                        placeholder="Enter Description"
                        ></b-form-input>
                    </b-form-group>

                    <b-form-group id="input-group-2" label="Your Name:" label-for="input-2">
                        <b-form-input
                        id="input-2"
                        v-model="form.name"
                        required
                        placeholder="Enter Price"
                        ></b-form-input>
                    </b-form-group>

                    <b-form-group id="input-group-3" label="Gender:" label-for="input-3">
                        <b-form-select
                        id="input-3"
                        v-model="form.food"
                        :options="Gender"
                        required
                        ></b-form-select>
                    </b-form-group>
                        <div class="mt-3">Selected file: {{ file ? file.name : '' }}</div>
                    <b-form-file
                        v-model="file"
                        :state="Boolean(file)"
                        placeholder="Choose a file or drop it here..."
                        drop-placeholder="Drop file here..."
                        ></b-form-file>

                    <b-form-group id="input-group-4">
                    </b-form-group>
                    <b-button type="submit" variant="primary">Submit</b-button>
                    </b-form>
                </div>
            </div>
        </div>
        </div>
    </div>
  
</template>

<script>
export default {
    data() {
      return {
        form: {
          email: '',
          name: '',
          Gender: null,
          checked: [],
          file: null,
        },
        Gender: [{ text: 'Select One', value: null }, 'male','female'],
        show: true
      }
    },
    methods: {
      onSubmit(evt) {
        evt.preventDefault()
        alert(JSON.stringify(this.form))
      },
      onReset(evt) {
        evt.preventDefault()
        this.form.email = ''
        this.form.name = ''
        this.form.food = null
        this.show = false
        this.$nextTick(() => {
          this.show = true
        })
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