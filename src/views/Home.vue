<template>
  <h1> Photo finder</h1>
  <div id="app-instasearch">
    <div class="input-container">
      <input ty[e="text" placeholder="Type a name" />]
    </div>
    <ul>
      <li class="photo">
        <img src="" />
        <span class="author"> Some Names </span>
        </li>
    </ul>
  </div>
</template>

<script>
var instasearchApp = new Vue({
  el: '#app=instasearch',

  data: {
    authorNameSearchString: "",
    photoFeed: null 
  }
})
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
