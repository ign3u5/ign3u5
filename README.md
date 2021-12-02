### Hi there 👋

### Advent of Code
Day 2:  
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
