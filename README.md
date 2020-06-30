https://percio.gitlab.io/maze 


//
let map = [
    "WWWWWWWWWWWWWWWWWWWWW",
    "W   W     W     W W W",
    "W W W WWW WWWWW W W W",
    "W W W   W     W W   W",
    "W WWWWWWW W WWW W W W",
    "W         W     W W W",
    "W WWW WWWWW WWWWW W W",
    "W W   W   W W     W W",
    "W WWWWW W W W WWW W F",
    "S     W W W W W W WWW",
    "WWWWW W W W W W W W W",
    "W     W W W   W W W W",
    "W WWWWWWW WWWWW W W W",    
    "W       W       W   W",
    "WWWWWWWWWWWWWWWWWWWWW",
];

let y=9;
let x=0;

let player = document.getElementById('player');
const mazeEl = document.getElementById('maze');
document.addEventListener('keydown', movePlayer);

const createMaze = function (blueprint) {
    for (let rowNum = 0; rowNum < blueprint.length; rowNum++) {
        const rowString = blueprint[rowNum]
        let blockDivs ='';
        for (let colNum = 0; colNum < rowString.length; colNum++) {
            const blockType = rowString[colNum]
            if (blockType === 'W') {
                blockDivs += '<div class="block wall"></div>'

            
            } else if (blockType === 'S') {
                blockDivs += '<div class="block start"></div>'
                y = rowNum
                x = colNum

            }
            else if (blockType === 'F') {
                blockDivs += '<div class="block end"></div>'
                y= rowNum
                x = colNum
            }
            else {
                blockDivs += '<div class = "block"></div>'
            }
        }
        mazeEl.innerHTML += '<div class= "row">' + blockDivs + '</div>'
    }

}

createMaze(map)


function movePlayer(event) {
    let player = document.getElementById('player');

    if (event.code === 'ArrowUp' ) {
        y = y - 1  
        console.log(x,y)
        console.log(map[x][y])
        
    }
    else if (event.code === 'ArrowDown') {
        y = y + 1
        console.log(x,y)
        console.log(map[x][y])
    }
    else if (event.code === 'ArrowLeft') {
        x = x - 1
        console.log(x,y)
        console.log(map[x][y])
    }
    else if (event.code === 'ArrowRight' ) {
        x = x + 1
        console.log(x,y)
        console.log(map[x][y])
    }

    
    player.style.top = y * 20 + "px";
    player.style.left = x * 20 + "px";
    
}






