# Valid Sudoku
## 描述
## 细节介绍 

## 实现
```javascript
var isValidSudoku = function(board) {
    let intMap = {};
    for(let x = 0,xLen = board.length;x<xLen;x++){
        let boardRow = board[x];
        for(let y= 0,yLen = board[x].length;y<yLen;y++){
            let int = boardRow[y];
            if(int === '.')continue;
            let extent = get3X3Extent(x,y);            
            if(!intMap[int]){
                intMap[int] = [[x,y]];
            } else {
                for(let i = 0,len=intMap[int].length;i<len;i++){
                    let existInt = intMap[int][i];
                    if(existInt[0] === x || existInt[1] === y || //同行或同列
                      //3*3
                     (existInt[0]>=extent[0] && existInt[0]<=extent[2]) && (existInt[1]>=extent[1] && existInt[1]<=extent[3])){
                    return false;
                    }     
                }
                intMap[int].push([x,y]);
            }      
        }
    }
    return true;
};

var get3X3Extent = function(x,y){
    
    let restX = Math.floor(x/3);    
    let restY = Math.floor(y/3);
    return [restX*3,restY*3,(restX+1)*3-1,(restY+1)*3-1];
}
```

