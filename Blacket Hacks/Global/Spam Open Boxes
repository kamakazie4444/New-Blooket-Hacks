let i = 0;
const colors = {
  Divine: 'violet',
  Mystical: 'plum',
  Perfect: 'lemonchiffon',
  Chroma: 'skyblue',
  Legendary: 'gold',
  Epic: 'red',
  Rare: 'blue',
  Uncommon: 'lime'
}

let zename = prompt("Which box would you like to open?");
let amt = Number(prompt(`How many of the ${zename} Box would you like to open?\ntype "*" to unlock all possible with your current tokens.`));
if (isNaN(amt)) amt = Number.MAX_VALUE

function buyBox(name) {
  $.post('/worker/box/openbox.php', `box=${name}`, function(data) {
    if (data === 'You\'re being rate limited.') return
    if (data.includes("rate")) i--;
    console.log('%c%s', `color: white; font-size: 25px; text-shadow: 0px 0px 15px ${colors[data.split('|')[1]]}`, `${data.split('|')[0]}`);
    updateTokens();
  });
}

var check = setInterval(() => {
    if (i <= amt) {
        buyBox(zename);
        i++;
    } else {
        clearInterval(check);
        alert("Done buying boxes!\nCheck the Blooks page or the Console for your results.");
    }
}, 751);
