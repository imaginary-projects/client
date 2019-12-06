<template>
  <b-card-group columns style="margin-left:10%; margin-right:10%;display:flex;flex-direction:column;align-items:center">

       
          <form style="width:99vw;margin-bottom:150px">
          <div class="form-row" style="padding-left:20%;padding-right:15%;height:300px;display:flex;align-items:center;box-shadow: 27px 46px 57px -8px rgba(0,0,0,0.2);">
            <div class="col-md-2 mb-3">
              <label for="validationTooltip01">Min price</label>
              <input type="text" class="form-control" id="validationTooltip01" placeholder="1000" required>
              <div class="valid-tooltip">
                Looks good!
              </div>
            </div>
            <div class="col-md-2 mb-3">
              <label for="validationTooltip02">Max price</label>
              <input type="text" class="form-control" id="validationTooltip02" placeholder="1.000.000" required>
              <div class="valid-tooltip">
                Looks good!
              </div>
            </div>
              <div class="form-group col-md-3">
              <label for="inputState">Sex</label>
              <select id="inputState" class="form-control">
                <option selected>Choose...</option>
                <option>Female</option>
                <option>Male</option>
              </select>
            </div>
            <div class="col-md-3 mb-3">
              <label for="validationTooltip01">Specific category</label>
              <input type="text" class="form-control" id="validationTooltip01" placeholder="Bulldog" required>
              <div class="valid-tooltip">
                Looks good!
              </div>
            </div>

            <button style="height:40px; width:100px;margin-left:30px;" type="submit" class="btn btn-primary">Submit</button>
          </div>

          </form>


       

        <div class="dogs" style="display:flex;flex-basis: 30%;width:80vw;flex-wrap: wrap;">
            <div class="card" style="width: 30%;margin:20px">
            <div class="images" style="height:300px;width:auto;background-image: url('https://www.rd.com/wp-content/uploads/2017/02/16-result-5-Which-Adorable-Puppy-Are-You-521697453-Bigandt_Photography-800x450.jpg'); background-size:cover">
            </div>
            <div class="card-body" style="padding:40px;">
              <h4 class="card-title">{{nama}}</h4>
              <p class="card-text">{{description}}</p>
              <a href="#" class="btn btn-primary">Details</a>
              <button type="submit" class="btn btn-primary"><i style="font-size:18px;margin-right:10px" class="fas fa-paw"></i>Favorite</button>
            </div>
          </div>


          <div class="card" style="width: 30%;margin:20px">
            <div class="images" style="height:300px;width:auto;background-image: url('https://www.rd.com/wp-content/uploads/2017/02/16-result-5-Which-Adorable-Puppy-Are-You-521697453-Bigandt_Photography-800x450.jpg'); background-size:cover">
<!--             <img src="../../dist/bookmark.png" style="height:90px;position:absolute;top:-20px;left:360px" alt="">
 -->            </div>
            <div class="card-body" style="padding:40px;">
              <h4 class="card-title">Annice The Cute Dog</h4>
              <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
              <a href="#" class="btn btn-primary">details</a>
              <button type="submit" class="btn btn-primary"><i style="font-size:18px;margin-right:10px" class="fas fa-paw"></i>Favorite</button>
            </div>
          </div>

          <!-- <div class="card" style="width: 30%;margin:20px">
            <div class="images" style="height:300px;width:auto;background-image: url('https://www.rd.com/wp-content/uploads/2017/02/16-result-5-Which-Adorable-Puppy-Are-You-521697453-Bigandt_Photography-800x450.jpg'); background-size:cover">
            <img src="../../dist/bookmark.png" style="height:90px;position:absolute;top:-20px;left:360px" alt="">
            </div>
            <div class="card-body" style="padding:40px;">
              <h4 class="card-title">Annice The Cute Dog</h4>
              <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
              <a href="#" class="btn btn-primary">details</a>
              <button type="submit" class="btn btn-primary"><i style="font-size:18px;margin-right:10px" class="fas fa-paw"></i>Favorite</button>
            </div>
          </div>

          <div class="card" style="width: 30%;margin:20px">
            <div class="images" style="height:300px;width:auto;background-image: url('https://cdn.pixabay.com/photo/2016/11/16/00/19/golden-retriever-1827899_960_720.jpg'); background-size:cover">
            
            </div>
            <div class="card-body" style="padding:40px;">
              <h4 class="card-title">Annice The Cute Dog</h4>
              <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
              <a href="#" class="btn btn-primary">details</a>
              <button type="submit" class="btn btn-primary"><i style="font-size:18px;margin-right:10px" class="fas fa-paw"></i>Favorite</button>
            </div>
          </div> -->

          

          

           

        </div>


        <!-- <div class="card" style="width: 100%;">
          <div class="images" style="height:300px;width:auto;background-image: url('https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSRFeGl-Nrqsd-HHLUaUyBaAQnogvf3tB3-OdT84eVDHTvhETP6&s'); background-size:cover">
          
          </div>
          <div class="card-body">
            <h5 class="card-title">Card title</h5>
            <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
            <a href="#" class="btn btn-primary">Go somewhere</a>
          </div>
        </div>

        <div class="card" style="width: 100%;">
          <div class="images" style="height:300px;width:auto;background-image: url('https://cdn.shopify.com/s/files/1/0812/3573/files/DogTraining_Website_Yellow_Dog.png?8767'); background-size:cover">
          
          </div>
          <div class="card-body">
            <h5 class="card-title">Card title</h5>
            <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
            <a href="#" class="btn btn-primary">Go somewhere</a>
          </div>
        </div> -->

        

  </b-card-group>
</template>

<script>
import axios from 'axios'
export default {
   data() {
    return {
      input : '',
      searchBtn : '',
      dogList: []
    }
  },

  methods : {
    expand(){
        searchBtn.classList.toggle("close");
        input.classList.toggle("square");
    },
    fetchData(){
      axios({
        method:'get',
        url: 'http://localhost:3000/anjing'
      })
        .then((data) => {
          dogList = data
          console.log(data)
        })
        .catch((err) => {
          console.log(err)
        })
    }
  },
  created(){
    this.fetchData()
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