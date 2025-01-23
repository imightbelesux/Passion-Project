# Passion-Project

let rows = 3 //create amount of row
let cols = 3 // create amount of cols
let cellWidth = 250
let theImage;
let x = 1
let y = 1
let currentplayer = 0
let count = 0
let mouse = 0



function preload() {
	theImage = loadImage('ximage.png')
	theImage2 = loadImage('o.png')
}


function setup() {
	createCanvas(windowWidth, windowHeight);
	background(100);
	print('start')

	// initializ players
	for (let i = 0; i < 9; i++) {
		player1Selection[i] = false


	}
	// initializ players
	for (let i = 0; i < 9; i++) {
		player2Selection[i] = false
	}
}

function draw() {

	drawBoard()
	drawplayer1()
	drawplayer2()
winScreen()
endGame()
}
function drawBoard() {
//	clear()
	fill('rgb(120,228,245)')
	// let i = 8
	for (let i = 0; i < 9; i++) {
		// print('cell ' + i)
		let x = (i % 3) * cellWidth
		let y = Math.floor(i / 3) * cellWidth
		square(x, y, cellWidth)
	}
}

player1Selection = []

function drawplayer1() {
	//image(theImage,x,y, cellWidth,cellWidth)
	for (let i = 0; i < 9; i++) {
		// print('cell ' + i)
		let isSelected = player1Selection[i]
		if (isSelected) {
			let x = (i % 3) * cellWidth
			let y = Math.floor(i / 3) * cellWidth
			image(theImage, x, y, cellWidth, cellWidth)
		}
	}
}
player2Selection = []

function drawplayer2() {
	//image(theImage,x,y, cellWidth,cellWidth)
	for (let i = 0; i < 9; i++) {
		// print('cell ' + i)
		let isSelected = player2Selection[i]
		if (isSelected) {
			let x = (i % 3) * cellWidth
			let y = Math.floor(i / 3) * cellWidth
			image(theImage2, x, y, cellWidth, cellWidth)
		}
	}
}
function mouseClicked() {
	// given mouseX, mouseY
	if (mouse == 0) {
		mouseClick = false
		print(mouseX, mouseY)
		row = Math.floor(mouseY / cellWidth)
		print(row)
		col = Math.floor(mouseX / cellWidth)
		print(col)
		if (row < 3 && col < 3) {
			cellIndex = row * 3 + col // calculate using mouseX, mouseY
			if (!player2Selection[cellIndex] && !player1Selection[cellIndex]) {
				if (currentplayer == 0) {
					// 1st player stuff
					player1Selection[cellIndex] = true
					let win = checkPlayer1Winner()
					if (win) {
						print('player 1 wins!')

					}
				} else {
					// 2nd player stuff
					player2Selection[cellIndex] = true
					let win = checkPlayer2Winner()
					if (win) {
						print('player 2 wins!')
					}
				}

				// change player
				currentplayer = (currentplayer + 1) % 2

			}
		}
	}
}
function checkPlayer1Winner() {
	if (
		//horizontal win 1
		(player1Selection[0] && player1Selection[1] && player1Selection[2]) ||
		// horizontal win 2
		(player1Selection[3] && player1Selection[4] && player1Selection[5]) ||
		// horizontal win 3
		(player1Selection[6] && player1Selection[7] && player1Selection[8]) ||
		//diagonal win 1
		(player1Selection[0] && player1Selection[4] && player1Selection[8]) ||
		// diagonal win 2
		(player1Selection[2] && player1Selection[4] && player1Selection[6]) ||
		// vertical win 1
		(player1Selection[0] && player1Selection[3] && player1Selection[6]) ||
		// vertical win 2
		(player1Selection[1] && player1Selection[4] && player1Selection[7]) ||
		// vertical win 3
		(player1Selection[2] && player1Selection[5] && player1Selection[8])
	) {
count = 1
mouse = 1
		return true
	}
	return false

}
function checkPlayer2Winner() {
	if (
		//horizontal win 1
		(player2Selection[0] && player2Selection[1] && player2Selection[2]) ||
		// horizontal win 2
		(player2Selection[3] && player2Selection[4] && player2Selection[5]) ||
		// horizontal win 3
		(player2Selection[6] && player2Selection[7] && player2Selection[8]) ||
		//diagonal win 1
		(player2Selection[0] && player2Selection[4] && player2Selection[8]) ||
		// diagonal win 2
		(player2Selection[2] && player2Selection[4] && player2Selection[6]) ||
		// vertical win 1
		(player2Selection[0] && player2Selection[3] && player2Selection[6]) ||
		// vertical win 2
		(player2Selection[1] && player2Selection[4] && player2Selection[7]) ||
		// vertical win 3
		(player2Selection[2] && player2Selection[5] && player2Selection[8])
	) {
count = 2
mouse = 2
		return true
	}

	return false

}
function winScreen() {
if (count == 1){
fill("rgb(2,121,241)")
rect(0,0,cellWidth*3 ,cellWidth*3)

	textSize(60)
	fill('rgb(0,0,0)')
	stroke(0)
textAlign(CENTER)
	text('player 1 wins!', 1.5* cellWidth, 1.5* cellWidth)
}
if (count == 2){
fill("rgb(176,255,0)")
rect(0,0,cellWidth*3,cellWidth*3)
	
	textSize(60)
	fill('rgb(0,0,0)')
	stroke(0)
textAlign(CENTER)
	text('player 2 wins!', 1.5* cellWidth, 1.5* cellWidth)	
}	
//if(checkPlayer2Winner && checkPlayer2Winner == false){

//}
}
function endGame() {
	if (mouse == 1) {
		mouseClick = true
}
}
https://docs.google.com/document/d/1GglS1u5FoTkKvejxpfG9JwE937DBdiHqLx7GUPQWQTA/edit?pli=1&tab=t.0
