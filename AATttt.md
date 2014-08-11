aat-tictactoe
================

tic tac toe game (among others?)

my name is Fizan and I am new to web programming. here is my first professional project:

<!DOCTYPE HTML>
<html>
<head><link rel="stylesheet" type="text/css" href="ttt.css"/>

<script>

		var a, box, c, context, content, filled, winCombo;
		var turn = 0;
		var playerTurn, CPUturn, sym, variable, fullName, boxNumber, CPUbox, CPUnumber, CPUc, CPUcontext;
		var BoxesFilled = 0;
		window.onload=function()
		{			
			filled = new Array();
			content = new Array();
			winCombo = [[1,2,3],[4,5,6],[7,8,9],[1,4,7],[2,5,8],[3,6,9],[1,5,9],[3,5,7]];

			for(var i = 1; i < 10; i++)
			{
			filled[i] = false;
			content[i] = '';
			}
		}
		
		function Symbol() {
		
			document.getElementById(fullName).src = '/home/fizan/Documents/AAT Tic Tac Toe/Ambassador Pics/O.gif';			
			if (document.getElementById('1').hidden != true) document.getElementById('1').style.visibility = 'hidden';
			if (document.getElementById('2').hidden != true) document.getElementById('2').style.visibility = 'hidden';
			if (document.getElementById('3').hidden != true) document.getElementById('3').style.visibility = 'hidden';
			if (document.getElementById('4').hidden != true) document.getElementById('4').style.visibility = 'hidden';
			if (document.getElementById('5').hidden != true) document.getElementById('5').style.visibility = 'hidden';
			if (document.getElementById('6').hidden != true) document.getElementById('6').style.visibility = 'hidden';
			if (document.getElementById('7').hidden != true) document.getElementById('7').style.visibility = 'hidden';
			if (document.getElementById('8').hidden != true) document.getElementById('8').style.visibility = 'hidden';
			if (document.getElementById('9').hidden != true) document.getElementById('9').style.visibility = 'hidden';
			if (document.getElementById('10').hidden != true) document.getElementById('10').style.visibility = 'hidden';
			}

		function chooseBox()
		{
			
			box = "Box" + boxNumber;
			c = document.getElementById(box);
			context = c.getContext("2d");
		
			if(filled[boxNumber] == false)
			{
				if(turn % 2 == 0)
				{
				content[boxNumber] = 'X';
				var Ximage = new Image();
				Ximage.src = '/home/fizan/Documents/AAT.jpg';
				Ximage.onload = function() {
				context.drawImage(Ximage, -5, 20);
				checkWin(content[boxNumber]);	
				};
				}
				
 				turn++; 
 				playerTurn = !playerTurn; 
 				CPUturn = !CPUturn; 
 				filled[boxNumber] = true; 
 				BoxesFilled++;
				
				if(BoxesFilled >= 9)
				{
					alert("Tie game. You both stink!");
					location.reload(true);
				}
			}
			else if(filled[boxNumber] == true) alert("What are you trying? That space is taken, dummy!");
			else alert("ERROR");
		}
		
		function CPUboxNumber() {
			if (filled[5] == false) return CPUnumber = 5;

			if ((filled[1] == true && (filled[7] == true || filled[9] == true) && filled [4] == true && 
			filled[5] == true && filled[6] == false && filled[8] == false) && (content[1] == content[9] || content[1] == content[7]) && (content[4] == content[5]) && (filled[6] == false)) return CPUnumber = 6;

			if ((filled[1] == true && filled[3] == true && filled[8] == true && filled[2] == true && 
			filled[5] == true) && (content[1] == content[3] && content[3] == content[8] && content[2] == content[5]) && filled[6] == false)
			return CPUnumber == 6;
		
			for (var z = 0; z < 8; z++) {  
				if ((filled[winCombo[z][1]] == true) && (filled[winCombo[z][2]] == true) 
				&& (content[winCombo[z][1]] == content[winCombo[z][2]]) && (filled[winCombo[z][0]] == false)) 
				return CPUnumber = winCombo[z][0];
				else if ((filled[winCombo[z][0]] == true) && (filled[winCombo[z][2]] == true) 
				&& (content[winCombo[z][0]] == content[winCombo[z][2]]) && (filled[winCombo[z][1]] == false)) 
				return CPUnumber = winCombo[z][1];
				else if ((filled[winCombo[z][0]] == true) && (filled[winCombo[z][1]] == true) 
				&& (content[winCombo[z][0]] == content[winCombo[z][1]]) && (filled[winCombo[z][2]] == false)) 
				return CPUnumber = winCombo[z][2];
			} 
			
			if ((filled[1] == true && filled[2] == true) && (content[1] != content[2])) return CPUnumber = 5;
			else if (((filled[1] == true && filled[5] == true && filled[9] == true) && 
			(content[1] == content[9]) && (content[5] != content[9]))
			|| ((filled[3] == true && filled[5] == true && filled[7] == true) &&
			(content[3] == content[7]) && (content[5] != content[7]))) {
			if (filled[4] == false) return CPUnumber = 4;
			else if (filled[6] == false) return CPUnumber = 6;
			} 		
			
			else if (filled[1] == false) return CPUnumber = 1;
			else if (filled[3] == false) return CPUnumber = 3;
			else if (filled[7] == false) return CPUnumber = 7;
			else if (filled[9] == false) return CPUnumber = 9;
			else if (filled[5] == false) return CPUnumber = 5;
		}
		
		function CPUmove() 
		{
			CPUboxNumber();		
			box = "Box" + CPUnumber;
			CPUc = document.getElementById(box);
			CPUcontext = CPUc.getContext("2d");
		
			if(filled[CPUnumber] == false)
			{
				if(turn % 2 != 0)
				{
				content[CPUnumber] = 'O';				
				var Oimage = new Image();
				Oimage.src = '/home/fizan/Documents/AAT Tic Tac Toe/Ambassador Pics/' + fullName + '.png';
				Oimage.onload = function() {
				CPUcontext.drawImage(Oimage, 2.5, 2.5);
				checkWin(content[CPUnumber]);	
				};
				}

 				turn++; 
 				playerTurn = !playerTurn; 
 				CPUturn = !CPUturn; 
 				filled[CPUnumber] = true; 
 				BoxesFilled++;
				
				if(BoxesFilled >= 9)
				{
					alert("Tie game. You both stink!");
					location.reload(true);
				}
			}
		}
			
		function checkWin(symbol)
		{		
			for(var j = 0; j < winCombo.length; j++)
			{
			if(content[winCombo[j][0]] == symbol && content[winCombo[j][1]] == symbol &&
			content[winCombo[j][2]] == symbol)
			{
				alert(symbol + " Wins!");
				location.reload(true);
			}
		}
		}
		
		</script></head>
		<body>

	<h1>Welcome to The AAT Project's Tic Tac Toe</h1>
	<h2>Who will you play against?</h2><br>
	<button id="1" onclick="variable = '1'; fullName = 'EastonLaChapelle'; Symbol();">
	<img id = "EastonLaChapelle" src='/home/fizan/Documents/AAT Tic Tac Toe/Ambassador Pics/EastonLaChapelle.png' width='130' height='100'></button>
	<button id="2" onclick="variable = '2'; fullName = 'EdelBrowne'; Symbol();">
	<img id="EdelBrowne" src="/home/fizan/Documents/AAT Tic Tac Toe/Ambassador Pics/EdelBrowne.png" width="90" height="90"></button>
	<button id="3" onclick="variable = '3'; fullName = 'GraceYoung'; Symbol();">
	<img id="GraceYoung" src="/home/fizan/Documents/AAT Tic Tac Toe/Ambassador Pics/GraceYoung.png" width="80" height="100"></button>
	<button id="4" onclick="variable = '4'; fullName = 'JonnyCohen'; Symbol();">
	<img id="JonnyCohen" src="/home/fizan/Documents/AAT Tic Tac Toe/Ambassador Pics/JonnyCohen.png" width="70" height="100"></button>
	<button id="5" onclick="variable = '5'; fullName = 'KatherineBomkamp'; Symbol();">
	<img id="KatherineBomkamp" src="/home/fizan/Documents/AAT Tic Tac Toe/Ambassador Pics/KatherineBomkamp.png" width="80" height="100"></button>
	<button id="6" onclick="variable = '6'; fullName = 'MoniqueColeman'; Symbol();">
	<img id="MoniqueColeman" src="/home/fizan/Documents/AAT Tic Tac Toe/Ambassador Pics/MoniqueColeman.png" width="100" height="100"></button>
	<button id="7" onclick="variable = '7'; fullName = 'ParamJaggi'; Symbol();">
	<img id="ParamJaggi" src="/home/fizan/Documents/AAT Tic Tac Toe/Ambassador Pics/ParamJaggi.png" width="75" height="100"></button>
	<button id="8" onclick="variable = '8'; fullName = 'StaceyFerreira'; Symbol();">
	<img id="StaceyFerreira" src="/home/fizan/Documents/AAT Tic Tac Toe/Ambassador Pics/StaceyFerreira.png" width="100" height="100"></button>
	<button id="9" onclick="variable = '9'; fullName = 'JackAndraka'; Symbol();">
	<img id="JackAndraka" src="/home/fizan/Documents/AAT Tic Tac Toe/Ambassador Pics/JackAndraka.png" width="100" height="100"></button>	
	<button id="10" onclick="variable = '10'; fullName = 'OmarAbudayyeh'; Symbol();">
	<img id="OmarAbudayyeh" src="/home/fizan/Documents/AAT Tic Tac Toe/Ambassador Pics/OmarAbudayyeh.png" width="80" height="100"></button><br>

	<div id ="box">
			<h2>Can you beat our ambassador?</h2>
			<canvas id = "Box1"  width="100" height="100" style="" onclick="boxNumber = 1; chooseBox(); CPUmove();"></canvas>
			<canvas id = "Box2"  width="100" height="100" style="border-left:5px solid black; border-right:5px solid black;" onclick="boxNumber = 2; chooseBox(); CPUmove();"></canvas>
			<canvas id = "Box3"  width="100" height="100" style="" onclick="boxNumber = 3; chooseBox(); CPUmove();"></canvas><br/>
			<canvas id = "Box4"  width="100" height="100" style="border-bottom:5px solid black; border-top:5px solid black;" onclick="boxNumber = 4; chooseBox(); CPUmove();"></canvas>
			<canvas id = "Box5"  width="100" height="100" style="border:5px solid black;" onclick="boxNumber = 5; chooseBox(); CPUmove();"></canvas>
			<canvas id = "Box6"  width="100" height="100" style="border-top:5px solid black; border-bottom:5px solid black;" onclick="boxNumber = 6; chooseBox(); CPUmove();"></canvas><br/>
			<canvas id = "Box7"  width="100" height="100" style="" onclick="boxNumber = 7; chooseBox(); CPUmove();"></canvas>
			<canvas id = "Box8"  width="100" height="100" style="border-right:5px solid black; border-left:5px solid black" onclick="boxNumber = 8; chooseBox(); CPUmove();"></canvas>
			<canvas id = "Box9"  width="100" height="100" style="" onclick="boxNumber = 9; chooseBox(); CPUmove();"></canvas><br>
		</div>
	</body>
	</html>
