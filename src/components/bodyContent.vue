<template>
  <b-card-group columns style="margin-left:10%; margin-right:10%;display:flex;flex-direction:column;align-items:center">

       
          <form style="width:99vw;margin-bottom:150px">
          <div class="form-row" style="padding-left:34%;padding-right:15%;height:300px;display:flex;align-items:center;box-shadow: 27px 46px 57px -8px rgba(0,0,0,0.2);">
            <div class="col-md-2 mb-3">
              <label for="validationTooltip01">Min price</label>
              <input v-model="minPrice" type="text" class="form-control" id="validationTooltip01" placeholder="1000" required>
              <div class="valid-tooltip">
                Looks good!
              </div>
            </div>
            <div class="col-md-2 mb-3">
              <label for="validationTooltip02">Max price</label>
              <input v-model="maxPrice" type="text" class="form-control" id="validationTooltip02" placeholder="1.000.000" required>
              <div class="valid-tooltip">
                Looks good!
              </div>
            </div>
              <div class="form-group col-md-3">
              <label for="inputState">Gender</label>
              <select v-model="sex" id="inputState" class="form-control">
                <option selected>Choose...</option>
                <option>Female</option>
                <option>Male</option>
              </select>
            </div>
            <!-- <div class="col-md-3 mb-3">
              <label for="validationTooltip01">Specific category</label>
              <input type="text" class="form-control" id="validationTooltip01" placeholder="Bulldog" required>
              <div class="valid-tooltip">
                Looks good!
              </div>
            </div> -->

            <button @click.prevent="showFilterred" style="height:40px; width:100px;margin-left:30px;" type="submit" class="btn btn-primary">Submit</button>
          </div>

          </form>
       
         <div style="margin-bottom:100px">
            <button type="button" class="btn btn-success" style="float:right; margin-left:5px;" @click="nextPage">Next</button>
            <button type="button" class="btn btn-success" style="float:right;" @click="prevPage">Previous</button>
          </div>
    
        <div class="dogs" style="display:flex;flex-basis: 30%;width:80vw;flex-wrap: wrap;">

            <div v-for="(dog, i) in currents" :key="i" class="card" style="width: 30%;margin:20px">
            <div class="images"

            :style="`height:300px;width:auto;background-image:url('${dog.image_url}'); background-size:cover`">
            </div>
            <div class="card-body" style="padding:40px;">
              <h4 class="card-title">{{dog.name}}</h4>
              <p class="card-text">{{dog.description.slice(0,50)}}</p>
              <a href="#" @click.prevent=showDetail(dog) class="btn btn-primary">detail</a>
              <button @click.prevent="deleteAnjing(dog._id)" type="submit" class="btn btn-warning"><i style="font-size:18px;margin-right:10px" class="fas fa-paw"></i>Delete</button>
            </div>
          </div>     

        </div>

  </b-card-group>
</template>

<script>
import axios from 'axios'
import Swal from 'sweetalert2'

export default {
   data() {
    return {
      minPrice:'',
      maxPrice:'',
      sex:'',
      input : '',
      searchBtn : '',
      dogList: [],
      isDetail:true,
      input : '',
      pageNumber: 0,
      size:6,
      currents : [],
    }
  },

  methods : {
    deleteAnjing(id){
      Swal.fire({
          title: 'Are you sure?',
          text: "You won't be able to revert this!",
          icon: 'warning',
          showCancelButton: true,
          confirmButtonColor: '#3085d6',
          cancelButtonColor: '#d33',
          confirmButtonText: 'Yes, delete it!'
        }).then((result) => {
          if (result.value) {
            axios({
                method:'delete',
                url: `http://localhost:3000/anjing/${id}`,
                headers : {
                  token : localStorage.getItem('token')
                }
              })
              .then(({data}) => {
                console.log(data)
                this.fetchData()
                  Swal.fire(
                      'Deleted!',
                      'Delete success',
                      'success'
                  )
              })
              .catch(({response}) => {
                  Swal.fire({
                      icon: 'error',
                      title: 'Oops...',
                      text: 'You are not the owner of the dog!',
                  })
                
                  console.log(response)
              })

            Swal.fire(
              'Deleted!',
              'Your dog removed from our page!',
              'success'
            )
          }
        })
      console.log(id)
      
      
    },
    showFilterred(){
      console.log('filter triggereddddd')
      axios({
        method:'post',
        url: 'http://localhost:3000/anjing/filter',
        data: {
          minPrice : this.minPrice,
          maxPrice : this.maxPrice,
          sex : this.sex
        }
      })
        .then(({data}) => {
          console.log(data,'dataa from anjing')
          console.log(this.pageNumber)
          this.dogList = data
          this.pageNumber = 0
          this.currentAnjing()
        })
        .catch((err) => {
          // console.log(err)
        })
    },
    showDetail(dog){
      this.$emit('show-detail',dog)
      this.$emit('detail-page',true)
      console.log('from show detail dog',dog)
    },
    expand(){
        searchBtn.classList.toggle("close");
        input.classList.toggle("square");
    },
    nextPage(){
       this.pageNumber++;
       this.currentAnjing()
    },
    currentAnjing(){
      // console.log('tajhdfnjkanflajsdbnfjlanfjlansdlf')
      const start = this.pageNumber * this.size
      const end = start + this.size;
      console.log(this.dogList)
      // console.log(this.dogList,'-------------------')
      // console.log(this.dogList.slice(start, end))
      this.currents = this.dogList.slice(start, end);

    },
    prevPage(){
      this.pageNumber--;
      this.currentAnjing()
    },
    fetchData(){
      axios({
        method:'get',
        url: 'http://localhost:3000/anjing'
      })
        .then(({data}) => {
          console.log(data)
          this.dogList = data
          this.currentAnjing()
        })
        .catch((err) => {
          console.log(err)
        })
    },
  },

  props : ['newAnjing'],

  created(){
    this.fetchData()
    
  },

  watch: {
    newAnjing(value){
      this.dogList.unshift(value)
      this.currentAnjing()
    }
  }



}
</script>

<style>

#bg {
  position: fixed; 
  top: 0; 
  left: 0; 
  background-size:cover;
}

@import url(https://fonts.googleapis.com/css?family=Open+Sans);

body{
  background: #f2f2f2;
  font-family: 'Open Sans', sans-serif;
}

.search {
  width: 100%;
  display: flex;
}

.searchTerm {
  width: 100%;
  border: 3px solid rgb(49, 49, 49);
  border-right: none;
  padding: 15px;
  height: 50px;
  border-radius: 5px 0 0 5px;
  outline: none;
  color: #9DBFAF;
}

.searchTerm:focus{
  color: rgb(34, 34, 34);
}

.searchButton {
  width: 50px;
  height: 50px;
  border: 1px solid rgb(63, 63, 63);
  background: rgb(71, 71, 71);
  text-align: center;
  color: #fff;
  border-radius: 0 5px 5px 0;
  cursor: pointer;
  font-size: 20px;
}

/*Resize the wrap to see the search bar change!*/
/* .wrap{
  width: 30%;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
} */

</style>