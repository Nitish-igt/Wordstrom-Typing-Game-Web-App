const gameArea = document.getElementById("gameArea");
const startBtn = document.getElementById("startBtn");
const pauseBtn = document.getElementById("pauseBtn");
const resetBtn = document.getElementById("resetBtn");
const scoreSpan = document.getElementById("score");
const accuracySpan = document.getElementById("accuracy");
const lettersTypedSpan = document.getElementById("lettersTyped");
const bestScoreSpan = document.getElementById("bestScore");
const gamesPlayedSpan = document.getElementById("gamesPlayed");
const speedInput = document.getElementById("speed");
const speedValue = document.getElementById("speedValue");
const instructionsBtn = document.getElementById("instructionsBtn");
const instructionsModal = document.getElementById("instructionsModal");
const closeInstructions = document.getElementById("closeInstructions");
const gameHistory = document.getElementById("gameHistory");
const toggleSound = document.getElementById("toggleSound");
instructionsBtn.onclick = () => {
  instructionsModal.classList.remove("hidden");
};

closeInstructions.onclick = () => {
  instructionsModal.classList.add("hidden");
};

instructionsModal.onclick = (e) => {
  if (e.target === instructionsModal) {
    instructionsModal.classList.add("hidden");
  }
};


let gameInterval, fallingLetter, isRunning = false, score = 0, lettersTyped = 0, bestScore = 0, gamesPlayed = 0;
let soundEnabled = true;

const getRandomLetter = () => String.fromCharCode(65 + Math.floor(Math.random() * 26));

function startGame() {
  if (isRunning) return;
  isRunning = true;
  fallingLetter = createLetter();
  gameInterval = setInterval(moveLetter, 100);
}

function pauseGame() {
  clearInterval(gameInterval);
  isRunning = false;
}

function resetGame() {
  pauseGame();
  score = 0;
  lettersTyped = 0;
  updateStats();
  if (fallingLetter) fallingLetter.remove();
}

function endGame() {
  if (score > bestScore) bestScore = score;
  gamesPlayed++;
  const accuracy = lettersTyped ? Math.round((score / lettersTyped) * 100) : 0;
  const item = document.createElement("li");
  item.textContent = `Score: ${score}, Accuracy: ${accuracy}%`;
  gameHistory.prepend(item);
  resetGame();
}

function updateStats() {
  scoreSpan.textContent = score;
  lettersTypedSpan.textContent = lettersTyped;
  accuracySpan.textContent = lettersTyped ? `${Math.round((score / lettersTyped) * 100)}%` : "100%";
  bestScoreSpan.textContent = bestScore;
  gamesPlayedSpan.textContent = gamesPlayed;
}

function createLetter() {
  const letter = document.createElement("div");
  letter.className = "absolute text-3xl font-bold";
  letter.textContent = getRandomLetter();
  letter.style.left = `${Math.random() * 90}%`;
  letter.style.top = "0px";
  gameArea.appendChild(letter);
  return letter;
}

function moveLetter() {
  if (!fallingLetter) return;
  const speed = parseInt(speedInput.value) * 2;
  const top = parseInt(fallingLetter.style.top) + speed;
  fallingLetter.style.top = `${top}px`;

  if (top >= gameArea.clientHeight - 30) {
    endGame();
  }
}

document.addEventListener("keydown", (e) => {
  if (!isRunning || !fallingLetter) return;
  lettersTyped++;
  if (e.key.toUpperCase() === fallingLetter.textContent) {
    score++;
    if (soundEnabled) new Audio("https://freesound.org/data/previews/256/256113_3263906-lq.mp3").play();
    fallingLetter.remove();
    fallingLetter = createLetter();
  }
  updateStats();
});

speedInput.addEventListener("input", () => {
  speedValue.textContent = speedInput.value;
});

startBtn.onclick = startGame;
pauseBtn.onclick = pauseGame;
resetBtn.onclick = resetGame;

instructionsBtn.onclick = () => instructionsModal.classList.remove("hidden");
closeInstructions.onclick = () => instructionsModal.classList.add("hidden");

toggleSound.onclick = () => {
  soundEnabled = !soundEnabled;
  toggleSound.textContent = soundEnabled ? "🔊" : "🔇";
};


instructionsModal.onclick = (e) => {
  if (e.target === instructionsModal) {
    instructionsModal.classList.add("hidden");
  }
};
