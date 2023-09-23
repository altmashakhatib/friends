<template>
  <header>
    <h1>Add Friends</h1>
  </header>
  <form @submit.prevent="submitData">
    <div>
      <label for="name">Name:</label>
      <input type="text" name="name" id="name" v-model.trim="name" />
    </div>
    <div>
      <label for="email">Email:</label>
      <input type="email" name="email" id="email" v-model.trim="email" />
    </div>
    <div>
      <label for="phone">Phone:</label>
      <input type="tel" name="phone" id="phone" v-model.trim="phone" />
    </div>
    <div>
    <label for="location">Location:</label>
    <input type="text" name="location" id="location" v-model.trim="location" /></div>
    <div>
        <button>Submit</button>
    </div>
  </form>
  <div v-if="friend" class="submit">Submit Sucesfully !</div>
</template>

<script>
export default{
    data(){
        return{
            name:'',
            email:'',
            phone:'',
            location:'',
            friend:false
        }
    },
    methods:{
        submitData(){
            if(this.name===''||this.email===''||this.phone===''||this.location===''){
                alert("Fill All Details Properly")
            }
            else{
               
                fetch('https://friends-eebcf-default-rtdb.firebaseio.com/friends.json',{
                    method:'POST',
                    headers:{
                        'content-type' :'application/json'
                    },
                    body:JSON.stringify({
                        name:this.name,
                        email:this.email,
                        phone:this.phone,
                        location:this.location
                    })
                    
                })
                this.name=''
                this.email=''
                this.phone=''
                this.location=''
                this.friend=true }

        }
    }
}
</script>

<style scoped>

  body {
    font-family: Arial, sans-serif;
    padding: 20px;
  }

  header {
    background-color: #f0f0f0;
    padding: 10px;
    text-align: center;
  }

  h1 {
    margin: 0;
    font-size: 24px;
  }

  form {
    max-width: 400px;
    margin: 20px auto;
  }

  label {
    display: block;
    margin-bottom: 5px;
  }

  input {
    width: 100%;
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    box-sizing: border-box;
  }

  button {
    padding: 10px 20px;
    background-color: #3498db;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }

  button:hover {
    background-color: #2980b9;
  }

  .submit{
    color: green;
    font-weight: bold;
    margin-top: 10px;
    margin-left: 400px;
  }
</style>





