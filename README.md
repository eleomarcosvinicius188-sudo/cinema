# cinema

<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#101010">
  <title>CINEWEB | Seu universo de cinema</title>
  <link rel="stylesheet" href="cine.css">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;700&family=Playfair+Display:wght@700;800&display=swap" rel="stylesheet">
  <script src="javas.js" defer></script>
</head>
<body>

  <header class="topbar">
    <a href="#" class="logo">CINE<span>WEB</span><i>®</i></a>

    <nav>
      <a href="#inicio">Início</a>
      <a href="#catalogo">Filmes</a>
      <button id="verFavoritos" class="nav-fav">
        ♥ Favoritos <span id="contadorFavoritos">0</span>
      </button>
    </nav>
  </header>

  <main>
    <section class="hero" id="inicio">
      <div class="hero-content">
        <span class="eyebrow">SUA PRÓXIMA HISTÓRIA COMEÇA AQUI</span>
        <h1>O mundo é seu.<br><span>Aperte o play.</span></h1>
        <p>
          Grandes histórias, universos inesquecíveis e personagens
          que ficam com você muito depois dos créditos.
        </p>
        <a href="#catalogo" class="btn-primary">EXPLORAR FILMES ↗</a>
        <div class="hero-note">✦ DESCUBRA · ESCOLHA · ASSISTA</div>
      </div>
      <div class="hero-decoration">
        <div class="orbit orbit-one"></div>
        <div class="orbit orbit-two"></div>
        <div class="film-symbol">C<span>W</span></div>
        <span class="decoration-text">A ARTE DE CONTAR HISTÓRIAS</span>
      </div>
    </section>

    <section class="catalog" id="catalogo">
      <div class="section-heading">
        <div>
          <span class="eyebrow">NOSSO CATÁLOGO</span>
          <h2>Encontre seu próximo <span>favorito.</span></h2>
        </div>
        <span class="catalog-label">CINEWEB COLLECTION</span>
      </div>

      <div class="search-area">
        <label class="search-box">
          <span>⌕</span>
          <input
            type="search"
            id="pesquisa"
            placeholder="Pesquisar título ou gênero..."
            aria-label="Pesquisar filmes"
          >
          <button id="limparPesquisa" aria-label="Limpar pesquisa">✕</button>
        </label>

        <select id="ordenacao" aria-label="Ordenar filmes">
          <option value="padrao">Em destaque</option>
          <option value="nota">Melhor avaliação</option>
          <option value="titulo">Ordem alfabética</option>
        </select>
      </div>

      <div class="filters" id="filtros">
        <button class="filter active" data-genero="Todos">Todos</button>
        <button class="filter" data-genero="Ação">Ação</button>
        <button class="filter" data-genero="Comédia">Comédia</button>
        <button class="filter" data-genero="Romance">Romance</button>
        <button class="filter" data-genero="Terror">Terror</button>
        <button class="filter" data-genero="Ficção científica">Ficção científica</button>
        <button class="filter" data-genero="Aventura">Aventura</button>
      </div>

      <div class="results-line">
        <span id="resultadoTexto">Carregando filmes...</span>
        <span>✦ ESCOLHIDOS PARA VOCÊ</span>
      </div>

      <div class="movie-grid" id="listaFilmes"></div>

      <div id="mensagemVazia" class="empty-state" hidden>
        <span>🎬</span>
        <h3>Nenhum filme encontrado</h3>
        <p>Tente outro título ou escolha uma categoria diferente.</p>
        <button class="btn-primary" id="resetar">VER TODOS OS FILMES</button>
      </div>
    </section>

    <section class="quote-section">
      <span class="quote-mark">“</span>
      <p>O cinema é uma forma de sonhar<br>com os olhos abertos.</p>
      <span class="eyebrow">CINEWEB · TECNOLOGIA, CINEMA E ARTE</span>
    </section>
  </main>

  <footer>
    <a href="#inicio" class="logo">CINE<span>WEB</span><i>®</i></a>
    <p>Uma experiência criada com HTML, CSS e JavaScript.</p>
    <span>© 2026 CINEWEB — PROJETO ESCOLAR</span>
  </footer>

  <dialog id="modalFilme" class="movie-modal">
    <button class="close-modal" id="fecharModal" aria-label="Fechar">✕</button>
    <div id="detalhesFilme"></div>
  </dialog>

  <div id="notificacao" class="toast" role="status" aria-live="polite"></div>

