let generoSelect, humorSelect, botao;
let filmes = [];
let recomendacao = '';

function preload() {
  // Simulação de base de dados
  filmes = [
    { titulo: "A Origem", genero: "Ação", humor: "Sério" },
    { titulo: "Divertida Mente", genero: "Animação", humor: "Leve" },
    { titulo: "Deadpool", genero: "Ação", humor: "Cômico" },
    { titulo: "Clube da Luta", genero: "Drama", humor: "Sério" },
    { titulo: "Toy Story", genero: "Animação", humor: "Leve" },
    {titulo: "Terra doi nunca", genero: "Animação", humor: "Leve"}
  ];
}

function setup() {
  createCanvas(600, 400);
  textAlign(CENTER);
  textSize(16);

  generoSelect = createSelect();
  generoSelect.position(50, 50);
  generoSelect.option('Ação');
  generoSelect.option('Animação');
  generoSelect.option('Drama');

  humorSelect = createSelect();
  humorSelect.position(200, 50);
  humorSelect.option('Sério');
  humorSelect.option('Leve');
  humorSelect.option('Cômico');

  botao = createButton('Recomendar Filme');
  botao.position(400, 50);
  botao.mousePressed(recomendarFilme);
}

function recomendarFilme() {
  let genero = generoSelect.value();
  let humor = humorSelect.value();

  let filtrados = filmes.filter(f => f.genero === genero && f.humor === humor);

  if (filtrados.length > 0) {
    let sorteado = random(filtrados);
    recomendacao = "🎬 Recomendação: " + sorteado.titulo;
  } else {
    recomendacao = "😕 Nenhum filme encontrado com esses critérios.";
  }
}

function draw() {
  background(240);
  fill(0);
  text("Escolha suas preferências:", width / 2, 20);
  text(recomendacao, width / 2, 150);
}
