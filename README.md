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
var state = {f: 0, d: 0, a: 0};
document.getElementsByTagName('pre')[0].innerText.split('\n').forEach(el => {
    el = el.trim();
    switch(el.substring(0, 1)) {
        case 'f':
            state.f += +el.slice(-1);
            state.d += state.a * +el.slice(-1);
            break;
        case 'd':
            state.a += +el.slice(-1);
            break;
        case 'u':
            state.a -= +el.slice(-1);
			break;
    }});
console.log(state.f * state.d);
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