</body>
</html>



:root {
  --bg: #101010;
  --surface: #191919;
  --surface-light: #242424;
  --red: #f04444;
  --red-dark: #c92e35;
  --white: #f7f4f0;
  --muted: #a4a09e;
  --border: rgba(255, 255, 255, 0.10);
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
  scroll-padding-top: 90px;
}

body {
  background: var(--bg);
  color: var(--white);
  font-family: "DM Sans", sans-serif;
  line-height: 1.6;
}

button, input, select {
  font: inherit;
}

button, a, select {
  -webkit-tap-highlight-color: transparent;
}

a {
  color: inherit;
  text-decoration: none;
}

button {
  cursor: pointer;
}

button:focus-visible,
a:focus-visible,
input:focus-visible,
select:focus-visible {
  outline: 2px solid var(--red);
  outline-offset: 4px;
}

.topbar {
  min-height: 76px;
  padding: 16px 7%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 20px;
  border-bottom: 1px solid var(--border);
  background: #101010;
  position: sticky;
  top: 0;
  z-index: 10;
}

.logo {
  font-size: 25px;
  font-weight: 800;
  letter-spacing: -1.5px;
}

.logo span {
  color: var(--red);
}

.logo i {
  font-size: 9px;
  vertical-align: top;
  margin-left: 3px;
}

.topbar nav {
  display: flex;
  align-items: center;
  gap: 30px;
  font-size: 13px;
  color: var(--muted);
}

.topbar nav a:hover {
  color: white;
}

.nav-fav {
  background: transparent;
  color: white;
  border: 1px solid var(--border);
  border-radius: 30px;
  padding: 9px 15px;
}

.nav-fav span {
  color: var(--red);
  font-weight: 700;
  margin-left: 5px;
}

