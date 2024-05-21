# stopwatch
자바스크립트를 이용한 스탑워치 만들기
![Animation](https://github.com/jung-chaewon/stopwatch/assets/131144717/83210c4d-7695-492f-81e1-961def0ab010)

### script
```javascript
  const timerEl = document.getElementById("timer");
const startButtonEl = document.getElementById("start");
const stopButtonEl = document.getElementById("stop");
const resetButtonEl = document.getElementById("reset");

let startTime = 0;
let elapsedTime = 0;
let timerInterval;

function startTimer(){
    startTime = Date.now()-elapsedTime;
    timerInterval = setInterval(() => {
        elapsedTime = Date.now()-startTime;
        timerEl.textContent = formatTime(elapsedTime);
    }, 10);
    startButtonEl.disabled= true;
    stopButtonEl.disabled= false;

}
function formatTime(elapsedTime){
    const milliseconds = Math.floor((elapsedTime%1000)/10);
    const seconds = Math.floor((elapsedTime%(1000*60))/1000);
    const minutes = Math.floor((elapsedTime%(1000*60*60))/(1000*60));
    const hours = Math.floor((elapsedTime/(1000*60*60)));
    return(
        (hours ? (hours > 9 ? hours : "0" + hours):"00") +
        ":"+
        (minutes ? (minutes > 9 ? minutes : "0" + minutes):"00") +
        ":"+
        (seconds ? (seconds > 9 ? seconds : "0" + seconds):"00") +
        "."+
        (milliseconds > 9 ? milliseconds : "0" + milliseconds)

    );
}
function stopTimer() {
    clearInterval(timerInterval);
    startButtonEl.disabled = false;
    startButtonEl.disabled = true;
}
function resetTimer(){
    clearInterval(timerInterval);
    elapsedTime = 0;
    timerEl.textContent = "00:00:00";
    startButtonEl.disabled = false;
    stopButtonEl.disabled = true;
}
startButtonEl.addEventListener("click",startTimer);
stopButtonEl.addEventListener("click",stopTimer);
resetButtonEl.addEventListener("click",resetTimer);
```
