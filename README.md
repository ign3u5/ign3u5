### Hi there 👋

# Advent of Code
## Day 2
### Task 1
```javascript
console.log(Object.values(document.getElementsByTagName('pre')[0].innerText.split('\n').reduce((acc, el) => {
    switch (el.substring(0, 1)) {
        case 'f':
			acc.f += +el.slice(-1);
			break;
        case 'd':
			acc.d += +el.slice(-1);
            break;
        case 'u':
			acc.d -= +el.slice(-1);
			break;
    };
return acc;}, {f:0,d:0})).reduce((acc, el) => acc * el));
```
### Task 2
```javascript
console.log(Object.values(document.getElementsByTagName('pre')[0].innerText.split('\n').reduce((acc, el) => {
    switch (el.substring(0, 1)) {
        case 'f':
			acc.f += +el.slice(-1);
            acc.d += +el.slice(-1) * acc.a;
			break;
        case 'd':
			acc.a += +el.slice(-1);
            break;
        case 'u':
			acc.a -= +el.slice(-1);
			break;
    };
return acc;}, {f:0,d:0,a:0})).reduce((acc, el, i) => i < 2 ? acc * el : acc));
```

## Day 3
### Task 2
```javascript
var rawInput = document.getElementsByTagName('pre')[0].innerText.split('\n').map(el => Array.from(el));
var validate = (arr, i, pref) => !(arr.length - 1) ? parseInt(arr[0].reduce((acc, el) => acc += el, ''), 2) : validate(arr.filter(el => +el[i] == pref(arr.reduce((acc, el) => acc + +el[i], 0) >= arr.length / 2)), ++i, pref);
validate(rawInput, 0, b => b ? 1 : 0) * validate(rawInput, 0, b => b ? 0 : 1);
```

## Day 4
### Task 1
```javascript
var rawInput = document.getElementsByTagName('pre')[0].innerText.split('\n\n').map(el => el.split('\n')).map(el => el.map(x => x.split(' ').filter(n => n != '')));
var listOfNumbers = rawInput.splice(0, 1)[0][0][0].split(',');
rawInput = rawInput.map(el => el.map(x => x.map(t => ({n: t, c: false}))));
rawInput[99].splice(5, 1);

var getResult = () => {
for (const num of listOfNumbers) {
    mark(rawInput, num);
    var result = checkForBingo(rawInput, num);
    if (result != -1) {
        return result;
    }
}; return -1;};

var mark = (arr, num) => {
    arr.forEach(el => el.forEach(x => x.forEach(n => +n.n == +num ? n.c = true : n.c)));
}

var checkForBingo = (arr, n) => {
    var winningGridIndex = -1;
    arr.forEach((el, i) => checkHorizontal(el) || checkVertical(el) ? winningGridIndex = i : winningGridIndex);
    if (winningGridIndex != -1) {
        var filteredArrays = arr[winningGridIndex].flatMap(el => el.filter(x => !x.c));
        var totalFalseValues = filteredArrays.reduce((acc, el) => acc + +el.n, 0);
        var result = totalFalseValues * +n;
        return result;
    }
    return winningGridIndex;
}

var checkHorizontal = (grid) => {
    for (const line of grid) {
        if (!line.some(x => !x.c)) {
            return true;
        }
    }
    return false;
}

var checkVertical = (grid) => {
    for (var i = 0; i < grid.length; i++) {
        var lineResult = true;
        for (var l = 0; l < grid.length; l++) {
            if (!grid[l][i].c) {
                lineResult = false;
                break;
            }
        }
        if (lineResult) {
            return true;
        }
    }
    return false;
}

getResult();
```

<!--
**ign3u5/ign3u5** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
