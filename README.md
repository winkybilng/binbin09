# binbin09
<!DOCTYPE html>
<html>
<head>
	<title>binbin09</title>
	<style type="text/css">
		#tree{
			width: 1200px;
		}
		.foot{
			background-color: white;
			border: 2px solid #999;
			padding:20px 10px;
			width: 45%;
			box-sizing: border-box;
			float: left;
			margin: 0 2.5%;
		}
		.active{
			background-color: #F08080;
			padding:20px 10px;
			border: 2px solid #999;
			width: 45%;
			box-sizing: border-box;
			float: left;
			margin: 0 2.5%;
		}
		.first{
			z-index: 10;
		}
		.second{
			z-index: 20;
		}
		.third{
			z-index: 30;
		}
		.fourth{
			z-index: 40;
		}
		.fifth{
			z-index: 50;
		}
		#ppp{
			clear: both;
		}
	</style>
</head>
<body>
<div id="tree" class="foot" class="first">
	Super
	<div class="foot" class="second">
		Car
		<div class="foot" class="third">
			Apple
			<div class="foot" class="fourth">Pear
			</div>
			<div class="foot" class="fourth">Pig
			</div>
			<div class="foot" class="fourth">Cola
			</div>	
			<div class="foot" class="fourth">Succor
			</div>		
		</div>
		<div class="foot" class="third">
			Phone
		</div>
		<div class="foot" class="third">
			Student
			<div class="foot" class="fourth">Book
			</div>
			<div class="foot" class="fourth">School
			</div>
		</div>
	</div>
	<div class="foot" class="second">
		Note
		<div class="foot" class="third">
			Human
			<div class="foot" class="fourth">Code
			</div>
			<div class="foot" class="fourth">Operate
			</div>
			<div class="foot" class="fourth">Man
			</div>
		</div>
		<div class="foot" class="third">
			Program
			<div class="foot" class="fourth">Element
			<div class="foot" class="fifth">Cat
			</div>
			</div>
			<div class="foot" class="fourth">Grass
			</div>
		</div>
	</div>
	<div class="foot" class="second">Fish
	</div>
</div>
<div id="anniu">
<button id="DLR">遍历</button>
<input type="text" value="请输入想要查找的节点" id="text" onfocus="myfunction(this)">
<button id="search">查询</button>
<button id="delete">删除</button>
<input type="text" value="请输入想要加入的节点内容" id="text1" onfocus="myfunction(this)">
<button id="join">加入节点</button>
</div>
<script type="text/javascript">
	var c;
	var tree = document.getElementById("tree");
	var Nodearray = new Array();
	var a = document.getElementById("text");
	function myfunction(x){
		x.value="";
	}
	function active(Nodearray){
		var i=0;
		var int = setInterval(function(){
			if (i<Nodearray.length) {
				if (i>0) {
				Nodearray[i-1].className= "foot";}
				Nodearray[i].className = "active";
				i++;
			} else {
				Nodearray[i-1].className = "foot";
				clearInterval(int);
			}
		},500);
	}
	function search(Nodearray){
		var i = 0;
		var arr = Nodearray[0].innerText.split(" ");
		var int = setInterval(function(){
			if (i<Nodearray.length && arr[i]!=a.value) {
				if (i>0) {
				Nodearray[i-1].className= "foot";}
				Nodearray[i].className = "active";
				i++;
			} else if(arr[i] == a.value) {
				if (i>0) {
				Nodearray[i-1].className= "foot";}
				Nodearray[i].className= "active";
				clearInterval(int);
			}
			else{
				Nodearray[i-1].className = "foot";
				clearInterval(int);
				alert("查找的节点不存在了啦！");
			}
		},500);
	}
	function DLR(root){
		if (!root) {
			return;
		} else {
			Nodearray.push(root);
			for (var i = 0; i < root.children.length; i++) {
				DLR(root.children[i]);
			}
		}
	}
	document.getElementById("tree").addEventListener("click",function(){
		var divs =document.getElementById("tree").getElementsByTagName("div");
		for (var i = 0; i < divs.length; i++) {
			divs[i].className="foot";
		}
		c = event.target;//window.event.srcElement;
		c.className="active";
		});
	document.getElementById("anniu").addEventListener("click",function(){
		var b = event.target;
		var divs =document.getElementById("tree").getElementsByTagName("div");
		for (i = 0; i < divs.length; i++) {
			divs[i].className="foot";
			}
		switch(b.id){
			case "DLR":
			Nodearray = [];
			DLR(tree);
			active(Nodearray);
			break;
			case "search":
			Nodearray = [];
			DLR(tree);
			search(Nodearray);
			break;
			case "delete":
			c.parentNode.removeChild(c);
			break;
			case "join":
			var div=document.createElement("div");
			c.appendChild(div);
			div.className="foot";
			div.innerText = document.getElementById("text1").value;
			break;
		}
	});
</script>
</body>
</html>