.hero {
  min-height: 470px;
  padding: 85px 10%;
  position: relative;
  overflow: hidden;
  display: flex;
  align-items: center;
  background:
    radial-gradient(ellipse at 78% 40%, rgba(240, 68, 68, .15), transparent 38%),
    linear-gradient(110deg, #151515, #101010 70%);
  border-bottom: 1px solid var(--border);
}

.hero-content {
  max-width: 620px;
  position: relative;
  z-index: 2;
}

.eyebrow {
  color: var(--red);
  font-size: 10px;
  font-weight: 700;
  letter-spacing: 3px;
}

h1, h2, .quote-section p {
  font-family: "Playfair Display", Georgia, serif;
}

.hero h1 {
  font-size: clamp(42px, 6vw, 70px);
  line-height: 1.08;
  margin: 20px 0;
  letter-spacing: -2px;
}

.hero h1 span,
.section-heading h2 span {
  color: var(--red);
}

.hero-content > p {
  color: var(--muted);
  max-width: 460px;
  font-size: 14px;
  margin-bottom: 28px;
}

.btn-primary {
  display: inline-flex;
  justify-content: center;
  align-items: center;
  background: var(--red);
  color: white;
  padding: 13px 22px;
  border: none;
  border-radius: 3px;
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 1px;
  transition: .2s;
}

.btn-primary:hover {
  background: var(--red-dark);
  transform: translateY(-2px);
}

.hero-note {
  margin-top: 30px;
  color: #888;
  font-size: 9px;
  letter-spacing: 2px;
}

.hero-decoration {
  position: absolute;
  width: 370px;
  height: 370px;
  right: 9%;
  top: 50%;
  transform: translateY(-50%);
  display: grid;
  place-items: center;
}

.orbit {
  position: absolute;
  width: 100%;
  height: 100%;
  border: 1px solid rgba(240, 68, 68, .25);
  border-radius: 50%;
}

.orbit-one {
  transform: rotateX(65deg) rotate(-25deg);
}

.orbit-two {
  transform: rotateY(65deg) rotate(25deg);
}

.film-symbol {
  width: 155px;
  height: 155px;
  border: 2px solid var(--red);
  color: white;
  border-radius: 50%;
  display: grid;
  place-items: center;
  font-family: Georgia, serif;
  font-size: 75px;
  font-weight: 700;
  box-shadow: 0 0 75px rgba(240, 68, 68, .12);
}

.film-symbol span {
  color: var(--red);
}

.decoration-text {
  position: absolute;
  bottom: 12px;
  font-size: 9px;
  letter-spacing: 3px;
  color: var(--muted);
}

.catalog {
  padding: 75px 8%;
  max-width: 1500px;
  margin: auto;
}

.section-heading {
  display: flex;
  justify-content: space-between;
  align-items: end;
  gap: 20px;
  margin-bottom: 28px;
}

.section-heading h2 {
  font-size: clamp(27px, 3.5vw, 39px);
  line-height: 1.3;
  margin-top: 9px;
}

.catalog-label {
  font-size: 9px;
  color: var(--muted);
  letter-spacing: 2px;
  padding-bottom: 7px;
}

.search-area {
  display: flex;
  gap: 12px;
  margin-bottom: 20px;
}

.search-box {
  flex: 1;
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 0 15px;
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 4px;
}

.search-box > span {
  font-size: 25px;
  color: var(--red);
}

.search-box input {
  min-width: 0;
  width: 100%;
  background: transparent;
  border: none;
  outline: none;
  color: white;
  padding: 14px 0;
  font-size: 12px;
}

.search-box input::placeholder {
  color: #898989;
}

.search-box button {
  border: none;
  background: transparent;
  color: var(--muted);
  padding: 6px;
}

#ordenacao {
  background: var(--surface);
  color: white;
  border: 1px solid var(--border);
  padding: 0 12px;
  border-radius: 4px;
  font-size: 11px;
}

.filters {
  display: flex;
  gap: 9px;
  flex-wrap: wrap;
  margin-bottom: 30px;
}

.filter {
  color: #bbb;
  border: 1px solid var(--border);
  background: transparent;
  border-radius: 30px;
  padding: 8px 17px;
  font-size: 11px;
  transition: .2s;
}

.filter:hover,
.filter.active {
  background: var(--red);
  border-color: var(--red);
  color: white;
}

.results-line {
  display: flex;
  justify-content: space-between;
  gap: 12px;
  margin-bottom: 20px;
  color: var(--muted);
  font-size: 10px;
}

.results-line span:last-child {
  letter-spacing: 1.5px;
}

.movie-grid {
  display: grid;
  grid-template-columns: repeat(5, minmax(0, 1fr));
  gap: 26px 17px;
}

.movie-card {
  min-width: 0;
  animation: appear .4s ease both;
}

.poster-wrap {
  position: relative;
  overflow: hidden;
  aspect-ratio: 2 / 3;
  background: var(--surface);
  border-radius: 5px;
  margin-bottom: 13px;
}

.poster {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform .4s;
}

.movie-card:hover .poster {
  transform: scale(1.06);
}

