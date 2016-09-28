<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
<style>
	*{margin:0;padding:0;}
	body{overflow:hidden;}
	canvas{display:block;border:1px solid #ccc;margin:10px auto;}
	input[type='button']{width:100px;height:30px;line-height:30px;cursor:pointer;}
</style>
</head>
<body>
<canvas id="canvas1" width="450" height="600">您的浏览器不支持HTML5</canvas>
<div style="height:50px;text-align:center;line-height:50px;">
	<input id="stop" type="button" value="开始" >
	<input id="restart" type="button" value="重新开始" style="display:none;float:right;margin-top:10px;" >
	<!-- 一开始只有“开始”按钮，“重新开始”按钮并不显示，只有在“暂停”按钮点击后，该按钮才会显示 -->
</div>
<script>
window.onload = function(){
	var cvs = document.getElementById('canvas1');
	var ctx = cvs.getContext("2d");
	
	var contarr = [];
	//主要数组，整个面板,是contarr[i][j]的格式，表示面板上第i行第j列的方格，值可以为0或1，0表示这个面板这个坐标对应没有方块，1表示对应的有方块
	var nowrect = [];//正在运动的方块
	var nextrect = [];//下一个方块
	var num = 0;//分数
	var timeline;//计时器
	var stop = true;//是否暂停
	var speed = 400;//速度 / 毫秒
	//4个小方块组成的方块的所有可能的形状（共16种）如下，方块分布在4行4列的格局里，4个小方块要能连成一个整体,1表示此处有一个方块，0表示此处没有方块
	var createRect = [[ //创建方块形状
			[0,0,0,0],
			[0,0,0,0],
			[1,1,1,1],
			[0,0,0,0]
		],[
			[0,0,0,0],
			[0,1,1,0],
			[0,1,1,0],
			[0,0,0,0]
		],[
			[0,0,0,0],
			[1,1,1,0],
			[0,1,0,0],
			[0,0,0,0]
		],[
			[0,1,1,0],
			[0,1,0,0],
			[0,1,0,0],
			[0,0,0,0]
		],[
			[0,1,1,0],
			[0,0,1,0],
			[0,0,1,0],
			[0,0,0,0]
		],[
			[0,1,0,0],
			[0,1,1,0],
			[0,0,1,0],
			[0,0,0,0]
		],[
			[0,0,1,0],
			[0,1,1,0],
			[0,1,0,0],
			[0,0,0,0]
		],[
			[0,1,0,0],
			[0,1,0,0],
			[0,1,0,0],
			[0,1,0,0]
		]];
	//初始化
	init();
	function init(){
		contarr = [];//主要数组，整个画板。用contarr[i][j]来表示面板上第i行第j列的方格
		nowrect = [];//正在运动的方块，此时的方块，用nowrect[i][j]来表示：选取在这4个方格的行和列，第i行第j列的方格（例如一个田字型的4个方块，nowrect[0][0]表示其左上角的一个方块）
		nextrect = [];//下一个方块
		num = 0;//分数
		timeline = null;//计时器
		stop = true;//是否暂停
		//添加背景
		ctx.fillStyle = "#000000";
		ctx.strokeStyle = "#ffffff";
		ctx.fillRect(0,0,450,600);//canvas的width:450和高度600，先是画了一个全黑的画布
		ctx.clearRect(20,25,275,550);//在left20,top25处选取宽度275，高度550的区域清空（用来画俄罗斯方块的画板）
		ctx.fillStyle = "#ffffff";//字体填充为白色
		ctx.font = "20px 黑体";
		ctx.textAlign = "left";
		ctx.fillText("下一个:",325,50,100);
		ctx.clearRect(325,70,100,100);//在left325,top70处选取宽度100，高度100（25*4）的区域清空（用来画"下一个"的画板）
		ctx.fillText("得分:",325,260,100);//在left325,top260处选取宽度100（25*4），用来填“得分”二字
		ctx.fillText("0",325,300,100);//默认得分为0
		ctx.strokeStyle = "#cccccc";
		ctx.lineWidth = 1;
		ctx.fillStyle = "#3A70A3";
		//填充面板数组
		for(var i=0;i<22;i++){   //22行
			var arr = [];
			for(var j=0;j<11;j++){arr.push(0);};  //11列，先初始化，都存入0
			contarr.push(arr);
		}
		contdraw();//绘制主面板
		rectdraw();//绘制窗口面板
		//暂停
		document.getElementById("stop").onclick = function(){
		//左侧的开始按钮在被电击后显示“暂停”，在“暂停按钮”被点击后又变为“开始”
			document.getElementById("restart").style.display = 'block';//暂停按钮点击后，“重新开始”按钮由默认的不显示变为显示
			if(stop){//左侧的开始按钮在被电击后显示“暂停”，在“暂停按钮”被点击后又变为“开始”
				timeline = setInterval(function(){move(0,1);},speed);//暂停，设置时间间隔,speed为400ms
				this.value = "暂停";
			}else{
				clearInterval(timeline);
				this.value = "开始";
			}
			stop = !stop;
		}
		//重新开始
		document.getElementById("restart").onclick = function(){
			clearInterval(timeline);           //开始，清除时间间隔
			document.getElementById("stop").value = "开始";
			init();//重新开始，初始化
		}
		//键盘事件,响应键盘的移动命令
		document.onkeyup=function(event){
			var e = event || window.event || arguments.callee.caller.arguments[0];
			if(e && e.keyCode==37){
				move(-1,0);//left方向键,向左移动一格
			}else if(e && e.keyCode == 39){
				move(1,0);//right方向键，向右移动一格
			}else if(e && e.keyCode == 40){
				move(0,1);//down方向键，向下移动一格
			}else if(e && e.keyCode == 38){
				rotate();//up方向键，用于旋转方块更改方块的形状
			}
        }; 
	};
	//旋转方块,即在4行4列的方块阵里
	function rotate(){
		//清除
		for(var i=0;i<nowrect.length;i++){  //此时4个方块共占几行  //对此时的4个方块进行设置
			for(var j=0;j<nowrect[i].length;j++){//此时4个方块共占几列
				if(nowrect[i][j]){
					var px = 20+(j+nowrect.left)*25;//方块组的第j列所在位置，25是每个方块的宽度，20是画布的左侧边的宽度
					var py = 25+(i+nowrect.top)*25;//方块组的第i行所在位置，是画布的上下的边的宽度也是25
					if(!(i+nowrect.top<0)){//此时4个方块不是在第1行，即已经从上面下来了
						contarr[i+nowrect.top][j+nowrect.left] = 0;//将其设置为0.表示清除当前方块,以便画新的旋转后的方块组
					};						
				}
			}
		}
		//创建旋转后的形状
		var rot = [];
		var saver;  //保存方块形状
		for(var i=0;i<nowrect.length;i++){rot.unshift([]);}  //rot.unshift([])向rot数组的开头添加一个或更多元素，先初始化
		for(i=0;i<nowrect.length;i++){				//对此时的4个方块进行设置
			for(var j=0;j<nowrect[i].length;j++){
				rot[j].unshift(nowrect[i][j]);//将此时方块组的位置存到rot数组中
			}
		}
		rot.left = nowrect.left;
		rot.top = nowrect.top;
		saver = nowrect;//保存此时的方块形状
		nowrect = rot;
		//如果不可以旋转则nowrect不变
		if(ifmove(0,0)!=1){nowrect = saver;}		//不能移动，则将刚才保存的方块形状赋给此时的方块组	
		for(i=0;i<nowrect.length;i++){				//对此时的4个方块进行设置
			for(j=0;j<nowrect[i].length;j++){
				if(i+nowrect.top<0){continue;}//此时4个方块在还没到第1行，刚从上面下来，则继续
				if(nowrect[i][j]){
					contarr[i+nowrect.top][j+nowrect.left] = 1;
				}
			}
		}
		contdraw();
	}
	//移动方块，mx和my只能为0、1、-1，因为，每次只能移动一格，mx表示左右方向的移动（mx为-1表示向左移动，mx为1表示向右移动），my表示上下方向的移动（my为1表示向下移动）
	function move(mx,my){
		//清除数组中的当前方块
		for(var i=0;i<nowrect.length;i++){
			for(var j=0;j<nowrect[i].length;j++){      //对此时的4个方块进行设置
				if(nowrect[i][j]){
					var px = 20+(j+nowrect.left)*25;
					var py = 25+(i+nowrect.top)*25;
					if(!(i+nowrect.top<0)){//此时4个方块不是在第1行，即已经从上面下来了
						contarr[i+nowrect.top][j+nowrect.left] = 0;  //将其设置为0.表示清除当前方块
					};					
				}
			}
		}
		var state = ifmove(mx,my);//可以怎么移动的状态， 0：往下不可移动，1：可以移动，2：左右不可移动
		if(state){//如果可以移动，则 top,left += my,mx
			if(state !=2){  //不是左右不可移动，即可以左右和朝下移动。
						//nowrect.top和nowrect.left表示4个方块在移动之后的top和left的位置
				nowrect.top += my;    //4个方块在朝下移动的可能值的移动之后在垂直方向的位置（即第几行）
				nowrect.left += mx;   //4个方块在左右移动的可能值的移动之后在水平方向的位置（即第几列）
			}

			//将4个方块移动到的某个位置画出来
			for(i=0;i<nowrect.length;i++){        //对此时的4个方块进行设置
				for(j=0;j<nowrect[i].length;j++){
					if(i+nowrect.top<0){continue;}//此时4个方块在还没到第1行，刚从上面下来，则继续
					if(nowrect[i][j]){
						contarr[i+nowrect.top][j+nowrect.left] = 1;
						//[i+nowrect.top]为第几行，[j+nowrect.left]为第几列，contarr[i+nowrect.top][j+nowrect.left]为在面板的对应的行和列的位置的方块，将其设置为1.表示将当前坐标方块设置为存在，即面板中nowrect每次移动到某个位置，都将该4个方块画出来。
					}
				}
			}
		}else{//如果不能移动，则数组添加原位置方块
			for(i=0;i<nowrect.length;i++){		 //对此时的4个方块进行设置
				for(j=0;j<nowrect[i].length;j++){
					if(i+nowrect.top<0){continue;}//此时4个方块在还没到第1行，刚从上面下来，则继续
					if(nowrect[i][j]){
						contarr[i+nowrect.top][j+nowrect.left] = 1;//将其设置为1.表示将当前坐标方块设置为存在
					}
				}
			}
//------------------------------------------------- 计算得分----------------------------------------------------------
			var clr = [];//该数组用来记录铺满了几行
			for(i=0;i<contarr.length;i++){		//对画板数组进行检测来计算分数
				var boo = 0;
				for(j=0;j<contarr[i].length;j++){  
					if(contarr[i][j]){boo++}  //判断一行的所有列是否全被铺满，如果是，得11分
				}
				if(boo==11){//如果一行全铺满了（一行有11列），则得100分
					num += 100;fraction(num);//得到游戏得分
					clr.push(i);//铺满了几行了
				}
			}
//-------------------------------------------消除,每铺满一行，该行就消除---------------------------------------------
			for(i=0;i<clr.length;i++){                              
				var id = clr.length-i-1;//在铺满方格的行中，从排在最下面的行最先消除
				contarr.splice(clr[id],1);//从数组删除该行
			}
			for(i=0;i<clr.length;i++){
				var n = [];
				for(j=0;j<contarr[0].length;j++){n.push(0);}
				contarr.unshift(n);//把面板的底部铺满的方格删除后，要在面板第一行添加一行空的方格
			}
			//游戏结束,如果方块累积到第1行，第1行的所有列均不为空即均有方块，则游戏结束
			for(i=0;i<contarr[0].length;i++){if(contarr[0][i]){alert("游戏结束");clearInterval(timeline);return false;}}
			rectdraw();//绘制"下一个"的窗口面板
		}
		contdraw();//绘制主面板
	}
	//判断是否可以移动,即在水平方线和垂直方向移动了mx、my之后，是否还可以移动
	function ifmove(mx,my){
	//ifmove(mx,my),mx和my分别为在行和列上的移动步数（mx为1表示向右移动一格，为-1表示向左移动一格，my为1表示向下移动一格），该函数可能的返回值为：0,1,2（ 0：往下不可移动，1：可以移动，2：左右不可移动）
		var boo = 1;
		for(var i=0;i<nowrect.length;i++){//对此时的4个方块进行判断
			for(var j=0;j<nowrect[i].length;j++){
				if(nowrect[i][j]){
					var px = j+nowrect.left+mx;//表示这4个方块在列上可能移动到的地方
					var py = i+nowrect.top+my; //表示这4个方块在行上可能移动到的地方
					if(px<0){return 2;}// px<0即到第1列了，左右不可移动
					if(px>10){return 2;}// px>10即到第11列了，左右不可移动
					if(py<0){continue;} //第0行，继续
					if(py>21){return 0;}//py>21即到第22行了，往下不可移动
					var fr = contarr[py][px];//py行px列的方格
					if(fr!=0){  //contarr[py][px]处的方格不为空
						if(mx==0){return 0;}//往下不可移动
						if(my==0){return 2;}// 左右不可移动
					}
				}
			}
		}
		// 0：往下不可移动，1：可以移动，2：左右不可移动
		return boo;
	}
	//绘制"下一个"的窗口面板（4行4列，并且里面每次都要产生新的方块组）
	function rectdraw(){
		//------------------------------------先产生"下一个"的窗口面板里的方块组内容-----------------------------------
		if(nextrect.length == 0){
			nowrect = Box();  //还没产生下一个掉下来的方块组（即nextrect.length == 0）时，随机产生4个方块的形状
		}else{
			nowrect = nextrect;//刚才产生的方块组掉下来之后，就再产生下一个方块组
		}
		nowrect.top = -4;//此时方块组的位置：left:4,top:-4（即占有了面板第一行上面还没下来的4行和1到4列）
		nowrect.left = 4;
		nextrect = Box();     //随机产生4个方块的形状
		//-----------------------------------再将产生的方块组内容画到"下一个"的窗口面板里，分两步：先画4*4窗口面板，再画刚才产生的方块组
		for(var i=0;i<nextrect.length;i++){  //下个方块组的列数
			for(var j=0;j<nextrect[i].length;j++){//该方块组每列对应的行数
				//每个小方块的宽高均为25。"下一个"的窗口面板对应整个canvas的位置是：left:325,top:70
				var wx = 325+(j*25);//循环地，这是方块组中某个方块在水平方向所占有的位置
				var wy = 70+(i*25);//循环地，这是方块组中某个方块在垂直方向所占有的位置
				ctx.clearRect(wx,wy,25,25);
				if(nextrect[i][j]){  //若方块组内的该方块存在
					ctx.strokeRect(wx,wy,25,25);
					ctx.fillRect(wx+1,wy+1,23,23);//填充方块组的该方块，给方块（宽度为25）填充蓝色（为留缝隙，填充的宽度为23）
				}else{
					ctx.strokeRect(wx,wy,25,25);//若方块组内的该方块不存在，就只描边不填充
				}
			}
		}
	}
	//绘制主面板
	function contdraw(){
		for(var i=0;i<contarr.length;i++){
			for(var j=0;j<contarr[i].length;j++){
				var wx = 20+(j*25);//在主面板上把主面板上的方块组画出来
				var wy = 25+(i*25);//
				ctx.clearRect(wx,wy,25,25);
				if(contarr[i][j]){//该位置的方块若有，则填充
					ctx.fillRect(wx+1,wy+1,23,23);//给方块（宽度为25）填充蓝色（为留缝隙，填充的宽度为23）	
				}else{//否则只给面板描边
					ctx.strokeRect(wx,wy,25,25);
				}
			}
		}
	};
	//修改分数,显示在得分上，num就是得到的分数
	function fraction(num){
		var fillcolor = ctx.fillStyle;
		ctx.fillStyle = "#000000";
		ctx.fillRect(325,280,100,20);//在left325,top280处选取宽度100（25*4），高度20的区域用来填得分
		ctx.fillStyle = "#ffffff";//字体为白色
		ctx.fillText(num,325,300,100);
		ctx.fillStyle = fillcolor;
	};
	//返回随机形状
	function Box(){
		var len = createRect.length;//createRect里面共有8中形状的方块组，len为8
		var rtvalue = createRect[parseInt(Math.random()*len)];//随机选一个1~8的数字，从里面选一个方块组
		return rtvalue;
	}
}
</script>
</body>
</html>
