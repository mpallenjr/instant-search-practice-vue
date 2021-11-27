<template>

<div id="app-instasearch">
  <h1> Photo finder</h1>
  <div id="app-instasearch">
    <div class="input-container">
      <input type="text" placeholder="Type a name" v-model="authorNameSearchString" />
    </div>
    <ul>
      <li class="photo" v-for="photo in filteredPhotoFeed" v-bind:key="photo.id">
        <img v-bind:src="photo.download_url" />
        <span class="author">{{ photo.author }} </span>
        </li>
    </ul>
  </div>
</div>

</template>

<script>
import axios from 'axios';
export default {

data: function() {
  return { 
		authorNameSearchString: "",
		photoFeed: null
	};
},
mounted() {
  axios.get('https://picsum.photos/v2/list?page=2&limit=10').then(response => {
      this.photoFeed = response.data;
    })
    .catch(error => console.log(error))
},
computed: {

  filteredPhotoFeed: function () {

    var photos = this.photoFeed;
    var authorNameSearchString = this.authorNameSearchString;

    if(!authorNameSearchString){
      return photos;
    }

    searchString = authorNameSearchString.trim().toLowerCase();

    photos = photos.filter(function(item){
      if(item.author.toLowerCase().indexOf(authorNameSearchString) !== -1){
        return item;
      }
    })

    return photos;
  }
},

}

</script>

<style>
.photo {
	list-style: none;
	display: grid;
	grid-template-columns: 200px auto;
	margin-top: 20px;
	align-items: center;
	background-color: #e9edf0;
	padding: 30px 50px;
	border-radius: 5px;
	border: 1px solid #e3e3e3;
}

.author {
	font-size: 25px;
	margin-left: 20px;
	color: #75818e;
}

.photo img {
	border-radius: 5px;
	width: 200px;
}

.input-container {
	border-radius: 5px;
	background: #677482;
	padding: 10px;
}

.input-container input {
	border: none;
	background: transparent;
	color: white;
	padding: 6px 15px;
	font-size: 18px;
}

::placeholder { /* Chrome, Firefox, Opera, Safari 10.1+ */
  color: #a6b0ba;
  opacity: 1; /* Firefox */
}
</style>
