# gitTest1
this is just for learning git.
let numbers = new Set();

document.querySelectorAll('span[title]').forEach(el => {
    let text = el.getAttribute('title');
    if (text && text.match(/\+?\d{10,15}/)) {
        numbers.add(text);
    }
});

console.log([...numbers].join('\n'));