function sellBlook(blookname, amt) {
  $.post("/worker/blook/sellblook.php", `blook=${blookname}&amount=${amt}`, (res) => {});
}

for (let i = 0; i <= window.maxID; i++) {
  $.get(`/worker/misc/getblook.php?id=${i}`, (res) => {
    $.get(`/worker/blook/getuserblook.php?blook=${res.split('|')[0].replace(/\s/g, '')}`, (res2) => {
      if (Number.parseInt(res2) === 0 || Number.parseInt(res2) === 1 || res2.toString() === 'NO BLOOK') return
      qnt = Number.parseInt(res2) - 1;
      sellBlook(res.split('|')[0].replace(/\s/g, ''), qnt);
      console.log(`[sellDupes.js] Selling ${qnt} ${qnt <= 1 ? `${res.split('|')[0].replace(/\s/g, '')}` : `${res.split('|')[0].replace(/\s/g, '')}s`}`);
    })
  })
}