.poster-placeholder {
  display: grid;
  place-items: center;
  width: 100%;
  height: 100%;
  background: linear-gradient(145deg, #363030, #171717);
  color: var(--red);
  font-family: Georgia, serif;
  font-size: 55px;
}

.movie-rating {
  position: absolute;
  top: 10px;
  left: 10px;
  background: rgba(0, 0, 0, .82);
  border: 1px solid var(--border);
  padding: 4px 8px;
  border-radius: 3px;
  font-size: 11px;
}

.favorite-btn {
  position: absolute;
  top: 9px;
  right: 9px;
  width: 34px;
  height: 34px;
  border: 1px solid rgba(255, 255, 255, .2);
  border-radius: 50%;
  background: rgba(0, 0, 0, .75);
  color: white;
  font-size: 18px;
  transition: .2s;
}

.favorite-btn:hover,
.favorite-btn.is-favorite {
  color: var(--red);
  border-color: var(--red);
}

.details-btn {
  position: absolute;
  bottom: 12px;
  left: 10px;
  right: 10px;
  background: var(--red);
  border: none;
  border-radius: 3px;
  padding: 10px 5px;
  color: white;
  font-size: 10px;
  font-weight: 700;
  opacity: 0;
  transform: translateY(8px);
  transition: .2s;
}

.movie-card:hover .details-btn,
.details-btn:focus-visible {
  opacity: 1;
  transform: translateY(0);
}

.movie-genre {
  color: var(--red);
  font-size: 9px;
  letter-spacing: 1px;
  text-transform: uppercase;
}

.movie-title {
  font-size: 15px;
  margin: 4px 0;
  line-height: 1.4;
}

.movie-year {
  color: var(--muted);
  font-size: 11px;
}

.empty-state {
  text-align: center;
  padding: 65px 15px;
}

.empty-state > span {
  font-size: 45px;
}

.empty-state h3 {
  margin: 12px 0 5px;
}

.empty-state p {
  color: var(--muted);
  font-size: 13px;
  margin-bottom: 20px;
}

.quote-section {
  text-align: center;
  padding: 65px 20px 75px;
  background: #171414;
  border-top: 1px solid var(--border);
  border-bottom: 1px solid var(--border);
}

.quote-mark {
  display: block;
  color: var(--red);
  font-family: Georgia, serif;
  font-size: 65px;
  height: 55px;
}

.quote-section p {
  font-size: clamp(25px, 4vw, 37px);
  line-height: 1.4;
  margin: 10px 0 22px;
}

footer {
  padding: 28px 8%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 18px;
  flex-wrap: wrap;
}

footer p,
footer > span {
  font-size: 10px;
  color: var(--muted);
}

.movie-modal {
  position: fixed;
  inset: 0;
  margin: auto;
  width: min(680px, calc(100% - 30px));
  max-height: 85vh;
  overflow-y: auto;
  border: 1px solid #444;
  border-radius: 8px;
  background: #181818;
  color: white;
  padding: 30px;
}

.movie-modal::backdrop {
  background: rgba(0, 0, 0, .82);
  backdrop-filter: blur(5px);
}

.close-modal {
  display: block;
  margin-left: auto;
  width: 34px;
  height: 34px;
  border-radius: 50%;
  background: #292929;
  color: white;
  border: 1px solid var(--border);
  font-size: 16px;
}

.modal-layout {
  display: grid;
  grid-template-columns: 160px 1fr;
  gap: 25px;
  align-items: start;
  margin-top: 12px;
}

.modal-poster {
  width: 100%;
  aspect-ratio: 2 / 3;
  object-fit: cover;
  border-radius: 4px;
}

.modal-info h2 {
  font-family: "Playfair Display", Georgia, serif;
  font-size: 29px;
  line-height: 1.2;
  margin: 10px 0;
}

.modal-info p {
  color: #c0c0c0;
  font-size: 13px;
  margin: 13px 0;
}

.modal-meta {
  color: var(--red);
  font-size: 11px;
}

.toast {
  position: fixed;
  bottom: 24px;
  left: 50%;
  transform: translate(-50%, 20px);
  background: #282828;
  color: white;
  border: 1px solid #444;
  padding: 12px 20px;
  border-radius: 6px;
  font-size: 12px;
  z-index: 30;
  opacity: 0;
  pointer-events: none;
  transition: .25s;
}

.toast.show {
  opacity: 1;
  transform: translate(-50%, 0);
}

[hidden] {
  display: none !important;
}

@keyframes appear {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (max-width: 1050px) {
  .movie-grid {
    grid-template-columns: repeat(4, minmax(0, 1fr));
  }

  .hero-decoration {
    right: -80px;
    opacity: .5;
  }
}

@media (max-width: 750px) {
  .topbar {
    padding: 14px 5%;
  }

  .topbar nav {
    gap: 13px;
    font-size: 11px;
  }

  .topbar nav > a {
    display: none;
  }

  .hero {
    padding: 75px 7%;
    min-height: 440px;
  }

  .hero-decoration {
    right: -170px;
    opacity: .25;
  }

  .catalog {
    padding: 55px 5%;
  }

  .movie-grid {
    grid-template-columns: repeat(3, minmax(0, 1fr));
    gap: 23px 12px;
  }

  .section-heading {
    align-items: start;
  }

  .catalog-label {
    display: none;
  }

  .details-btn {
    opacity: 1;
    transform: none;
    font-size: 9px;
    padding: 8px 2px;
  }
}

@media (max-width: 480px) {
  .movie-grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 25px 14px;
  }

  .search-area {
    flex-direction: column;
  }

  #ordenacao {
    min-height: 42px;
  }

  .section-heading h2 {
    font-size: 27px;
  }

  .modal-layout {
    grid-template-columns: 105px 1fr;
    gap: 15px;
  }

  .movie-modal {
    padding: 18px;
  }

  .modal-info h2 {
    font-size: 22px;
  }

  footer {
    flex-direction: column;
    align-items: flex-start;
  }
}

