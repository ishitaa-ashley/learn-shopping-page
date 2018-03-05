<template>
  <div id="app">
    <HelloWorld/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: 'URW Chancery L', cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  
}
ul
{
  list-style-type: none;
  margin: auto;
  margin-top: 10px;
}
li
{
  display: inline-block;
  margin-left: 10px;
  padding-right: 10px;
  font-size: 20px;
  font-family: 'URW Chancery L', cursive;
}
li:first-child
{
  margin-left: 0px;

}
li:hover
{
  cursor: pointer;
}

header
{
  top:0;
  width: 100%;
  position: fixed;
  z-index:1;
  background-color: white;
  left:0;

}

.text
{
  float: left;
  margin-left: 0px;
  font-size: 30px;
  font-family: 'URW Chancery L', cursive;
}

svg, .svg-inline--fa, .fa-cart-plus, .fa-w-18
{

 height: 50px;
 width: 50px;
 float: right;

 float: top;

}
svg:hover
{
  cursor: pointer;
}
.flex-container {
  display: flex;
}
.col-lg-8
{
  text-align: center;

}
.cardmain
{
 margin-left: 10px;
 height: 20%;


}

</style>
