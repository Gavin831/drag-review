<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		#box1{
			width: 100px;
			height: 100px;
			background-color: red;
			position: absolute;
		}
	</style>

	<script>
		window.onload = function(){

			var box1 = document.getElementById('box1');

			drag(box1);
			

			function drag(obj){
				//鼠标上在obj点下onmousedown事件
				//鼠标在document中移动onmousemove
				//鼠标松开onmouseup
				obj.onmousedown = function(e){

					//当调用一个元素的setCapture()方法以后，这个元素将会把下一次所有的鼠标按下相关的事件捕获到自身上
					obj.setCapture && obj.setCapture();

					e = e || window.e;
					var ol = e.clientX - obj.offsetLeft;
					var ot = e.clientY - obj.offsetTop;
					document.onmousemove = function(e){
						e = e || window.e;
						var x = e.clientX - ol;
						var y = e.clientY - ot;
						obj.style.left = x + "px";
						obj.style.top = y + "px";
					}

					document.onmouseup = function(){
						document.onmousemove = null;

						obj.releaseCapture && obj.releaseCapture();
					}

					// 当我们拖拽一个网页中的内容时，浏览器会默认去搜索引擎中搜索内容，
					// 此时会导致拖拽功能的异常，这个是浏览器提供的默认行为，
					// 如果不希望发生这个行为，则可以通过return false来取消默认行为
					
					// 但是这招对IE8不起作用
					//当调用一个元素的setCapture()方法以后，这个元素将会把下一次所有的鼠标按下相关的事件捕获到自身上
					return false;
				}

			}

			
			
		}

		
	</script>
</head>
<body style="width: 2000px;height: 1000px">
	<p>bguifddfnivdfiui</p>
	<div id="box1"></div>
</body>
</html>
