# N-Queens
## 描述
- 问题描述：在n*n的棋盘上摆n个互不攻击的Queen（国际象棋Queen，可以米字型攻击）,显示排列种类。
- 函数类型：n:int=>[]
## 思路
1. 采用递归、回溯需要找到递归的逻辑，判断Queen可不可以放在x行y列，如果可以则继续执行判断是否可以放置x+1行。否则判断放置y+1列。
2. 使用递归时先判断推出条件。x行判断结束时推出
3. 单行判断为递归单元，符合条件进入下一个递归。<br />

## 实现
```javascript
const solveNQueens = (n) => {
    const result = [];
    const store = [];
    backTracking(n,0,store,result);
    return result;
};

const backTracking = (n,row,store,result)=> {
    if(n === row){
        result.push(arrayToChess(store,n));
    }
    for(let i = 0; i<n; i++){
        store[row] = i;
        if(check(row,i,store)){
            backTracking(n, row+1, store, result)
        }
    }
}

const arrayToChess = (array,n) => {
    const chess = []
    for(let i = 0; i<n; i++){
        let str = '';
        for(let j=0; j<n; j++){
            str +=array[i] === j?'Q':'.';
        }
        chess.push(str);
    }
    return chess;
}

const check = (row,col,store) => {
    for(let i = 0; i<row; i++){
        if(store[i] === col ||
          row ===i + Math.abs(store[i]-col)){
            return false;
        }
    }
    return true
}
```

