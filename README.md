
let move = setInterval(() => {
  btn.style.left = Math.random() * (window.innerWidth - 120) + "px";
  btn.style.top = Math.random() * (window.innerHeight - 80) + "px";
}, 120);

// wrong touch anywhere
document.body.addEventListener("click", function(e){
  if(e.target.id !== "btn"){
    sound.currentTime = 0;
    sound.play();

    if(navigator.vibrate){
      navigator.vibrate([200,100,200]);
    }

    alert("⚠️ Wrong touch detected!");
  }
});

// correct button click
btn.onclick = function(e){
  e.stopPropagation();

  clearInterval(move);

  sound.pause();

  document.body.innerHTML =
    "<h1 style='color:#00ff00;text-align:center;margin-top:200px'>✔ SYSTEM UNLOCKED</h1>";
};
</script>

</body>
</html>