@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    scroll-behavior: auto !important;
    animation-duration: .01ms !important;
    transition-duration: .01ms !important;
  }
}

const filmes = [
  {
    id: 1,
    titulo: "Além do Horizonte",
    genero: "Aventura",
    ano: 2025,
    nota: 9.2,
    imagem: "https://images.unsplash.com/photo-1464822759023-fed622ff2c3b?auto=format&fit=crop&w=600&q=80",
    sinopse: "Uma jovem exploradora parte em uma jornada por montanhas desconhecidas para encontrar uma cidade perdida. No caminho, descobre que a maior aventura é conhecer a si mesma.",
    elenco: "Luna Martins, Caio Mendes"
  },
  {
    id: 2,
    titulo: "Risos em Dobro",
    genero: "Comédia",
    ano: 2024,
    nota: 8.5,
    imagem: "https://images.unsplash.com/photo-1527224857830-43a7acc85260?auto=format&fit=crop&w=600&q=80",
    sinopse: "Dois amigos completamente diferentes precisam organizar o maior festival da cidade. Entre confusões e ideias absurdas, eles descobrem o verdadeiro valor da amizade.",
    elenco: "Bia Costa, Pedro Lima"
  },
  {
    id: 3,
    titulo: "Entre Nós",
    genero: "Romance",
    ano: 2025,
    nota: 9.0,
    imagem: "https://images.unsplash.com/photo-1516589178581-6cd7833ae3b2?auto=format&fit=crop&w=600&q=80",
    sinopse: "Dois desconhecidos se encontram por acaso em uma pequena livraria e começam a trocar cartas anônimas. O destino prepara uma surpresa para os dois.",
    elenco: "Clara Alves, Rafael Nunes"
  },
  {
    id: 4,
    titulo: "A Casa Silenciosa",
    genero: "Terror",
    ano: 2023,
    nota: 8.7,
    imagem: "https://images.unsplash.com/photo-1518709268805-4e9042af9f23?auto=format&fit=crop&w=600&q=80",
    sinopse: "Uma família se muda para uma mansão isolada onde todos os relógios pararam à meia-noite. A cada noite, um novo segredo aparece nas paredes da casa.",
    elenco: "Marina Rocha, André Freitas"
  },
  {
    id: 5,
    titulo: "Órbita Zero",
    genero: "Ficção científica",
    ano: 2026,
    nota: 9.5,
    imagem: "https://images.unsplash.com/photo-1446776811953-b23d57bd21aa?auto=format&fit=crop&w=600&q=80",
    sinopse: "No futuro, uma equipe de astronautas recebe um sinal vindo de uma região desconhecida do universo. A descoberta pode mudar tudo o que a humanidade sabe sobre a vida.",
    elenco: "Davi Torres, Elisa Prado"
  },
  {
    id: 6,
    titulo: "Código Vermelho",
    genero: "Ação",
    ano: 2025,
    nota: 8.9,
    imagem: "https://images.unsplash.com/photo-1519608487953-e999c86e7455?auto=format&fit=crop&w=600&q=80",
    sinopse: "Uma especialista em segurança digital descobre uma conspiração capaz de colocar milhares de pessoas em perigo. Agora, ela tem poucas horas para impedir o plano.",
    elenco: "Lucas Barros, Nina Duarte"
  },
  {
    id: 7,
    titulo: "O Último Reino",
    genero: "Aventura",
    ano: 2024,
    nota: 8.8,
    imagem: "https://images.unsplash.com/photo-1518709594023-6eab9bab7b23?auto=format&fit=crop&w=600&q=80",
    sinopse: "Um aprendiz de guerreiro precisa atravessar terras mágicas para recuperar um artefato capaz de salvar seu povo de uma antiga maldição.",
    elenco: "Miguel Azevedo, Sofia Reis"
  },
  {
    id: 8,
    titulo: "Encontro Marcado",
    genero: "Romance",
    ano: 2023,
    nota: 8.2,
    imagem: "https://images.unsplash.com/photo-1470252649378-9c29740c9fa8?auto=format&fit=crop&w=600&q=80",
    sinopse: "Depois de se conhecerem em uma estação de trem, dois artistas passam a se encontrar todos os anos no mesmo lugar. Cada encontro muda o rumo de suas vidas.",
    elenco: "Laura Melo, Bruno Castro"
  },
  {
    id: 9,
    titulo: "A Última Risada",
    genero: "Comédia",
    ano: 2025,
    nota: 7.9,
    imagem: "https://images.unsplash.com/photo-1485846234645-a62644f84728?auto=format&fit=crop&w=600&q=80",
    sinopse: "Um aspirante a comediante entra por engano em uma competição profissional. Sem experiência, ele precisará improvisar para conquistar o público.",
    elenco: "Felipe Souza, Júlia Ramos"
  },
  {
    id: 10,
    titulo: "Sombras da Noite",
    genero: "Terror",
    ano: 2024,
    nota: 8.6,
    imagem: "https://images.unsplash.com/photo-1509248961158-e54f6934749c?auto=format&fit=crop&w=600&q=80",
    sinopse: "Uma estudante começa a receber mensagens de uma pessoa desaparecida há vinte anos. As pistas a conduzem a um mistério escondido em sua própria cidade.",
    elenco: "Alice Mendes, Thiago Vieira"
  }
];

