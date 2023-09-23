<template>
    <header><h1>Friends Details</h1></header>
   <div>
    <h4>Name:{{ data.name }}</h4>
    <p>Email:{{ data.email }}</p>
    <p>Phone:{{ data.phone }}</p>
    <p>Location:{{ data.location }}</p>
   </div>
</template>

<script>
export default{
    props:['data']
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

  div {
    max-width: 400px;
    margin: 20px auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }

  h4 {
    font-size: 20px;
    margin-bottom: 10px;
  }

  p {
    margin: 5px 0;
  }
</style>



