Olá, me chamo Davi e iniciei minha jornada com a proramação em 2022

![Fraga GitHub stats](https://github-readme-stats.vercel.app/api?username=Dav1Samu3l&show_icons=true&theme=dracula&count_private=true)


![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=Dav1Samu3l&layout=compact)



## Tecnologias que eu uso no meu dia

<div style="display: inline_block">
  <img align="center" alt="html5" src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" />
  <img align="center" alt="css" src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white" />
 <img align="center" alt="js" src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" />
 <img align="center" alt="react" src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" />
  <img align="center" alt="nodejs" src="https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white" />
</div><br/>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Snake</title>
    <link rel="stylesheet" href="style.css">
    <style>
.wrapper {
  position: relative;
  width: 100%;
  height: 100%;
  overflow: hidden;
  background-color: #1e2327;
}
.snake-wrapper {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  transform: translateX(-100%);
}
.snake {
  position: absolute;
  width: 0.4rem;
  height: 0.4rem;
  background-color: #9be9a8;
  border-radius: 50%;
}
    </style>
  </head>
  <body>
    <div class="wrapper">
      <div class="snake-wrapper">
        <div class="snake"></div>
      </div>
    </div>
    <script src="script.js"></script>
    <script>
     const colors = ['#9be9a8', '#40c463', '#30a14e', '#216e39'];

const getRandomColor = () => {
  const index = Math.floor(Math.random() * colors.length);
  return colors[index];
};

const getRange = (start, end) => {
  return Array.from({length: end - start}, (_, i) => i + start);
};

const getPoints = () => {
  const points = [];
  const xRange = getRange(1, 53);
  const yRange = getRange(1, 7);
  yRange.forEach(y => {
    const xs = y % 2 === 0 ? xRange.reverse() : xRange;
    xs.forEach(x => {
      points.push({x, y});
    });
  });
  return points;
};

const drawSnake = () => {
  const points = getPoints();
  const snakeEl = document.querySelector('.snake');
  let index = 0;
  const intervalId = setInterval(() => {
    if (index >= points.length) {
      clearInterval(intervalId);
      return;
    }
    const {x, y} = points[index];
    const color = getRandomColor();
    const left = `${x * 10}px`;
    const top = `${y * 10}px`;
    const style = `background-color: ${color}; left: ${left}; top: ${top};`;
    snakeEl.setAttribute('style', style);
    index++;
  }, 20);
};

drawSnake();

    </script>
  </body>
</html>