// Estado da aplicação
let generoAtual = "Todos";
let mostrandoFavoritos = false;
let favoritos = new Set();
let filmeSelecionado = null;
let temporizadorToast;

// Elementos da página
const listaFilmes = document.getElementById("listaFilmes");
const pesquisa = document.getElementById("pesquisa");
const ordenacao = document.getElementById("ordenacao");
const filtros = document.getElementById("filtros");
const contadorFavoritos = document.getElementById("contadorFavoritos");
const resultadoTexto = document.getElementById("resultadoTexto");
const mensagemVazia = document.getElementById("mensagemVazia");
const modal = document.getElementById("modalFilme");
const detalhesFilme = document.getElementById("detalhesFilme");
const notificacao = document.getElementById("notificacao");

// Mensagens temporárias
function mostrarMensagem(texto) {
  clearTimeout(temporizadorToast);
  notificacao.textContent = texto;
  notificacao.classList.add("show");

  temporizadorToast = setTimeout(() => {
    notificacao.classList.remove("show");
  }, 2500);
}

// Atualiza o catálogo conforme as escolhas do usuário
function renderizarFilmes() {
  const termo = pesquisa.value.trim().toLocaleLowerCase("pt-BR");

  let encontrados = filmes.filter(filme => {
    const correspondePesquisa =
      filme.titulo.toLocaleLowerCase("pt-BR").includes(termo) ||
      filme.genero.toLocaleLowerCase("pt-BR").includes(termo) ||
      filme.sinopse.toLocaleLowerCase("pt-BR").includes(termo);

    const correspondeGenero =
      generoAtual === "Todos" || filme.genero === generoAtual;

    const correspondeFavorito =
      !mostrandoFavoritos || favoritos.has(filme.id);

    return correspondePesquisa &&
      correspondeGenero &&
      correspondeFavorito;
  });

  if (ordenacao.value === "nota") {
    encontrados.sort((a, b) => b.nota - a.nota);
  } else if (ordenacao.value === "titulo") {
    encontrados.sort((a, b) =>
      a.titulo.localeCompare(b.titulo, "pt-BR")
    );
  }

  listaFilmes.innerHTML = encontrados.map(filme => `
    <article class="movie-card">
      <div class="poster-wrap">
        <img
          class="poster"
          src="${filme.imagem}"
          alt="Imagem ilustrativa de ${filme.titulo}"
          loading="lazy"
          onerror="this.onerror=null;this.style.display='none';this.nextElementSibling.hidden=false;"
        >
        <div class="poster-placeholder" hidden aria-hidden="true">
          ${filme.titulo.charAt(0)}
        </div>

        <span class="movie-rating">★ ${filme.nota.toFixed(1)}</span>

        <button
          class="favorite-btn ${favoritos.has(filme.id) ? "is-favorite" : ""}"
          data-favorito="${filme.id}"
          aria-label="${favoritos.has(filme.id) ? "Remover dos favoritos" : "Adicionar aos favoritos"}: ${filme.titulo}"
          aria-pressed="${favoritos.has(filme.id)}"
          title="Favoritar filme"
        >${favoritos.has(filme.id) ? "♥" : "♡"}</button>

        <button class="details-btn" data-detalhes="${filme.id}">
          VER DETALHES ↗
        </button>
      </div>

      <span class="movie-genre">${filme.genero}</span>
      <h3 class="movie-title">${filme.titulo}</h3>
      <span class="movie-year">${filme.ano} · ★ ${filme.nota.toFixed(1)}</span>
    </article>
  `).join("");

  resultadoTexto.textContent =
    `${encontrados.length} ${encontrados.length === 1 ? "filme encontrado" : "filmes encontrados"}`;

  mensagemVazia.hidden = encontrados.length !== 0;
  listaFilmes.hidden = encontrados.length === 0;

  atualizarContador();
}

