<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Transformer Model Visualization</title>
<style>
  rect:hover { fill: #ffeb3b; cursor: pointer; }
  .tooltip { position: absolute; background-color: white; border: 1px solid black; padding: 5px; display: none; }
</style>
</head>
<body>

<svg id="transformer-diagram" width="1000" height="600" xmlns="http://www.w3.org/2000/svg">
  <!-- Components -->
  <rect x="50" y="100" width="120" height="40" fill="#f3c6c6" stroke="black" data-description="Input Embedding transforms input tokens into vectors."></rect>
  <text x="60" y="125" font-size="12">Input Embedding</text>
  
  <line x1="170" y1="120" x2="200" y2="120" stroke="black" stroke-width="2" marker-end="url(#arrow)"/>
  
  <rect x="200" y="100" width="120" height="40" fill="#b2d6d8" stroke="black" data-description="Positional Encoding adds position information."></rect>
  <text x="210" y="125" font-size="12">Positional Encoding</text>

  <!-- Arrow Marker -->
  <defs>
    <marker id="arrow" markerWidth="10" markerHeight="10" refX="0" refY="3" orient="auto">
      <path d="M0,0 L0,6 L9,3 z" fill="black"/>
    </marker>
  </defs>
</svg>

<div class="tooltip" id="tooltip"></div>

<script>
  const svg = document.getElementById('transformer-diagram');
  const tooltip = document.getElementById('tooltip');

  svg.addEventListener('mouseover', (event) => {
    const target = event.target;
    if (target.tagName === 'rect') {
      tooltip.innerText = target.getAttribute('data-description');
      tooltip.style.display = 'block';
    }
  });

  svg.addEventListener('mousemove', (event) => {
    tooltip.style.left = `${event.pageX + 10}px`;
    tooltip.style.top = `${event.pageY + 10}px`;
  });

  svg.addEventListener('mouseout', () => {
    tooltip.style.display = 'none';
  });
</script>

</body>
</html>
