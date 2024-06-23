<template>
  <Layout>
    <div class="game-container">
      <canvas ref="snakeCanvas" width="400" height="400"></canvas>
    </div>
    <div class="controls">
      <button @click="startGame">Démarrer le jeu</button>
      <div>Score: {{ score }}</div>
    </div>
  </Layout>
</template>

<script>
export default {
  data() {
    return {
      canvas: null,
      ctx: null,
      snake: [],
      food: {},
      score: 0,
      gameInterval: null,
      direction: '',
      gameSpeed: 100,
    };
  },
  mounted() {
    this.canvas = this.$refs.snakeCanvas;
    this.ctx = this.canvas.getContext('2d');
    document.addEventListener("keydown", this.keyHandler);
  },
  beforeDestroy() {
    document.removeEventListener("keydown", this.keyHandler);
    clearInterval(this.gameInterval);
  },
  methods: {
    startGame() {
      this.resetGame();
      this.gameInterval = setInterval(this.moveSnake, this.gameSpeed);
    },
    resetGame() {
      this.snake = [{ x: 160, y: 160 }, { x: 140, y: 160 }];
      this.generateFood();
      this.score = 0;
      this.direction = 'RIGHT';
      this.gameSpeed = 100;
    },
    generateFood() {
      this.food = {
        x: Math.floor(Math.random() * 17 + 1) * 20,
        y: Math.floor(Math.random() * 15 + 3) * 20
      };
    },
    keyHandler(event) {
      const keyPressed = event.key;
      const oppositeDirections = {
        'ArrowLeft': 'RIGHT',
        'ArrowRight': 'LEFT',
        'ArrowUp': 'DOWN',
        'ArrowDown': 'UP',
      };
      if (keyPressed.includes('Arrow') && this.direction !== oppositeDirections[keyPressed]) {
        this.direction = keyPressed.replace('Arrow', '').toUpperCase();
      }
    },
    moveSnake() {
  let { x: snakeX, y: snakeY } = this.snake[0];
  const moveAmount = 20;

  // Déterminer la nouvelle tête en fonction de la direction
  switch (this.direction) {
    case 'LEFT': snakeX -= moveAmount; break;
    case 'UP': snakeY -= moveAmount; break;
    case 'RIGHT': snakeX += moveAmount; break;
    case 'DOWN': snakeY += moveAmount; break;
  }

  // Faire réapparaître le serpent de l'autre côté s'il sort du canevas
  if (snakeX < 0) {
    snakeX = this.canvas.width - moveAmount;
  } else if (snakeX >= this.canvas.width) {
    snakeX = 0;
  }
  if (snakeY < 0) {
    snakeY = this.canvas.height - moveAmount;
  } else if (snakeY >= this.canvas.height) {
    snakeY = 0;
  }

  const newHead = { x: snakeX, y: snakeY };

  // Vérifier si le serpent se mord la queue
  if (this.snake.some((part, idx) => idx !== 0 && part.x === newHead.x && part.y === newHead.y)) {
    clearInterval(this.gameInterval);
    alert(`Game Over. Your final score was: ${this.score}`);
    this.resetGame();
    return;
  }

  this.snake.unshift(newHead);
  if (snakeX === this.food.x && snakeY === this.food.y) {
    this.score++;
    this.generateFood();
    this.gameSpeed *= 0.95;
    this.updateGameSpeed();
  } else {
    this.snake.pop();
  }

  this.draw();
},

    draw() {
      this.ctx.fillStyle = "lightgreen";
      this.ctx.fillRect(0, 0, this.canvas.width, this.canvas.height);
      this.snake.forEach((part, index) => {
        this.ctx.fillStyle = index === 0 ? "green" : "white";
        this.ctx.fillRect(part.x, part.y, 20, 20);
        this.ctx.strokeStyle = "red";
        this.ctx.strokeRect(part.x, part.y, 20, 20);
      });
      this.ctx.fillStyle = "red";
      this.ctx.fillRect(this.food.x, this.food.y, 20, 20);
    },
    isGameOver(newHead) {
      const { x, y } = newHead;
      return (
        x < 0 || x >= this.canvas.width || y < 0 || y >= this.canvas.height ||
        this.snake.some((part, idx) => idx !== 0 && part.x === x && part.y === y)
      );
    },
    updateGameSpeed() {
      clearInterval(this.gameInterval);
      this.gameInterval = setInterval(this.moveSnake, this.gameSpeed);
    }
  }
}
</script>

<style>
.game-container {
  display: flex;
  justify-content: center;
  margin: 20px 0;
}
.controls {
  text-align: center;
}
button {
  display: inline-block;
  margin: 20px;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}
</style>