// Mantém o número de favoritos atualizado
function atualizarContador() {
  contadorFavoritos.textContent = favoritos.size;
}

// Adicionar ou remover favoritos
function alternarFavorito(id) {
  const filme = filmes.find(item => item.id === id);
  if (!filme) return;

  if (favoritos.has(id)) {
    favoritos.delete(id);
    mostrarMensagem(`"${filme.titulo}" removido dos favoritos.`);
  } else {
    favoritos.add(id);
    mostrarMensagem(`"${filme.titulo}" adicionado aos favoritos! ♥`);
  }

  renderizarFilmes();
}

// Abrir informações de um filme
function abrirDetalhes(id) {
  const filme = filmes.find(item => item.id === id);
  if (!filme) return;

  filmeSelecionado = id;

  detalhesFilme.innerHTML = `
    <div class="modal-layout">
      <img
        class="modal-poster"
        src="${filme.imagem}"
        alt="Imagem ilustrativa de ${filme.titulo}"
        onerror="this.style.display='none'"
      >

      <div class="modal-info">
        <span class="eyebrow">CINEWEB ORIGINAL COLLECTION</span>
        <h2>${filme.titulo}</h2>

        <div class="modal-meta">
          ★ ${filme.nota.toFixed(1)} &nbsp;·&nbsp;
          ${filme.ano} &nbsp;·&nbsp;
          ${filme.genero}
        </div>

        <p>${filme.sinopse}</p>

        <p><strong>Personagens principais:</strong><br>${filme.elenco}</p>

        <button class="btn-primary" id="modalFavorito">
          ${favoritos.has(filme.id) ? "♥ REMOVER DOS FAVORITOS" : "♡ ADICIONAR AOS FAVORITOS"}
        </button>
      </div>
    </div>
  `;

  modal.showModal();
}

