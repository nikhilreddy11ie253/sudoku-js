# sudoku-js
logic
const board = [
    [4, 0, 0, 2, 6, 0, 7, 0, 1],
    [6, 8, 0, 0, 7, 0, 0, 9, 0],
    [1, 0, 7, 0, 0, 4, 3, 0, 0],
    [8, 2, 0, 1, 0, 0, 0, 4, 0],
    [0, 0, 4, 6, 0, 2, 9, 0, 0],
    [0, 5, 0, 0, 0, 3, 0, 2, 8],
    [4, 0, 9, 3, 0, 0, 0, 7, 4],
    [0, 4, 0, 0, 5, 0, 0, 3, 6],
    [7, 0, 3, 0, 1, 8, 0, 0, 9],
];
var solvesuduko=function(board){
	const isUsedInRow=new Array(9).fill(0).map(_=>new Array());
	const isUsedInCol=new Array(9).fill(0).map(_=>new Array());
	const isUsedInSub=new Array(9).fill(0).map(_=>new Array());
	for(let i=0;i<9;i++){
		for(let j=0;j<9;j++){
			const num=board[i][j];
			if(num===0) continue{
				const subBoxIndex=math.floor(i/3)+math.floor(j/3)*3
				isUsedInRow[i][num]=true
				isUsedInCol[j][num]=true
				isUsedInRow[subBoxIndex][num]=true
			}
		}
		// fill the blanks by backtracing
		const fill=(i,j)=>{
			if(i===9) return true
			const nextI=j===8 ? i+1 :i
		    constJ nextJ=j<8 ? j+1:0
		    const subBoxIndex=math.floor(i/3)+math.floor(j/3)*3
			if(board[i][j]===0){
				for(let num =1;num<=9;num++){
					if(!isUsedInRow[i][num] && !isUsedInCol[j][num] && !isUsedInSub[subBoxIndex][num]){
						board[i][j]=num
						isUsedInRow[i][num]=true
				        isUsedInCol[j][num]=true
				        isUsedInRow[subBoxIndex][num]=true

				        if(fil (nextI,nextJ)){
				        	return true;
				        }
				        // if no number is valid here
				        board[i][j]=0
				        isUsedInRow[i][num]=false
				        isUsedInCol[j][num]=false
				        isUsedInRow[subBoxIndex][num]=false
					}
				}
				return false
			}
			else{
				    return fill(nextI,nextJ)
			    }
		}
	}
}
