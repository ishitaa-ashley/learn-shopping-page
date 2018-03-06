<template>
<div class="hello container">
<header>
<div class=" row flex-container">
      <span class=" col-lg-2 col-sm-2 text">Jewel box </span> 
      <div class="col-lg-8 col-sm-8"><ul><li>Option 1</li>
      <li>Option 2</li>
      <li>Option 3</li>
      <li>Option 4</li>

      </ul>
      </div>
      <p class="checkurcart" @click="showcart"><i class="fas fa-shopping-basket" style="width:40px"></i>
        <p class="cartno">{{product_in_cart}}</p>
        <ul class="carthere dropdown">
        <li class="cartlist" v-if="cartproduct.length==0">No items in cart</li>
        <li class="cartlist" v-for="item in cartproduct" @dblclick="removeitem(item.id)">{{item.product}}  - ₹.{{item.price}}<p class="f" @click="removeitem(item.id)"><i class="fas fa-times"  ></i></p></li>

        <li class="cartlist"><label>Total</label><span id="price">₹.{{total}}</span></li>
        <button class="checkout" @click="checkoutitem">CHECKOUT</button>
        </ul>

        </p>
      
</div>
</header>
<div class="mainbody">
   
  <div class="row pic">
  <div class="layover"></div>
        <h1 class="over">JEWELBOX</h1>
        <button class="button-over">SHOP NOW</button>
  </div>
  <div class="row productshere">
  
  <div class="col-lg-3 col-md-4 cardmain hello card" v-for="product in products">

  
    
    <img :src="product.url">
    <p><h1>{{product.name}}</h1>
    <h4>₹{{product.price}}</h4>
    <button class="btn" @click="add_to_cart(product.id)" >ADD TO CART</button></p>
  </div>
  </div>
  </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      products:[{"name":"necklace","url":"https://i.pinimg.com/736x/65/76/99/657699cdb1e83538556ee80e103ec6c1--royal-jewels-crown-jewels.jpg","price":500, "id":0} , {"name":"earring","url":"https://www.christies.com/img/saleimages/NYR-14761-12062017-1.jpg?Width=600","price":700, "id":1},{"name":"necklace2","url":"https://i.pinimg.com/736x/65/76/99/657699cdb1e83538556ee80e103ec6c1--royal-jewels-crown-jewels.jpg","price":250, "id":2} , {"name":"earring2","url":"https://www.christies.com/img/saleimages/NYR-14761-12062017-1.jpg?Width=600","price":500, "id":3}],
      makeprice:0,
      makeproduct:'',
      idhere:0,
      cartproduct:[],
      indproduct:{},
      product_in_cart:0,
      drop:false,
      total:0,
      layout:false
      // item:[0,1,2,3,4],
      
    }
  },
  methods:{
    add_to_cart(val) {

        this.idhere=val;
        //alert(this.idhere);
        this.product_in_cart++;
        this.indproduct["product"]=this.products[this.idhere].name;
        this.indproduct["price"]=this.products[this.idhere].price;
        this.indproduct["id"]=this.products[this.idhere].id;
        //console.log(this.cartproduct);
        this.cartproduct.push({ ...this.indproduct });
        //console.log(this.cartproduct);
        this.total=this.total+this.products[this.idhere].price;
    },
    showcart()
    {
      var division=document.querySelector(".carthere");
      //var bodylay=document.querySelector(".bodyoverlay");
      this.dropdown=!this.dropdown;
      if(this.dropdown==true)
      {
        division.classList.remove("dropdown");
        division.classList.add("open");
        //bodylay.classList.add("layout");
      }
      else
      {
        division.classList.remove("open");
        division.classList.add("dropdown");
        //bodylay.classList.remove("layout");
      }
    },
    removeitem(removeid)
    {
      var listToDelete=[];
      listToDelete.push(removeid);
      //alert(removeid);
      var flag=0;
      /*this.cartproduct = this.cartproduct.filter(function(obj) {
    return listToDelete.indexOf(obj.id) === -1;
});*/
      
      for (var i = this.cartproduct.length - 1; i >= 0; --i) {
    if (this.cartproduct[i].id == removeid && flag<1) {
        this.cartproduct.splice(i,1);
        flag++;

    }
}
      this.total=0;
      this.product_in_cart=this.product_in_cart-1;
      for(var i=0;i<this.cartproduct.length;i++)
      {
        
        this.total=this.total+this.cartproduct[i].price;
        
      }
//console.log(this.cartproduct);
    },
checkoutitem()
{
  if(confirm("Are you sure to chcekout?"))
    {
      if(this.cartproduct.length==0)
        alert("no items in cart");
      else
      {
      alert("checkout confirmed ! Pay Rs."+this.total);
      this.cartproduct=[];
      this.total=0;
      this.product_in_cart=0;
    }
    }
  else
    alert("cancelled checkout");
}
    

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h4 {
  
  
  font-family: 'URW Chancery L', cursive;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.card
{
  
  border: none;
  margin-top: 10px;
  text-align: center;

}
.f
{
  margin-bottom: 0px;
}
img:hover {
    transform: scale(1.05); 
}
img
{
  height: 260px;
}
@media only screen and (max-width: 1500px) {
    img
    {
      height: 350px;
    }
}
.btn
{
  background-color: pink;
  color: white;
}
.productshere
{
  position: relative;
}
.cartno
{
  height:25px;
  width:30px;
  background-color: red;
  border-radius: 15px;
  color:white;
  margin-top: 17px;
}
.open
{
  background-color: #FF99B1;
  border-radius: 5px;
  color:white;
  width: 30%;
  z-index: 1;
  position: absolute;
  right: 0%;
  height: 300px;
  overflow: auto;


}
.checkout
{
  background-color: white;
  color:pink;
}
.carthere
{
  margin-top: 50px;
}
.cartlist
{
  
  margin-top: 10px;
  display: flex;
margin-left: 30%;


}
.dropdown{
display: none;
}
.pic
{
  position: relative;
  background-image: url("https://www.thewarehouse.co.nz/on/demandware.static/-/Sites/default/dw8ac75459/twl/campaign/themes/spring/week-9-2017/Style/pendant-necklaces.png");
  background-repeat: no-repeat;
  background-size: 100% 100%;
  height: 300px;
  width: 100%;
  margin-top: 80px;
}
.over
{
  position: absolute;
  top:30%;
  left:37%;
  
}
.button-over
{
 height: 30px;
 width: 200px;
 position: absolute;
  top:50%;
  left:37%;
  

}
.layover
{
  height: 300px;
  width: 100%;
  position: absolute;
  background: rgba(0, 0, 0, 0.2);
}

.layout
{
 width: 100%;
 position: absolute;
  background: rgba(0, 0, 0, 0.5);
}
.fas, .fa-times
{
  margin-left: 10px;
  margin-bottom: 0px;
    margin-top: -8px;
}
alert
{
  background-color: gray;
}
</style>