// Clique nos botões dos cartões
listaFilmes.addEventListener("click", evento => {
  const botaoFavorito = evento.target.closest("[data-favorito]");
  const botaoDetalhes = evento.target.closest("[data-detalhes]");

  if (botaoFavorito) {
    alternarFavorito(Number(botaoFavorito.dataset.favorito));
  }

  if (botaoDetalhes) {
    abrirDetalhes(Number(botaoDetalhes.dataset.detalhes));
  }
});

// Favoritar também pela janela de detalhes
detalhesFilme.addEventListener("click", evento => {
  if (evento.target.id === "modalFavorito" && filmeSelecionado !== null) {
    alternarFavorito(filmeSelecionado);
    abrirDetalhes(filmeSelecionado);
  }
});

// Pesquisar enquanto digita
pesquisa.addEventListener("input", renderizarFilmes);

// Limpar a pesquisa
document.getElementById("limparPesquisa").addEventListener("click", () => {
  pesquisa.value = "";
  renderizarFilmes();
  pesquisa.focus();
});

// Filtrar por gênero
filtros.addEventListener("click", evento => {
  const botao = evento.target.closest("[data-genero]");
  if (!botao) return;

  generoAtual = botao.dataset.genero;
  mostrandoFavoritos = false;

  document.querySelectorAll(".filter").forEach(item => {
    item.classList.toggle("active", item === botao);
  });

  document.getElementById("verFavoritos").style.color = "";
  renderizarFilmes();
});

// Ordenar filmes
ordenacao.addEventListener("change", renderizarFilmes);

// Mostrar apenas favoritos
document.getElementById("verFavoritos").addEventListener("click", () => {
  mostrandoFavoritos = !mostrandoFavoritos;

  document.getElementById("verFavoritos").style.color =
    mostrandoFavoritos ? "#f04444" : "";

  if (mostrandoFavoritos) {
    generoAtual = "Todos";

    document.querySelectorAll(".filter").forEach(botao => {
      botao.classList.toggle(
        "active",
        botao.dataset.genero === "Todos"
      );
    });

    mostrarMensagem("Exibindo seus filmes favoritos ♥");
    document.getElementById("catalogo").scrollIntoView();
  }

  renderizarFilmes();
});

// Resetar filtros e pesquisa
document.getElementById("resetar").addEventListener("click", () => {
  pesquisa.value = "";
  generoAtual = "Todos";
  mostrandoFavoritos = false;
  ordenacao.value = "padrao";

  document.querySelectorAll(".filter").forEach(botao => {
    botao.classList.toggle(
      "active",
      botao.dataset.genero === "Todos"
    );
  });

  document.getElementById("verFavoritos").style.color = "";
  renderizarFilmes();
});

// Fechar janela
document.getElementById("fecharModal").addEventListener("click", () => {
  modal.close();
});

// Fechar clicando fora da janela
modal.addEventListener("click", evento => {
  if (evento.target === modal) {
    modal.close();
  }
});

// Iniciar a aplicação
renderizarFilmes();
