<!DOCTYPE html>
<html lang="pt-PT">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<meta name="description" content="Study Brain: organiza o estudo, revê conteúdos e pratica para os testes do 6.º ao 9.º ano.">
<title>Study Brain — O futuro começa agora.</title>
<style>
:root{--bg:#f3f8f3;--card:#fff;--text:#203126;--muted:#718076;--green:#72bd83;--soft:#eaf5ec;--border:#dfe9e0}
body.dark{--bg:#151d18;--card:#202b23;--text:#edf5ee;--muted:#aab9ad;--soft:#293b2e;--border:#35453a}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--text);font-family:Arial,sans-serif}
header,nav{background:var(--card);padding:13px 5%;border-bottom:1px solid var(--border)}
header{display:flex;justify-content:space-between;align-items:center;position:sticky;top:0;z-index:5}
.brand{font-size:21px;font-weight:bold;display:flex;align-items:center;gap:10px}
.logo{background:var(--green);color:white;border-radius:12px;padding:10px}
nav{display:flex;gap:8px;flex-wrap:wrap}
button,select,input{font:inherit}
button{background:var(--green);color:white;border:0;padding:11px 15px;border-radius:10px;cursor:pointer;font-weight:bold}
button.secondary{background:var(--soft);color:var(--text)}
button.ghost{background:transparent;color:var(--text);border:1px solid var(--border)}
nav button{background:transparent;color:var(--muted)}
nav button.active{background:var(--soft);color:#398b51}
main{max-width:1050px;margin:25px auto;padding:0 16px 40px}
.hidden{display:none!important}
.panel{background:var(--card);border:1px solid var(--border);border-radius:17px;padding:20px;margin:15px 0}
.hero{text-align:center;padding:50px 20px}
.biglogo{font-size:45px;background:var(--green);width:75px;height:75px;margin:auto auto 15px;border-radius:22px;display:grid;place-items:center}
.credit,.muted{color:var(--muted)}
.credit{margin-top:35px}
.row{display:flex;justify-content:space-between;align-items:center;gap:12px;flex-wrap:wrap}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(210px,1fr));gap:13px}
.subject,.topic{width:100%;background:var(--card);color:var(--text);border:1px solid var(--border);border-radius:14px;padding:17px;text-align:left}
.subject strong,.topic strong{display:block;margin:7px 0}
input,select{padding:12px;border:1px solid var(--border);border-radius:10px;background:var(--card);color:var(--text)}
input{width:100%;margin:15px 0}
.actions{display:flex;gap:8px;flex-wrap:wrap;margin:15px 0}
.lesson{line-height:1.8}
.lesson h3{margin-top:24px}
.note{background:var(--soft);border-left:4px solid var(--green);padding:14px;border-radius:9px;margin:15px 0}
.formula{font-size:21px;font-weight:bold;text-align:center;padding:17px;background:var(--soft);border-radius:12px;margin:12px 0}
.answer{display:block;width:100%;text-align:left;margin:9px 0;background:var(--soft);color:var(--text);border:1px solid var(--border)}
.correct{background:#dff3e3!important;color:#183d22!important}
.wrong{background:#fbe7e7!important;color:#672222!important}
footer{text-align:center;padding:25px;color:var(--muted)}

/* Study Brain — interface refinement */
:root{--green-dark:#347b49;--focus:#246b3b}
body{font-family:system-ui,-apple-system,"Segoe UI",Arial,sans-serif;line-height:1.55}
main{max-width:1120px}
header{box-shadow:0 2px 12px #183d2210}
.header-tools{display:flex;align-items:center;gap:8px}
.header-tools select{width:auto;padding:9px 10px}
.sr-only{position:absolute;width:1px;height:1px;padding:0;margin:-1px;overflow:hidden;clip:rect(0,0,0,0);white-space:nowrap;border:0}
@media(max-width:520px){.header-tools{gap:5px}.header-tools select{max-width:130px;padding:8px 5px}}
.brand{letter-spacing:-.4px}
.logo,.biglogo{box-shadow:0 5px 16px #347b4920}
.panel{box-shadow:0 5px 22px #183d2208}
button,input,select{transition:transform .15s ease,box-shadow .15s ease,background .15s ease}
button:hover{filter:brightness(.97);transform:translateY(-1px)}
button:focus-visible,input:focus-visible,select:focus-visible{outline:3px solid #72bd83;outline-offset:3px}
button:disabled{cursor:default;opacity:.8;transform:none}
.subject,.topic{min-height:82px}
.topic{display:flex;justify-content:space-between;align-items:center;gap:12px;margin:8px 0}
.topic span{color:var(--muted);font-size:13px;white-space:nowrap}
.lesson{max-width:820px;font-size:16px;line-height:1.8}
.lesson h2,.lesson h3{color:var(--green-dark);line-height:1.3}
body.dark .lesson h2,body.dark .lesson h3{color:#9bd5a8}
.lesson p{margin:10px 0}
.lesson li{margin:7px 0}
.lesson .formula{overflow-x:auto}
.lesson .definition{background:var(--soft);padding:14px 16px;border-radius:12px;border:1px solid var(--border);margin:14px 0}
.lesson .example{border-left:4px solid var(--green);padding:12px 16px;background:var(--card);border-radius:8px;margin:14px 0}
.lesson .warning{border-left:4px solid #d5a33b;padding:12px 16px;background:var(--soft);border-radius:8px;margin:14px 0}
.lesson .keyline{display:flex;flex-wrap:wrap;gap:7px;margin:12px 0}
.lesson .keyline span{background:var(--soft);border:1px solid var(--border);padding:5px 10px;border-radius:999px;font-size:13px}
.quiz-progress{height:8px;background:var(--soft);border-radius:99px;overflow:hidden;margin:10px 0 18px}
.quiz-progress span{display:block;height:100%;background:var(--green);border-radius:99px}
.quiz-meta{font-size:13px;color:var(--muted)}
.answer{line-height:1.45;padding:13px 15px}
.note{line-height:1.6}
@media(max-width:620px){
 header,nav{padding:11px 4%}
 .brand{font-size:18px}
 main{margin:14px auto;padding:0 12px 30px}
 .panel{padding:15px}
 .hero{padding:35px 16px}
 .topic{align-items:flex-start}
}
@media(prefers-reduced-motion:reduce){*,*::before,*::after{transition:none!important;scroll-behavior:auto!important}}

</style>
</head>
<body>
<header>
<div class="brand"><span class="logo">🧠</span>Study Brain</div>
<div class="header-tools"><label for="languageSelect" class="sr-only" id="languageLabel">Idioma da interface</label><select id="languageSelect" aria-label="Idioma da interface" onchange="setLanguage(this.value)"><option value="pt">🇵🇹 Português</option><option value="en">🇬🇧 English</option><option value="es">🇪🇸 Español</option></select><button class="ghost" onclick="toggleTheme()" id="themeBtn">🌙 Tema</button></div>
</header>
<nav>
<button class="active" onclick="page('home',this)" id="navHome">⌂ Início</button>
<button onclick="page('subjects',this)" id="navSubjects">📚 Disciplinas</button>
<button onclick="page('favorites',this)" id="navFavorites">★ Favoritos</button>
</nav>
<main>
<section id="home" class="page">
<div class="panel hero">
<div class="biglogo">🧠</div>
<h1>Study Brain</h1>
<p class="muted">O futuro começa agora.</p>
<p>Aprende ao teu ritmo. Estuda, pratica e melhora os teus conhecimentos.</p>
<button onclick="page('subjects')">Começar a estudar</button>
<div class="credit">Feito por Rafael Saraiva 💚</div>
</div>
</section>

<section id="subjects" class="page hidden">
<div class="row"><div><h1 id="subjectsHeading">Disciplinas</h1><p class="muted" id="subjectsHint">Escolhe o ano e a disciplina.</p><p class="muted" id="subjectsNote">Temas de referência. Algumas disciplinas aparecem como apoio nos anos em que não fazem parte da matriz curricular nacional; confirma a oferta da tua escola.</p></div>
<select id="year" onchange="renderSubjects()">
<option value="6">6.º ano</option><option value="7">7.º ano</option><option value="8">8.º ano</option><option value="9" selected>9.º ano</option>
</select></div>
<input id="search" placeholder="🔎 Pesquisar disciplina ou tema..." oninput="renderSubjects()">
<div id="subjectGrid" class="grid"></div>
</section>

<section id="favorites" class="page hidden">
<h1 id="favoritesHeading">Favoritos</h1><div id="favoriteGrid" class="grid"></div>
</section>

<section id="detail" class="page hidden">
<button class="secondary" onclick="page('subjects')" id="backSubjects">← Voltar</button>
<div class="panel">
<div class="row"><div><p id="yearLabel" class="muted"></p><h1 id="subjectTitle"></h1></div><button class="ghost" id="favBtn" onclick="toggleFavorite()">☆ Guardar</button></div>
<div class="actions">
<button onclick="showTopics('summary')" id="tabSummary">Resumos</button>
<button class="secondary" onclick="showTopics('exercises')" id="tabExercises">Exercícios</button>
<button class="secondary" onclick="showTopics('complete')" id="tabComplete">Matéria e explicações</button>
<button class="secondary" onclick="showTopics('testprep')" id="tabTestprep">Preparação para testes</button>
</div>
<div class="note" id="contentNote"><strong>Nota:</strong> os conteúdos são guias de apoio ao estudo. Confirma sempre os tópicos e a profundidade da matéria com o manual e o professor.</div>
<div id="topics"></div>
</div>
</section>

<section id="study" class="page hidden">
<button class="secondary" onclick="page('detail')" id="backDetail">← Voltar</button>
<div class="panel">
<h1 id="lessonTitle"></h1>
<div id="lessonBody" class="lesson"></div>
<div id="exerciseArea"></div>
</div>
</section>
</main>
<footer><span id="footerTag">Study Brain · O futuro começa agora. 💚</span><br><small id="footerNote">Conteúdos de apoio ao estudo. Confirma sempre o programa da tua turma.</small></footer>

<script>
const subjects=[
["Matemática","📐"],["Português","📖"],["Ciências Naturais","🌱"],["Físico-Química","⚗️"],
["Inglês","🇬🇧"],["Espanhol","🇪🇸"],["Geografia","🌍"],["História","🏛️"],
["TIC","💻"],["Educação Física","⚽"],["Educação Visual","🎨"],["Música","🎵"]
];

const curriculum={
  "Matemática": {
    "6": [
      "Números naturais e operações",
      "Múltiplos e divisores",
      "Números primos e decomposição em fatores primos",
      "Frações: significado e equivalência",
      "Operações com frações",
      "Números decimais e operações",
      "Percentagens e proporcionalidade",
      "Regularidades e sequências",
      "Ângulos e amplitude",
      "Figuras geométricas planas",
      "Perímetro e área de figuras planas",
      "Sólidos geométricos, volume e capacidade",
      "Organização e tratamento de dados"
    ],
    "7": [
      "Números inteiros: representação e comparação",
      "Adição e subtração de números inteiros",
      "Números racionais e representação",
      "Operações com números racionais",
      "Potências e regras operatórias",
      "Sequências e regularidades",
      "Expressões algébricas",
      "Equações do 1.º grau",
      "Proporcionalidade direta",
      "Funções: tabelas e gráficos",
      "Triângulos e soma dos ângulos",
      "Construções geométricas",
      "Áreas e volumes",
      "Dados, medidas estatísticas e probabilidades"
    ],
    "8": [
      "Números racionais e números reais",
      "Dízimas e valores aproximados",
      "Potências de expoente inteiro",
      "Raízes quadradas e cúbicas",
      "Monómios e polinómios",
      "Operações com polinómios",
      "Casos notáveis da multiplicação",
      "Equações do 1.º grau e problemas",
      "Sistemas de duas equações",
      "Funções e gráficos",
      "Teorema de Pitágoras",
      "Vetores e translações",
      "Áreas e volumes de sólidos",
      "Organização e análise de dados"
    ],
    "9": [
      "Números reais e intervalos",
      "Potências e notação científica",
      "Inequações do 1.º grau",
      "Equações do 2.º grau",
      "Fatorização de polinómios",
      "Casos notáveis da multiplicação",
      "Funções: conceitos e representações",
      "Função afim e função quadrática",
      "Proporcionalidade inversa",
      "Trigonometria no triângulo retângulo",
      "Circunferência e polígonos",
      "Áreas e volumes",
      "Probabilidades e análise de dados"
    ]
  },
  "Português": {
    "6": [
      "Leitura e compreensão de textos",
      "Texto narrativo: estrutura e elementos",
      "Texto descritivo",
      "Texto poético",
      "Texto dramático",
      "Educação literária e obras de leitura",
      "Classes de palavras: nome, adjetivo e verbo",
      "Determinantes, pronomes e quantificadores",
      "Verbos: tempos e modos",
      "Frase, sujeito e predicado",
      "Pontuação e ortografia",
      "Texto de opinião e texto informativo",
      "Comunicação oral e apresentação"
    ],
    "7": [
      "Leitura: tema, assunto e ideias principais",
      "Texto narrativo e elementos da narrativa",
      "Texto descritivo e retrato",
      "Texto poético: recursos expressivos",
      "Texto dramático e texto teatral",
      "Educação literária: leitura e interpretação",
      "Classes e subclasses de palavras",
      "Tempos e modos verbais",
      "Funções sintáticas essenciais",
      "Frase simples e frase complexa",
      "Coordenação de orações",
      "Texto de opinião e argumentação",
      "Escrita, revisão e oralidade"
    ],
    "8": [
      "Texto narrativo e conto",
      "Texto poético e recursos expressivos",
      "Texto dramático",
      "Crónica e texto de opinião",
      "Texto expositivo e informativo",
      "Educação literária: interpretação de obras",
      "Classes de palavras e formação de palavras",
      "Funções sintáticas",
      "Orações coordenadas",
      "Orações subordinadas: introdução",
      "Discurso direto e indireto",
      "Coesão, coerência e conectores",
      "Escrita argumentativa e apresentação oral"
    ],
    "9": [
      "Leitura crítica e interpretação",
      "Educação literária: autores e obras",
      "Texto narrativo: conto e romance",
      "Texto poético: temas e recursos",
      "Texto dramático",
      "Crónica, crítica e apreciação",
      "Texto argumentativo e texto de opinião",
      "Orações coordenadas e subordinadas",
      "Orações subordinadas substantivas, adjetivas e adverbiais",
      "Funções sintáticas e modalidades de frase",
      "Discurso direto, indireto e indireto livre",
      "Coesão, coerência e progressão temática",
      "Escrita formal, revisão e comunicação oral"
    ]
  },
  "Ciências Naturais": {
    "6": [
      "Processos vitais comuns aos seres vivos",
      "Célula: constituição e organização",
      "Diversidade dos seres vivos e classificação",
      "Microrganismos e sua importância",
      "A água e a qualidade da água",
      "Ar, solo e conservação da Natureza",
      "Alimentação equilibrada e sistema digestivo",
      "Sistema respiratório e circulação",
      "Sistema urinário e eliminação de resíduos",
      "Reprodução humana e desenvolvimento",
      "Higiene, saúde e prevenção de doenças",
      "Ecossistemas e relações entre seres vivos"
    ],
    "7": [
      "Paisagens geológicas e dinâmica da Terra",
      "Minerais: propriedades e identificação",
      "Rochas: formação e ciclo das rochas",
      "Fósseis e história da Terra",
      "Vulcanismo e atividade vulcânica",
      "Sismos e risco sísmico",
      "Estrutura interna da Terra",
      "Dinâmica externa: meteorização e erosão",
      "Célula e níveis de organização biológica",
      "Biodiversidade e classificação dos seres vivos",
      "Ecossistemas e fatores abióticos e bióticos"
    ],
    "8": [
      "Ecossistemas: organização e funcionamento",
      "Fluxos de energia nos ecossistemas",
      "Cadeias e teias alimentares",
      "Ciclos de matéria nos ecossistemas",
      "Relações bióticas e equilíbrio ecológico",
      "Perturbações dos ecossistemas e conservação",
      "Gestão sustentável dos recursos naturais",
      "Solo, água e biodiversidade",
      "Reprodução nos seres vivos",
      "Reprodução das plantas e dos animais",
      "Hereditariedade: conceitos fundamentais",
      "Transmissão de características hereditárias"
    ],
    "9": [
      "Saúde individual e comunitária",
      "Promoção da saúde e prevenção da doença",
      "Sistema digestivo e nutrição",
      "Sistema cardiovascular e sangue",
      "Sistema respiratório e trocas gasosas",
      "Sistema urinário e regulação do organismo",
      "Sistema nervoso e sistema hormonal",
      "Sistema reprodutor humano",
      "Ciclo menstrual, fecundação e desenvolvimento",
      "Genética e transmissão hereditária",
      "Doenças: prevenção e estilos de vida saudáveis",
      "Ciência, tecnologia e qualidade de vida"
    ]
  },
  "Físico-Química": {
    "6": [
      "Materiais naturais e manufaturados",
      "Propriedades dos materiais",
      "Estados físicos da matéria",
      "Mudanças de estado físico",
      "Misturas e substâncias",
      "Separação de componentes de misturas",
      "Luz: fontes e propagação",
      "Reflexão e formação de imagens",
      "Som: produção e propagação",
      "Características do som e poluição sonora"
    ],
    "7": [
      "Universo: estrelas, planetas e galáxias",
      "Sistema Solar e movimentos dos planetas",
      "Distâncias no Universo",
      "Constituição da matéria: átomos e moléculas",
      "Substâncias e misturas",
      "Transformações físicas e químicas",
      "Energia: fontes e transferências",
      "Temperatura e equilíbrio térmico",
      "Movimento e repouso",
      "Rapidez média e gráficos posição-tempo",
      "Forças: efeitos e representação",
      "Massa e peso"
    ],
    "8": [
      "Reações químicas e evidências de transformação",
      "Equações químicas e conservação da massa",
      "Tipos de reações químicas",
      "Velocidade das reações",
      "Som: produção, propagação e receção",
      "Características das ondas sonoras",
      "Luz: propagação e reflexão",
      "Refração e lentes",
      "Eletricidade e corrente elétrica",
      "Circuitos elétricos e componentes",
      "Tensão, corrente e resistência",
      "Segurança na utilização da eletricidade"
    ],
    "9": [
      "Movimento e referencial",
      "Rapidez média e aceleração",
      "Gráficos dos movimentos",
      "Forças e leis do movimento",
      "Lei da inércia e lei fundamental da dinâmica",
      "Forças de ação-reação",
      "Forças, pressão e fluidos",
      "Energia cinética e energia potencial",
      "Conservação e transferências de energia",
      "Corrente elétrica e circuitos",
      "Resistência elétrica e lei de Ohm",
      "Estrutura atómica e tabela periódica",
      "Ligações químicas e propriedades dos materiais"
    ]
  },
  "Inglês": {
    "6": [
      "Personal identification and greetings",
      "Family and friends",
      "Home and daily routines",
      "School and classroom language",
      "Free time and hobbies",
      "Food, meals and healthy habits",
      "Clothes, shopping and prices",
      "Weather and seasons",
      "Town, places and directions",
      "Present simple and present continuous",
      "There is/there are, prepositions and question forms"
    ],
    "7": [
      "Personal identity and relationships",
      "Daily routines and free-time activities",
      "School life and learning",
      "Food, health and lifestyles",
      "House, town and directions",
      "Travel and holidays",
      "Environment and nature",
      "Past simple: regular and irregular verbs",
      "Comparatives and superlatives",
      "Countable and uncountable nouns",
      "Writing messages, descriptions and short texts"
    ],
    "8": [
      "People, identity and relationships",
      "Media, communication and technology",
      "Travel, cultures and traditions",
      "Healthy lifestyles and wellbeing",
      "Environment and sustainability",
      "School, work and future choices",
      "Past continuous and past simple",
      "Present perfect: experiences",
      "Future forms and intentions",
      "Modal verbs and advice",
      "Writing narratives, emails and opinions"
    ],
    "9": [
      "Identity, diversity and relationships",
      "Global issues and citizenship",
      "Environment and climate action",
      "Technology, media and digital life",
      "Work, careers and future plans",
      "Arts, culture and entertainment",
      "Social challenges and volunteering",
      "Present perfect and past tenses review",
      "Future forms and conditionals",
      "Passive voice and reported speech",
      "Argumentative writing, presentations and debate"
    ]
  },
  "Espanhol": {
    "6": [
      "Saludos y presentaciones",
      "La familia y los amigos",
      "La escuela y el material escolar",
      "La casa y las habitaciones",
      "Los alimentos y las comidas",
      "Los animales y la naturaleza",
      "Los días, meses y la hora",
      "Descripción física y carácter",
      "Presente de indicativo",
      "Artículos, género y número",
      "Preguntas y expresiones cotidianas"
    ],
    "7": [
      "La rutina diaria",
      "El tiempo libre y las aficiones",
      "La ciudad y los lugares",
      "Las compras y la ropa",
      "Los viajes y transportes",
      "El tiempo atmosférico",
      "La alimentación y la salud",
      "Presente y verbos reflexivos",
      "Verbos ser, estar y tener",
      "Adjetivos, posesivos y demostrativos",
      "Expresar gustos, preferencias y planes"
    ],
    "8": [
      "Las vacaciones y los viajes",
      "La cultura y las fiestas",
      "La alimentación y los hábitos saludables",
      "El medio ambiente",
      "La tecnología y los medios de comunicación",
      "La salud y el cuerpo humano",
      "Pretérito perfecto e indefinido",
      "Contraste entre tiempos del pasado",
      "Comparativos y superlativos",
      "Pronombres y preposiciones",
      "Dar consejos, narrar y expresar opinión"
    ],
    "9": [
      "Planes de futuro y profesiones",
      "Sociedad, ciudadanía y convivencia",
      "Medios de comunicación y redes",
      "Tecnología y mundo digital",
      "Cultura y diversidad del mundo hispano",
      "Medio ambiente y sostenibilidad",
      "Experiencias y recuerdos",
      "Futuro simple y perífrasis verbales",
      "Condicional y subjuntivo: introducción",
      "Oraciones temporales y causales",
      "Argumentar, debatir y redactar textos"
    ]
  },
  "Geografia": {
    "6": [
      "A Terra no Sistema Solar",
      "Globo terrestre e mapas",
      "Localização relativa e absoluta",
      "Elementos fundamentais dos mapas",
      "Continentes e oceanos",
      "Relevo e principais formas de relevo",
      "Rios e redes hidrográficas",
      "Clima, estados do tempo e fatores climáticos",
      "Paisagens naturais e humanizadas",
      "População e distribuição no território"
    ],
    "7": [
      "A representação da superfície terrestre",
      "Escalas, orientação e coordenadas geográficas",
      "Localização dos continentes e oceanos",
      "Meio natural: relevo e hidrografia",
      "Clima e formações vegetais",
      "Dinâmica da população mundial",
      "Distribuição e mobilidade da população",
      "Cidades e organização do espaço urbano",
      "Riscos naturais e proteção das populações"
    ],
    "8": [
      "População e povoamento",
      "Estrutura etária e movimentos da população",
      "Mobilidade e migrações",
      "Áreas rurais e urbanas",
      "Agricultura e produção alimentar",
      "Pesca e exploração dos recursos marinhos",
      "Indústria e localização industrial",
      "Serviços, comércio e turismo",
      "Transportes e telecomunicações",
      "Desigualdades de desenvolvimento",
      "Impactes ambientais das atividades económicas"
    ],
    "9": [
      "Contrastes de desenvolvimento",
      "Indicadores de desenvolvimento humano",
      "Desigualdades sociais e territoriais",
      "Globalização e interdependência económica",
      "Comércio internacional e fluxos mundiais",
      "Ambiente, recursos e sustentabilidade",
      "Alterações climáticas e riscos ambientais",
      "Riscos naturais e tecnológicos",
      "Ordenamento do território",
      "Cooperação internacional e desenvolvimento sustentável"
    ]
  },
  "História": {
    "6": [
      "Portugal nos séculos XIII e XIV",
      "Sociedade medieval portuguesa",
      "Poder político e vida quotidiana na Idade Média",
      "Crise do século XIV",
      "Revolução de 1383-1385",
      "Expansão portuguesa e contactos com outros povos",
      "Conquista de Ceuta e exploração da costa africana",
      "Império português e rotas comerciais",
      "Renascimento e Humanismo",
      "Reforma e Contrarreforma"
    ],
    "7": [
      "Origens da Humanidade e sociedades recoletoras",
      "Revolução neolítica e sedentarização",
      "Civilizações dos grandes rios",
      "Grécia Antiga: sociedade e democracia",
      "Roma: expansão e organização do Império",
      "Cristianismo e formação da Europa medieval",
      "Sociedade feudal e poder senhorial",
      "Cultura e arte medievais",
      "Nascimento e afirmação de Portugal"
    ],
    "8": [
      "Renascimento e Humanismo",
      "Reforma Protestante e Contrarreforma",
      "Expansão europeia e contactos entre culturas",
      "Impérios coloniais e comércio mundial",
      "Absolutismo e sociedade de ordens",
      "Iluminismo e pensamento político",
      "Revoluções liberais: causas e consequências",
      "Revolução Francesa",
      "Revolução Liberal portuguesa",
      "Revolução Industrial e transformações sociais",
      "Liberalismo, nacionalismo e imperialismo"
    ],
    "9": [
      "Sociedade e economia no início do século XX",
      "Primeira Guerra Mundial",
      "Revolução Russa e construção da URSS",
      "Crise das democracias e regimes totalitários",
      "Grande Depressão e crise de 1929",
      "Segunda Guerra Mundial e Holocausto",
      "Organização das Nações Unidas",
      "Guerra Fria e mundo bipolar",
      "Descolonização e novos países",
      "Portugal: Estado Novo e resistência",
      "Revolução de 25 de Abril de 1974",
      "Democratização, integração europeia e mundo atual"
    ]
  },
  "TIC": {
    "6": [
      "Cidadania e segurança digital",
      "Pesquisa e avaliação de informação",
      "Navegadores, motores de busca e fontes",
      "Organização de ficheiros e pastas",
      "Processamento de texto",
      "Formatação e edição de documentos",
      "Apresentações digitais",
      "Comunicação e colaboração online",
      "Direitos de autor e licenças",
      "Privacidade e proteção de dados"
    ],
    "7": [
      "Equipamentos e sistemas digitais",
      "Gestão de ficheiros e informação",
      "Pesquisa avançada e validação de fontes",
      "Documentos e ferramentas de produtividade",
      "Apresentações com elementos multimédia",
      "Comunicação e colaboração digital",
      "Segurança, privacidade e identidade digital",
      "Cidadania e comportamento online",
      "Introdução ao pensamento computacional"
    ],
    "8": [
      "Folhas de cálculo: células e fórmulas",
      "Funções e gráficos em folhas de cálculo",
      "Apresentações multimédia",
      "Imagem digital e edição",
      "Áudio e vídeo digital",
      "Algoritmos e decomposição de problemas",
      "Programação por blocos ou texto",
      "Dados, organização e visualização",
      "Segurança informática e privacidade",
      "Direitos de autor e utilização responsável"
    ],
    "9": [
      "Criação e publicação de conteúdos digitais",
      "Design e comunicação multimédia",
      "Folhas de cálculo e análise de dados",
      "Algoritmos e estruturas de controlo",
      "Programação e resolução de problemas",
      "Robótica e sistemas computacionais: introdução",
      "Redes e serviços digitais",
      "Cibersegurança e proteção da identidade",
      "Inteligência artificial e tecnologias emergentes",
      "Ética, direitos de autor e cidadania digital"
    ]
  },
  "Educação Física": {
    "6": [
      "Desenvolvimento das capacidades motoras",
      "Jogos pré-desportivos",
      "Basquetebol: regras e fundamentos",
      "Futebol: condução, passe e receção",
      "Andebol: passe e remate",
      "Atletismo: corridas, saltos e lançamentos",
      "Ginástica de solo",
      "Ginástica de aparelhos",
      "Dança e atividades rítmicas",
      "Orientação e atividades ao ar livre",
      "Saúde, segurança e hábitos ativos"
    ],
    "7": [
      "Aptidão física e capacidades motoras",
      "Basquetebol",
      "Futebol",
      "Andebol",
      "Voleibol",
      "Atletismo: corrida, salto e lançamento",
      "Ginástica de solo e aparelhos",
      "Dança e expressão corporal",
      "Badminton e desportos de raquete",
      "Atividades de exploração da Natureza",
      "Regras, arbitragem e espírito desportivo"
    ],
    "8": [
      "Aptidão física e condição física",
      "Basquetebol: técnica e tática",
      "Futebol: técnica e jogo",
      "Andebol: técnica e tática",
      "Voleibol: serviço, manchete e passe",
      "Atletismo: provas e técnica",
      "Ginástica: elementos e sequências",
      "Dança: composição e interpretação",
      "Badminton e ténis de mesa",
      "Orientação e atividades ao ar livre",
      "Segurança, cooperação e fair play"
    ],
    "9": [
      "Avaliação e desenvolvimento da aptidão física",
      "Desportos coletivos: técnica e tática",
      "Basquetebol e jogo formal",
      "Futebol e jogo formal",
      "Andebol e jogo formal",
      "Voleibol e jogo formal",
      "Atletismo: aperfeiçoamento técnico",
      "Ginástica: sequências e elementos",
      "Dança e atividades rítmicas",
      "Desportos de raquete e atividades alternativas",
      "Atividade física, saúde e autonomia"
    ]
  },
  "Educação Visual": {
    "6": [
      "Linguagem visual e comunicação",
      "Ponto, linha e forma",
      "Textura e padrão",
      "Cor: círculo cromático e misturas",
      "Luz e sombra",
      "Representação de objetos e espaço",
      "Desenho de observação",
      "Composição visual e equilíbrio",
      "Técnicas e materiais de expressão",
      "Imagem, símbolo e mensagem"
    ],
    "7": [
      "Elementos da linguagem visual",
      "Comunicação visual e leitura de imagens",
      "Geometria e construção de formas",
      "Representação do espaço e perspetiva",
      "Luz, sombra e volume",
      "Cor, contraste e harmonia",
      "Texturas e materiais",
      "Desenho de observação e interpretação",
      "Composição e organização visual",
      "Património artístico e cultural"
    ],
    "8": [
      "Design e resolução de problemas visuais",
      "Comunicação e narrativa visual",
      "Representação rigorosa e perspetiva",
      "Luz, sombra e modelação do volume",
      "Cor e relações cromáticas",
      "Composição, ritmo e equilíbrio",
      "Imagem digital e manipulação visual",
      "Materiais, técnicas e processos",
      "Arte, património e contexto cultural"
    ],
    "9": [
      "Projeto visual: pesquisa e desenvolvimento",
      "Design gráfico e comunicação",
      "Identidade visual, símbolos e logótipos",
      "Composição e hierarquia visual",
      "Desenho expressivo e representação",
      "Perspetiva e representação do espaço",
      "Fotografia e imagem digital",
      "Arte contemporânea e património",
      "Experimentação de materiais e técnicas",
      "Apresentação e avaliação de projetos"
    ]
  },
  "Música": {
    "6": [
      "Altura, duração, intensidade e timbre",
      "Pulsação, ritmo e compasso",
      "Figuras rítmicas e pausas",
      "Melodia e frases musicais",
      "Instrumentos e famílias instrumentais",
      "Voz e técnica vocal",
      "Notação musical e leitura simples",
      "Prática instrumental e vocal em conjunto",
      "Audição e identificação de elementos musicais",
      "Criação de padrões rítmicos e melódicos"
    ],
    "7": [
      "Elementos da linguagem musical",
      "Ritmo, pulsação e compassos",
      "Altura, escalas e intervalos",
      "Melodia e acompanhamento",
      "Timbre e famílias de instrumentos",
      "Dinâmica, andamento e forma",
      "Leitura e escrita musical",
      "Interpretação vocal e instrumental",
      "Música tradicional portuguesa e do mundo",
      "Escuta ativa e análise musical"
    ],
    "8": [
      "Organização e estrutura das formas musicais",
      "Ritmos e padrões de diferentes culturas",
      "Melodia, harmonia e acompanhamento",
      "Timbres e agrupamentos instrumentais",
      "Dinâmica, andamento e expressão",
      "Música erudita, tradicional e popular",
      "Tecnologia e produção musical",
      "Composição e improvisação",
      "Interpretação em conjunto",
      "Análise e contextualização de obras"
    ],
    "9": [
      "Música e identidade cultural",
      "Música em diferentes épocas e sociedades",
      "Géneros e estilos musicais",
      "Música tradicional e património",
      "Música popular e indústria musical",
      "Composição, arranjo e improvisação",
      "Tecnologias de gravação e produção",
      "Interpretação vocal e instrumental",
      "Elementos de análise musical",
      "Projeto musical e apresentação pública"
    ]
  }
};

const cases={
"Casos notáveis da multiplicação":{
summary:`Os **casos notáveis** são igualdades algébricas que permitem desenvolver produtos de polinómios rapidamente. Existem três fórmulas fundamentais.`,
complete:`<h3>1. Quadrado da soma</h3><div class="formula">(a + b)² = a² + 2ab + b²</div><p>O quadrado da soma de dois termos é igual ao quadrado do primeiro, mais o dobro do produto dos dois termos, mais o quadrado do segundo.</p><p><strong>Exemplo:</strong> (x + 3)²</p><p>= x² + 2 × x × 3 + 3²</p><p>= <strong>x² + 6x + 9</strong></p><div class="note">Atenção: (a + b)² não é igual a a² + b². Falta o termo 2ab.</div><h3>2. Quadrado da diferença</h3><div class="formula">(a - b)² = a² - 2ab + b²</div><p>O quadrado da diferença é igual ao quadrado do primeiro termo, menos o dobro do produto dos dois termos, mais o quadrado do segundo.</p><p><strong>Exemplo:</strong> (x - 4)²</p><p>= x² - 2 × x × 4 + 4²</p><p>= <strong>x² - 8x + 16</strong></p><h3>3. Diferença de quadrados</h3><div class="formula">(a + b)(a - b) = a² - b²</div><p>O produto da soma pela diferença de dois termos é igual à diferença dos seus quadrados.</p><p><strong>Exemplo:</strong> (x + 5)(x - 5)</p><p>= x² - 5²</p><p>= <strong>x² - 25</strong></p><h3>Como reconhecer os casos notáveis?</h3><ul><li>Um parêntesis ao quadrado com uma soma: quadrado da soma.</li><li>Um parêntesis ao quadrado com uma subtração: quadrado da diferença.</li><li>Dois parêntesis iguais, mas com sinais opostos: diferença de quadrados.</li></ul><div class="note"><strong>Regra essencial:</strong> identifica os dois termos antes de substituir na fórmula. Tem atenção aos sinais e ao termo do meio.</div>`,
questions:[
{q:"Qual é o desenvolvimento de (x + 2)²?",a:["x² + 4","x² + 4x + 4","x² + 2x + 4","x² - 4x + 4"],c:1,e:"Aplica-se a² + 2ab + b²: x² + 4x + 4."},
{q:"Qual é o desenvolvimento de (x - 3)²?",a:["x² - 9","x² - 6x + 9","x² + 6x + 9","x² - 3x + 9"],c:1,e:"Aplica-se a² - 2ab + b²: x² - 6x + 9."},
{q:"Quanto é (x + 4)(x - 4)?",a:["x² + 16","x² - 8x + 16","x² - 16","x² + 8x + 16"],c:2,e:"É uma diferença de quadrados: x² - 4² = x² - 16."},
{q:"Qual é a fórmula do quadrado da soma?",a:["a² + b²","a² - 2ab + b²","a² + 2ab + b²","a² - b²"],c:2,e:"O quadrado da soma é a² + 2ab + b²."}
]}
};

const generic={
"Matemática":{
summary:"A Matemática estuda números, formas, relações e padrões. Para resolver problemas, identifica os dados, escolhe uma estratégia e verifica o resultado.",
complete:"<h3>Como resolver problemas matemáticos</h3><p>Começa por ler o enunciado e identificar os dados conhecidos. Depois, determina o que é pedido e escolhe a operação, fórmula ou propriedade adequada.</p><h3>Apresentação do raciocínio</h3><p>Organiza os cálculos por etapas, utiliza símbolos corretamente e apresenta a resposta com as unidades, quando necessário.</p><div class='note'>Confirma sempre se o resultado é coerente com o problema.</div>"
},
"Português":{
summary:"O Português desenvolve a leitura, a escrita, a oralidade, a gramática e a educação literária.",
complete:"<h3>Compreender textos</h3><p>Identifica o tema, a intenção comunicativa, as ideias principais e a organização do texto. Distingue informação explícita de informação implícita.</p><h3>Gramática e escrita</h3><p>Reconhece as classes de palavras e as funções que desempenham. Na escrita, organiza as ideias em parágrafos, utiliza pontuação adequada e revê o texto.</p><div class='note'>Uma resposta completa deve ser clara, correta e fundamentada.</div>"
},
"Ciências Naturais":{
summary:"As Ciências Naturais estudam os seres vivos, o planeta, o ambiente e os processos que permitem compreender a Natureza.",
complete:"<h3>O trabalho científico</h3><p>A investigação científica começa com uma questão. Podem formular-se hipóteses, planear experiências, recolher dados e analisar resultados.</p><h3>Interpretação</h3><p>É importante distinguir observações, hipóteses e conclusões. Os resultados devem apoiar as conclusões apresentadas.</p><div class='note'>Relaciona os conhecimentos científicos com situações do quotidiano.</div>"
},
"Físico-Química":{
summary:"A Físico-Química estuda a matéria, a energia, os fenómenos físicos e as transformações químicas.",
complete:"<h3>Grandezas e medições</h3><p>Uma grandeza física é uma propriedade que pode ser medida. O resultado de uma medição deve incluir um valor numérico e uma unidade.</p><h3>Experiências</h3><p>As experiências permitem estudar fenómenos de forma controlada. Regista os dados, identifica variáveis e interpreta os resultados.</p><div class='note'>Não confundas massa com peso: são grandezas físicas diferentes.</div>"
},
"Inglês":{
summary:"English learning includes vocabulary, grammar, reading, listening, speaking and writing.",
complete:"<h3>Building communication skills</h3><p>Learn vocabulary in context and practise using it in complete sentences. Reading helps you understand main ideas and specific information.</p><h3>Grammar and writing</h3><p>Pay attention to verb tenses, word order, pronouns and connectors. Organise written texts with an introduction, development and conclusion.</p><div class='note'>Practise regularly and use new words in your own examples.</div>"
},
"Espanhol":{
summary:"El español se aprende mediante la comprensión y expresión oral y escrita, el vocabulario y la gramática.",
complete:"<h3>Comprensión y expresión</h3><p>Lee textos, identifica las ideas principales y aprende vocabulario relacionado con diferentes situaciones cotidianas.</p><h3>Gramática</h3><p>Practica la conjugación verbal, los artículos, los pronombres y la concordancia entre sustantivos y adjetivos.</p><div class='note'>Presta atención a los acentos y a la pronunciación.</div>"
},
"Geografia":{
summary:"A Geografia estuda a distribuição dos fenómenos naturais e humanos e as relações entre as sociedades e o território.",
complete:"<h3>Ferramentas geográficas</h3><p>Os mapas, gráficos, tabelas e imagens ajudam a localizar e interpretar fenómenos. Analisa sempre o título, a legenda, a escala e a orientação.</p><h3>Sociedade e ambiente</h3><p>As atividades humanas transformam o território e influenciam os recursos naturais, a população e a organização das cidades.</p><div class='note'>Relaciona os fenómenos com a sua localização e contexto.</div>"
},
"História":{
summary:"A História estuda as sociedades humanas ao longo do tempo, analisando acontecimentos, causas e consequências.",
complete:"<h3>Tempo histórico</h3><p>Os acontecimentos podem ser organizados cronologicamente. Séculos, décadas e períodos históricos ajudam a compreender a evolução das sociedades.</p><h3>Análise histórica</h3><p>Compara fontes, identifica causas e consequências e procura compreender os acontecimentos no contexto da época.</p><div class='note'>Distingue sempre a data de um acontecimento das suas causas e consequências.</div>"
},
"TIC":{
summary:"As TIC permitem criar, organizar e comunicar informação através de ferramentas digitais.",
complete:"<h3>Utilização responsável</h3><p>Utiliza ferramentas digitais de forma segura, respeita a privacidade e confirma a fiabilidade das fontes.</p><h3>Criação de conteúdos</h3><p>Documentos, apresentações, folhas de cálculo e programas podem ser utilizados para resolver problemas e comunicar informação.</p><div class='note'>Respeita os direitos de autor e protege os teus dados pessoais.</div>"
},
"Educação Física":{
summary:"A Educação Física desenvolve capacidades motoras, conhecimentos sobre atividade física e atitudes de cooperação e respeito.",
complete:"<h3>Prática e aprendizagem</h3><p>As atividades físicas permitem desenvolver coordenação, equilíbrio, resistência e outras capacidades motoras.</p><h3>Segurança e cooperação</h3><p>Respeita as regras, os colegas e as indicações do professor. A preparação e a recuperação fazem parte de uma prática segura.</p><div class='note'>A atividade física deve ser adequada às capacidades e necessidades de cada pessoa.</div>"
},
"Educação Visual":{
summary:"A Educação Visual explora a comunicação através da linha, forma, cor, textura, luz e composição.",
complete:"<h3>Elementos visuais</h3><p>A linha pode sugerir movimento, a forma organiza os elementos e a cor influencia a perceção. A textura e a luz acrescentam características visuais.</p><h3>Composição</h3><p>Organizar os elementos numa imagem permite criar equilíbrio, contraste, hierarquia e intenção comunicativa.</p><div class='note'>Observa como cada escolha visual contribui para a mensagem.</div>"
},
"Música":{
summary:"A Música explora o som, o ritmo, a melodia, a harmonia, o timbre e a interpretação.",
complete:"<h3>Elementos musicais</h3><p>O ritmo organiza os sons no tempo. A melodia combina alturas sonoras e o timbre permite distinguir diferentes fontes sonoras.</p><h3>Escuta e interpretação</h3><p>Ao ouvir uma peça, procura reconhecer instrumentos, dinâmica, andamento e organização musical.</p><div class='note'>A escuta atenta ajuda a identificar características e estilos musicais.</div>"
}
};

const translations={
pt:{languageLabel:"Idioma da interface",slogan:"O futuro começa agora.",home:"Início",subjects:"Disciplinas",favorites:"Favoritos",theme:"Tema",start:"Começar a estudar",welcome:"Aprende ao teu ritmo. Estuda, pratica e melhora os teus conhecimentos.",year:"Escolhe o ano e a disciplina.",subjectNote:"Temas de referência. Algumas disciplinas aparecem como apoio nos anos em que não fazem parte da matriz curricular nacional; confirma a oferta da tua escola.",search:"🔎 Pesquisar disciplina ou tema...",topics:"temas",notFound:"Não foram encontrados resultados.",back:"← Voltar",summary:"Resumos",exercises:"Exercícios",complete:"Matéria e explicações",testprep:"Preparação para testes",practice:"Praticar",openGuide:"Abrir guia",note:"Nota:",contentNote:"Os conteúdos são guias de apoio ao estudo. Confirma sempre os tópicos e a profundidade da matéria com o manual e o professor.",question:"Pergunta",of:"de",correct:"Correto! ",incorrect:"Não está correto. ",result:"Resultado",right:"respostas certas.",retry:"Tentar novamente",next:"Próxima pergunta",showResult:"Ver resultado",emptyFav:"Ainda não guardaste favoritos.",footerNote:"Conteúdos de apoio ao estudo. Confirma sempre o programa da tua turma.",studyNote:"A interface e os conteúdos de estudo estão apresentados em português.",levels:["Fraco","Insuficiente","Suficiente","Bom","Muito Bom"],subjects:{"Matemática":"Matemática","Português":"Português","Ciências Naturais":"Ciências Naturais","Físico-Química":"Físico-Química","Inglês":"Inglês","Espanhol":"Espanhol","Geografia":"Geografia","História":"História","TIC":"TIC","Educação Física":"Educação Física","Educação Visual":"Educação Visual","Música":"Música"}},
en:{languageLabel:"Interface language",slogan:"The future starts now.",home:"Home",subjects:"Subjects",favorites:"Favourites",theme:"Theme",start:"Start studying",welcome:"Learn at your own pace. Study, practise and improve your knowledge.",year:"Choose a year and a subject.",subjectNote:"Reference topics. Some subjects may be offered as additional support rather than as part of the national curriculum; check your school’s offer.",search:"🔎 Search for a subject or topic...",topics:"topics",notFound:"No results found.",back:"← Back",summary:"Summaries",exercises:"Exercises",complete:"Study material",testprep:"Test preparation",practice:"Practise",openGuide:"Open guide",note:"Note:",contentNote:"These materials are study guides. Always check the topics and level of detail with your textbook and teacher.",question:"Question",of:"of",correct:"Correct! ",incorrect:"Not quite. ",result:"Result",right:"correct answers.",retry:"Try again",next:"Next question",showResult:"See result",emptyFav:"You have no saved favourites yet.",footerNote:"Study support material. Always check your class syllabus.",studyNote:"The interface, navigation and subject names are in English. Most lesson explanations and quiz questions are still in Portuguese.",levels:["Very poor","Insufficient","Satisfactory","Good","Very good"],subjects:{"Matemática":"Mathematics","Português":"Portuguese","Ciências Naturais":"Natural Sciences","Físico-Química":"Physics and Chemistry","Inglês":"English","Espanhol":"Spanish","Geografia":"Geography","História":"History","TIC":"ICT","Educação Física":"Physical Education","Educação Visual":"Visual Arts","Música":"Music"}},
es:{languageLabel:"Idioma de la interfaz",slogan:"El futuro empieza ahora.",home:"Inicio",subjects:"Asignaturas",favorites:"Favoritos",theme:"Tema",start:"Empezar a estudiar",welcome:"Aprende a tu ritmo. Estudia, practica y mejora tus conocimientos.",year:"Elige el curso y la asignatura.",subjectNote:"Temas de referencia. Algunas asignaturas pueden ofrecerse como apoyo adicional; consulta la oferta de tu centro.",search:"🔎 Buscar asignatura o tema...",topics:"temas",notFound:"No se encontraron resultados.",back:"← Volver",summary:"Resúmenes",exercises:"Ejercicios",complete:"Material de estudio",testprep:"Preparación para exámenes",practice:"Practicar",openGuide:"Abrir guía",note:"Nota:",contentNote:"Estos contenidos son guías de estudio. Comprueba siempre los temas y el nivel de detalle con el libro y el profesor.",question:"Pregunta",of:"de",correct:"¡Correcto! ",incorrect:"No es correcto. ",result:"Resultado",right:"respuestas correctas.",retry:"Intentar de nuevo",next:"Siguiente pregunta",showResult:"Ver resultado",emptyFav:"Todavía no has guardado favoritos.",footerNote:"Material de apoyo al estudio. Comprueba siempre el programa de tu clase.",studyNote:"La interfaz, la navegación y los nombres de las asignaturas están en español. La mayoría de las explicaciones y preguntas de los cuestionarios siguen en portugués.",levels:["Muy bajo","Insuficiente","Suficiente","Bien","Muy bien"],subjects:{"Matemática":"Matemáticas","Português":"Portugués","Ciências Naturais":"Ciencias Naturales","Físico-Química":"Física y Química","Inglês":"Inglés","Espanhol":"Español","Geografia":"Geografía","História":"Historia","TIC":"TIC","Educação Física":"Educación Física","Educação Visual":"Educación Visual","Música":"Música"}}
};
let currentLanguage=localStorage.getItem("sb_language")||"pt";
function tr(key){return (translations[currentLanguage]||translations.pt)[key]??translations.pt[key]??key}
function subjectLabel(name){return (translations[currentLanguage]||translations.pt).subjects[name]||name}
function setLanguage(lang){if(!translations[lang])lang="pt";currentLanguage=lang;localStorage.setItem("sb_language",lang);applyLanguage()}
function applyLanguage(){document.documentElement.lang=currentLanguage==="en"?"en":currentLanguage==="es"?"es":"pt-PT";document.getElementById("languageSelect").value=currentLanguage;document.getElementById("languageLabel").textContent=tr("languageLabel");document.getElementById("languageSelect").setAttribute("aria-label",tr("languageLabel"));
 document.getElementById("navHome").textContent="⌂ "+tr("home");document.getElementById("navSubjects").textContent="📚 "+tr("subjects");document.getElementById("navFavorites").textContent="★ "+tr("favorites");
 document.getElementById("themeBtn").textContent=(document.body.classList.contains("dark")?"☀️ ":"🌙 ")+tr("theme");
 document.getElementById("subjectsHeading").textContent=tr("subjects");document.getElementById("subjectsHint").textContent=tr("year");document.getElementById("subjectsNote").textContent=tr("subjectNote");document.getElementById("search").placeholder=tr("search");document.getElementById("favoritesHeading").textContent=tr("favorites");
 document.getElementById("backSubjects").textContent=tr("back");document.getElementById("backDetail").textContent=tr("back");
 document.getElementById("tabSummary").textContent=tr("summary");document.getElementById("tabExercises").textContent=tr("exercises");document.getElementById("tabComplete").textContent=tr("complete");document.getElementById("tabTestprep").textContent=tr("testprep");
 document.getElementById("contentNote").innerHTML="<strong>"+tr("note")+"</strong> "+tr("contentNote");document.getElementById("footerNote").textContent=tr("footerNote");document.getElementById("footerTag").textContent="Study Brain · "+tr("slogan")+" 💚";document.querySelector(".hero .muted").textContent=tr("slogan");
 document.getElementById("home").querySelector("p:nth-of-type(2)").textContent=tr("welcome");document.querySelector('#home button').textContent=tr("start");
 const y=document.getElementById("year");[6,7,8,9].forEach((n,i)=>y.options[i].text=currentLanguage==="en"?`${n}th grade`:currentLanguage==="es"?`${n}.º curso`:`${n}.º ano`);
 const credit=document.querySelector(".credit");if(credit)credit.textContent="Feito por Rafael Saraiva 💚";
 if(!document.getElementById("studyLanguageNote")){const n=document.createElement("div");n.id="studyLanguageNote";n.className="note";document.getElementById("lessonBody").after(n)}
 const n=document.getElementById("studyLanguageNote");n.textContent=currentLanguage==="pt"?"":"ℹ️ "+tr("studyNote");n.style.display=currentLanguage==="pt"?"none":"block";
 if(document.getElementById("subjects").classList.contains("page")&&!document.getElementById("subjects").classList.contains("hidden"))renderSubjects();
 if(document.getElementById("favorites").classList.contains("page")&&!document.getElementById("favorites").classList.contains("hidden"))renderFavorites();
 if(state.subject&&document.getElementById("detail").classList.contains("page")&&!document.getElementById("detail").classList.contains("hidden")){document.getElementById("subjectTitle").textContent=subjectLabel(state.subject);showTopics(state.mode);updateFav()}
}

const state={year:"9",subject:"",topic:"",mode:"summary",quiz:[],index:0,score:0};
function get(key,fallback){try{return JSON.parse(localStorage.getItem(key))??fallback}catch{return fallback}}
function page(id,btn){document.querySelectorAll(".page").forEach(x=>x.classList.add("hidden"));document.getElementById(id).classList.remove("hidden");if(btn){document.querySelectorAll("nav button").forEach(x=>x.classList.remove("active"));btn.classList.add("active")}if(id==="subjects")renderSubjects();if(id==="favorites")renderFavorites();window.scrollTo(0,0)}
function toggleTheme(){document.body.classList.toggle("dark");let d=document.body.classList.contains("dark");localStorage.setItem("sb_dark",d?"1":"0");document.getElementById("themeBtn").textContent=(d?"☀️ ":"🌙 ")+tr("theme")}
function renderSubjects(){state.year=document.getElementById("year").value;let norm=x=>x.toLocaleLowerCase().normalize("NFD").replace(/[\u0300-\u036f]/g,"");let q=norm(document.getElementById("search").value);let grid=document.getElementById("subjectGrid");grid.innerHTML="";subjects.forEach(([name,emoji])=>{let topics=curriculum[name][state.year]||[];if(!norm(name+" "+subjectLabel(name)).includes(q)&&!topics.some(t=>norm(t).includes(q)))return;let b=document.createElement("button");b.className="subject";b.innerHTML=`<span>${emoji}</span><strong>${subjectLabel(name)}</strong><span>${topics.length} ${tr("topics")}</span>`;b.onclick=()=>openSubject(name);grid.appendChild(b)});if(!grid.children.length)grid.textContent=tr("notFound")}
function openSubject(name){state.subject=name;document.getElementById("subjectTitle").textContent=subjectLabel(name);document.getElementById("yearLabel").textContent=currentLanguage==="en"?`${state.year}th grade`:currentLanguage==="es"?`${state.year}.º curso`:`${state.year}.º ano`;updateFav();page("detail");showTopics("summary")}
function showTopics(mode){state.mode=mode;let area=document.getElementById("topics");area.innerHTML="";let h=document.createElement("h2");h.textContent=tr(mode);area.appendChild(h);curriculum[state.subject][state.year].forEach(topic=>{let b=document.createElement("button");b.className="topic";b.innerHTML=`<strong>${topic}</strong><span>${(mode==="exercises"||mode==="testprep")?tr("practice"):tr("openGuide")}</span>`;b.onclick=()=>openLesson(topic,mode);area.appendChild(b)})}

function safeText(s){return String(s).replace(/[&<>"']/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]))}
function makeQ(q,a,c,e){return {q,a,c,e}}
function topicLibrary(subject,year,topic){
 const t=topic.toLowerCase();
 const lesson=(title,definition,points,example,warning,questions,keywords)=>({
  title,definition,points,example,warning,questions,keywords
 });
 const generic={
 "Matemática":lesson("Estratégia de resolução","Em Matemática, uma solução correta deve mostrar um raciocínio coerente, não apenas o resultado.",["Lê o enunciado e identifica os dados.","Determina o que é pedido.","Escolhe uma operação, propriedade ou representação adequada.","Resolve por etapas e verifica o resultado."],"Se um problema fornecer três valores e pedir um quarto, identifica primeiro a relação entre os valores antes de escolher a operação.","Não arredondes valores nem elimines unidades sem verificar se isso é permitido.",[makeQ("Qual é o primeiro passo para resolver um problema?",["Escolher uma resposta ao acaso","Identificar os dados e o que é pedido","Fazer todas as operações possíveis","Ignorar o enunciado"],1,"Os dados e a pergunta determinam a estratégia."),makeQ("Como verificas uma solução?",["Confirmando se responde ao problema e se os cálculos fazem sentido","Apagando os passos","Mudando os dados","Ignorando as unidades"],0,"A verificação permite detetar erros de cálculo ou interpretação.")],["Dados","Estratégia","Cálculo","Verificação"]),
 "Português":lesson("Leitura e análise","A compreensão de um texto implica identificar informação, interpretar sentidos e justificar as respostas com elementos do próprio texto.",["Lê o texto globalmente para perceber o assunto e a intenção.","Identifica ideias principais e informação de apoio.","Distingue informação explícita de inferências.","Justifica a interpretação com palavras ou passagens relevantes."],"Numa pergunta sobre a intenção do autor, não basta dizer o que pensas: relaciona a resposta com o tema, o tom e as escolhas de linguagem.","Evita apresentar uma opinião como se fosse informação explícita do texto.",[makeQ("Como justificas uma interpretação textual?",["Com uma passagem ou elemento do texto","Com uma opinião sem ligação ao texto","Com informação inventada","Sem responder ao pedido"],0,"A interpretação deve ser sustentada por elementos do texto."),makeQ("O que é uma ideia principal?",["Um detalhe sem importância","A informação central desenvolvida no texto","Sempre o título","Uma palavra desconhecida"],1,"A ideia principal resume o essencial do texto.")],["Assunto","Ideias principais","Inferência","Justificação"]),
 "Ciências Naturais":lesson("Compreender fenómenos naturais","As Ciências Naturais explicam fenómenos através de conceitos, observações e relações entre sistemas naturais e seres vivos.",["Define os conceitos científicos envolvidos.","Identifica os componentes do sistema em estudo.","Relaciona fatores e explica causas e consequências.","Interpreta esquemas, tabelas e resultados de observações."],"Ao analisar um ecossistema, identifica os seres vivos, os fatores não vivos e as relações que se estabelecem entre eles.","Uma correlação observada não prova, por si só, que um fator causou o outro.",[makeQ("O que deve incluir uma explicação científica?",["Apenas uma opinião","Conceitos corretos e relações apoiadas em evidências","Uma conclusão sem observações","Termos científicos sem significado"],1,"Uma explicação científica usa conceitos adequados e evidências."),makeQ("Para que serve interpretar um esquema científico?",["Para decorar as cores","Para compreender componentes e relações representadas","Para substituir todas as observações","Para ignorar legendas"],1,"O esquema representa informação e relações que devem ser interpretadas.")],["Conceitos","Observação","Evidência","Conclusão"]),
 "Físico-Química":lesson("Resolver problemas de Física e Química","A Físico-Química utiliza modelos, grandezas e evidências para explicar propriedades da matéria e fenómenos físicos e químicos.",["Identifica o fenómeno e as grandezas envolvidas.","Regista os dados com símbolos e unidades.","Escolhe a relação ou modelo adequado.","Substitui os valores, calcula e interpreta o resultado."],"Num problema quantitativo, apresenta os dados, a expressão utilizada, a substituição numérica e o resultado com unidade.","Não mistures unidades diferentes na mesma operação sem as converter primeiro.",[makeQ("O que deves fazer antes de substituir valores numa fórmula?",["Identificar grandezas, dados e unidade","Apagar as unidades","Escolher números aleatórios","Escrever o resultado"],0,"É necessário saber o significado e a unidade de cada grandeza."),makeQ("Porque se indica a unidade no resultado?",["É apenas decoração","Porque a unidade dá significado físico à grandeza","Para aumentar o cálculo","Porque substitui a explicação"],1,"O valor numérico sem unidade pode não representar corretamente a grandeza.")],["Grandezas","Unidades","Modelo","Interpretação"]),
 "História":lesson("Analisar acontecimentos históricos","A História estuda as sociedades no tempo e no espaço, procurando compreender mudanças, permanências e relações entre acontecimentos.",["Situa o acontecimento no período e no espaço.","Identifica os grupos sociais e protagonistas envolvidos.","Distingue causas, acontecimentos e consequências.","Interpreta fontes considerando autoria, data, contexto e objetivo."],"Ao estudar uma transformação histórica, organiza a explicação em contexto anterior, fatores que contribuíram para a mudança e consequências.","Não confundas a data de um acontecimento com a explicação das suas causas.",[makeQ("O que é uma fonte histórica?",["Um documento ou vestígio que fornece informação sobre o passado","Uma opinião atual sem relação com o passado","Uma data isolada","Uma previsão"],0,"As fontes históricas são vestígios usados para estudar o passado."),makeQ("O que ajuda a explicar um acontecimento?",["Apenas decorar a data","Relacionar contexto, causas e consequências","Ignorar os protagonistas","Usar apenas uma opinião"],1,"A contextualização permite compreender o significado do acontecimento.")],["Cronologia","Contexto","Causas","Consequências"]),
 "Geografia":lesson("Interpretar o espaço geográfico","A Geografia analisa a distribuição dos fenómenos naturais e humanos e as relações entre população, atividades e território.",["Localiza o fenómeno e identifica a escala de análise.","Lê o título, a legenda, a orientação e a escala do mapa.","Descreve padrões e compara áreas ou valores.","Explica a distribuição relacionando fatores naturais e humanos."],"Ao interpretar um mapa temático, começa por dizer o que representa e onde se observam valores maiores ou menores; depois procura explicar essa distribuição.","Não tires conclusões sem consultar a legenda, a escala e a fonte.",[makeQ("O que deves consultar primeiro num mapa temático?",["Apenas as cores","Título e legenda","O nome do ficheiro","A última página do manual"],1,"O título e a legenda explicam o assunto e o significado dos símbolos."),makeQ("O que significa descrever uma distribuição geográfica?",["Indicar onde os fenómenos se concentram ou são menos frequentes","Dar uma opinião pessoal","Indicar apenas uma cidade","Ignorar diferenças regionais"],0,"Descrever a distribuição é identificar padrões espaciais.")],["Localização","Escala","Legenda","Distribuição"]),
 "Inglês":lesson("Reading and communication","Understanding a topic in English means using vocabulary in context and communicating ideas in clear, accurate sentences.",["Read the text once to understand the general idea.","Identify key words and use context to infer meaning.","Notice verb forms, word order and connectors.","Write complete sentences and check spelling and punctuation."],"Write two original sentences using the topic vocabulary. Then check subject–verb agreement and whether the sentence expresses the intended meaning.","Do not translate every word automatically; use the context to understand the message.",[makeQ("What is the best way to understand an unfamiliar word?",["Ignore the whole text","Use context clues and nearby words","Choose a meaning at random","Stop reading"],1,"Context often helps you infer the meaning of a word."),makeQ("What should you check when writing?",["Only the length","Word order, verb forms and spelling","Only the title","Nothing"],1,"Clear writing requires correct structure and spelling.")],["Vocabulary","Context","Grammar","Communication"]),
 "Espanhol":lesson("Compreender e comunicar em espanhol","A aprendizagem do espanhol envolve compreender mensagens e utilizar vocabulário e estruturas gramaticais em contexto.",["Identifica o tema e as palavras-chave.","Observa artigos, género, número e concordância.","Verifica a conjugação verbal e a ordem das palavras.","Constrói frases completas e revê os acentos."],"Escreve duas frases originais relacionadas com o tema e confirma a concordância entre o nome e o adjetivo.","Atenção às palavras parecidas com o português: podem ter significados diferentes.",[makeQ("O que deves verificar numa frase em espanhol?",["Apenas o número de palavras","Concordância e forma verbal","Só a primeira letra","Nada"],1,"A concordância e a conjugação são essenciais para construir frases corretas."),makeQ("Como podes inferir o significado de uma palavra?",["Pelo contexto da frase","Escolhendo ao acaso","Ignorando a frase","Usando sempre a tradução literal"],0,"O contexto ajuda a compreender o significado.")],["Vocabulario","Contexto","Concordancia","Verbos"]),
 "TIC":lesson("Utilização crítica e segura das tecnologias","As tecnologias digitais devem ser utilizadas com objetivos claros, sentido crítico e respeito pela segurança e pelos direitos de autor.",["Define o objetivo antes de escolher uma ferramenta.","Organiza ficheiros e informação de forma lógica.","Avalia a credibilidade, atualidade e autoria das fontes.","Protege palavras-passe e dados pessoais e respeita licenças."],"Antes de partilhares informação, confirma a fonte, verifica se tens autorização para utilizar os materiais e remove dados pessoais desnecessários.","Não publiques palavras-passe, moradas, contactos ou dados privados.",[makeQ("Como avalias uma fonte digital?",["Pelo aspeto colorido","Pela autoria, data, evidências e credibilidade","Pelo número de emojis","Por ser o primeiro resultado"],1,"A credibilidade depende da autoria, atualidade e qualidade da informação."),makeQ("Qual é uma prática segura?",["Partilhar a palavra-passe","Publicar dados pessoais","Utilizar palavras-passe fortes e não as partilhar","Abrir qualquer anexo"],2,"Proteger credenciais e dados pessoais reduz riscos digitais.")],["Pesquisa","Credibilidade","Privacidade","Direitos de autor"]),
 "Educação Física":lesson("Prática motora, regras e cooperação","A Educação Física desenvolve capacidades motoras e promove a participação, o respeito pelas regras e a segurança.",["Conhece o objetivo e as regras da atividade.","Executa os movimentos com controlo e atenção às indicações.","Adapta decisões à situação de jogo ou exercício.","Coopera, respeita os colegas e pratica em segurança."],"Numa atividade coletiva, observa o espaço, comunica com os colegas e escolhe uma ação adequada à situação, respeitando as regras.","A segurança e o respeito pelos outros são mais importantes do que ganhar.",[makeQ("O que é essencial numa prática segura?",["Ignorar as regras","Respeitar regras e indicações","Empurrar os colegas","Não fazer aquecimento"],1,"As regras e as indicações ajudam a prevenir acidentes."),makeQ("O que demonstra cooperação?",["Impedir os outros de participar","Comunicar e respeitar os colegas","Ignorar a equipa","Não cumprir regras"],1,"A cooperação envolve comunicação e respeito.")],["Regras","Técnica","Cooperação","Segurança"]),
 "Educação Visual":lesson("Comunicação e linguagem visual","A linguagem visual utiliza elementos como linha, forma, cor, textura, luz e composição para comunicar ideias.",["Identifica os elementos visuais presentes.","Observa a organização e a hierarquia da composição.","Relaciona as escolhas visuais com a mensagem.","Experimenta soluções e revê o resultado."],"Num cartaz, o título pode ter maior destaque através do tamanho, contraste e posição, orientando a leitura do observador.","Uma composição deve ser pensada em função da mensagem, não apenas da decoração.",[makeQ("Que elemento ajuda a criar contraste visual?",["A utilização de diferenças de cor, tamanho ou forma","A repetição sem intenção","A ausência de organização","A eliminação da mensagem"],0,"O contraste diferencia elementos e ajuda a criar hierarquia."),makeQ("O que é composição visual?",["A organização dos elementos numa imagem","Apenas a escolha do papel","O nome do artista","A assinatura"],0,"A composição é a forma como os elementos visuais são organizados.")],["Linha","Forma","Cor","Composição"]),
 "Música":lesson("Escuta e organização dos sons","A música organiza sons e silêncios através de elementos como ritmo, melodia, timbre, intensidade e andamento.",["Escuta a peça mais do que uma vez.","Identifica padrões rítmicos e melódicos.","Distingue timbres e alterações de intensidade.","Relaciona os elementos com o carácter da música."],"Ao comparar dois excertos, observa se o andamento é mais rápido ou lento e se a intensidade aumenta ou diminui.","Não confundas intensidade (forte/fraco) com altura (grave/agudo).",[makeQ("O que descreve a intensidade sonora?",["Se o som é forte ou fraco","Se o som é grave ou agudo","A duração da música","O instrumento utilizado"],0,"A intensidade está relacionada com a força com que o som é ouvido."),makeQ("O que é o timbre?",["A característica que permite distinguir fontes sonoras","A velocidade da música","A letra da canção","O volume apenas"],0,"O timbre permite distinguir sons de diferentes fontes.")],["Ritmo","Melodia","Timbre","Intensidade"])
 };
 let d=null;
 if(subject==="Matemática"){
  if(/fraç|raciona/.test(t)&&/opera|fraç|raciona/.test(t)){
   d=lesson("Frações e números racionais","Uma fração representa uma ou mais partes iguais de uma unidade. O numerador indica quantas partes se consideram e o denominador em quantas partes iguais a unidade foi dividida.",["Frações equivalentes representam o mesmo valor.","Para somar ou subtrair, usa denominadores iguais; se necessário, determina um denominador comum.","Na multiplicação, multiplica numeradores entre si e denominadores entre si.","Na divisão, multiplica pela fração inversa do divisor."],"(1/2)+(1/4)=2/4+1/4=3/4. Na multiplicação: (2/3)×(3/5)=6/15=2/5.","Nunca somes numeradores e denominadores diretamente: 1/2+1/3 não é 2/5.",[makeQ("Quanto é 1/2 + 1/4?",["2/6","3/4","1/6","2/4"],1,"1/2 equivale a 2/4; 2/4+1/4=3/4."),makeQ("Quanto é (2/3) × (3/5)?",["5/8","6/15","5/6","2/5"],1,"Multiplica numeradores e denominadores: 6/15, que simplifica para 2/5.")],["Numerador","Denominador","Equivalência","Simplificação"]);
  } else if(/percent/.test(t)){
   d=lesson("Percentagens","Uma percentagem é uma razão com denominador 100. Assim, 25% corresponde a 25/100, ou seja, 0,25.",["Para converter percentagem em decimal, divide por 100.","Para calcular p% de um valor, multiplica o valor por p/100.","Um aumento de 10% corresponde a multiplicar por 1,10.","Uma diminuição de 10% corresponde a multiplicar por 0,90."],"25% de 80 = 0,25×80 = 20. Um aumento de 10% em 80 dá 80×1,10 = 88.","Um aumento de 10% seguido de uma diminuição de 10% não devolve o valor inicial.",[makeQ("Quanto é 20% de 50?",["5","10","20","25"],1,"20/100×50=10."),makeQ("Como representas 35% em número decimal?",["3,5","0,35","0,035","35"],1,"35% = 35/100 = 0,35.")],["Por cento","Razão","Decimal","Aumento e redução"]);
  } else if(/equação do 2|segundo grau/.test(t)){
   d=lesson("Equações do 2.º grau","Uma equação do 2.º grau pode escrever-se na forma ax²+bx+c=0, com a diferente de zero.",["Identifica os coeficientes a, b e c.","Calcula o discriminante: Δ=b²−4ac.","Se Δ>0, existem duas soluções reais distintas; se Δ=0, uma solução real dupla; se Δ<0, não existem soluções reais.","Aplica a fórmula resolvente x=(-b±√Δ)/(2a)."],"Em x²−5x+6=0, a=1, b=−5 e c=6. Δ=25−24=1. As soluções são x=(5±1)/2, isto é, x=3 ou x=2.","Confirma sempre os sinais dos coeficientes, sobretudo quando b ou c são negativos.",[makeQ("Qual é o discriminante de x²−5x+6=0?",["1","5","−1","25"],0,"Δ=b²−4ac=25−24=1."),makeQ("Quantas soluções reais distintas existem se Δ>0?",["Nenhuma","Uma","Duas","Infinitas"],2,"Um discriminante positivo corresponde a duas soluções reais distintas.")],["Coeficientes","Discriminante","Fórmula resolvente","Soluções"]);
  } else if(/pitágoras/.test(t)){
   d=lesson("Teorema de Pitágoras","Num triângulo retângulo, o quadrado da hipotenusa é igual à soma dos quadrados dos catetos: a²+b²=c².",["A hipotenusa é o lado oposto ao ângulo reto e é o maior lado.","Os catetos são os lados que formam o ângulo reto.","Para determinar a hipotenusa, calcula √(a²+b²).","Para determinar um cateto, calcula √(c²−outro cateto²)."],"Se os catetos medem 3 cm e 4 cm, c²=3²+4²=9+16=25; logo c=5 cm.","O teorema aplica-se a triângulos retângulos, não a qualquer triângulo.",[makeQ("Num triângulo retângulo com catetos 3 e 4, quanto mede a hipotenusa?",["5","6","7","12"],0,"3²+4²=9+16=25; √25=5."),makeQ("Qual é a hipotenusa?",["O lado menor","O lado oposto ao ângulo reto","Qualquer cateto","O lado que forma o ângulo reto"],1,"A hipotenusa fica sempre oposta ao ângulo reto.")],["Triângulo retângulo","Catetos","Hipotenusa","Quadrados"]);
  } else if(/trigonometria/.test(t)){
   d=lesson("Trigonometria no triângulo retângulo","Num triângulo retângulo, as razões trigonométricas relacionam um ângulo agudo com os comprimentos dos lados.",["sen(α)=cateto oposto/hipotenusa.","cos(α)=cateto adjacente/hipotenusa.","tan(α)=cateto oposto/cateto adjacente.","Escolhe a razão que relaciona os lados conhecidos com o lado procurado."],"Se, relativamente ao ângulo α, o cateto oposto mede 3 e a hipotenusa 5, então sen(α)=3/5=0,6.","Identifica sempre o ângulo de referência antes de decidir qual é o cateto oposto e o adjacente.",[makeQ("O seno de um ângulo é:",["Cateto adjacente/hipotenusa","Cateto oposto/hipotenusa","Cateto oposto/cateto adjacente","Hipotenusa/cateto oposto"],1,"Por definição, sen(α)=cateto oposto/hipotenusa."),makeQ("Qual é a hipotenusa?",["O lado oposto ao ângulo reto","O cateto adjacente","O cateto oposto","O lado mais curto"],0,"A hipotenusa é o lado oposto ao ângulo de 90°.")],["Seno","Cosseno","Tangente","Ângulo"]);
  } else if(/potênci/.test(t)){
   d=lesson("Potências","Uma potência representa uma multiplicação de fatores iguais. Em aⁿ, a é a base e n é o expoente.",["a² significa a×a; a³ significa a×a×a.","Produto de potências com a mesma base: somam-se os expoentes.","Quociente de potências com a mesma base: subtraem-se os expoentes, se a base for não nula.","Potência de potência: multiplicam-se os expoentes."],"2³×2²=2⁵=32. E (3²)³=3⁶.","As regras do produto e quociente indicadas exigem a mesma base.",[makeQ("Quanto é 2³×2²?",["2⁶","2⁵","2¹","4⁵"],1,"Com a mesma base, somam-se os expoentes: 2⁵."),makeQ("Quanto é (3²)³?",["3⁵","3⁶","3⁸","3⁹"],1,"Na potência de potência, multiplicam-se os expoentes: 3⁶.")],["Base","Expoente","Produto","Quociente"]);
  } else if(/equações do 1|equações/.test(t)){
   d=lesson("Equações do 1.º grau","Uma equação é uma igualdade com uma ou mais incógnitas. Resolver é encontrar o valor que torna a igualdade verdadeira.",["Simplifica os dois membros, se necessário.","Usa operações equivalentes nos dois membros para isolar a incógnita.","Verifica a solução substituindo-a na equação inicial."],"3x+5=20 → 3x=15 → x=5. Verificação: 3×5+5=20.","Quando passas um termo para o outro membro, o sinal muda porque estás a aplicar a operação inversa aos dois membros.",[makeQ("Qual é a solução de 3x+5=20?",["3","5","8","15"],1,"Subtrai 5: 3x=15; divide por 3: x=5."),makeQ("Como verificas uma solução?",["Substituindo-a na equação original","Mudando a incógnita","Apagando a equação","Dividindo apenas um membro"],0,"A solução deve tornar a igualdade verdadeira.")],["Incógnita","Equivalência","Operação inversa","Verificação"]);
  } else if(/proporcionalidade direta/.test(t)){
   d=lesson("Proporcionalidade direta","Duas grandezas são diretamente proporcionais quando o quociente entre valores correspondentes é constante. A relação pode escrever-se y=kx.",["A constante k é a constante de proporcionalidade.","Se uma grandeza duplica, a outra também duplica.","O gráfico é uma reta que passa na origem.","Determina k dividindo y por x."],"Se 2 cadernos custam 4 €, cada caderno custa 2 €. Para 5 cadernos: 5×2=10 €.","Não confundas proporcionalidade direta com qualquer relação crescente.",[makeQ("Numa relação y=3x, qual é y quando x=4?",["7","12","1","34"],1,"y=3×4=12."),makeQ("O gráfico de uma função de proporcionalidade direta é:",["Uma reta que passa na origem","Uma circunferência","Sempre uma parábola","Uma reta vertical"],0,"A expressão y=kx representa uma reta que passa na origem.")],["Constante k","Razão","Tabela","Gráfico"]);
  } else if(/proporcionalidade inversa/.test(t)){
   d=lesson("Proporcionalidade inversa","Duas grandezas são inversamente proporcionais quando o produto dos valores correspondentes é constante: x×y=k.",["Se uma grandeza duplica, a outra reduz-se para metade.","O produto dos valores correspondentes mantém-se constante.","A relação pode escrever-se y=k/x, com x diferente de zero."],"Se 2 pessoas fazem uma tarefa em 6 horas, 4 pessoas, ao mesmo ritmo, demorariam 3 horas: 2×6=4×3=12.","A relação inversa pressupõe condições constantes, como o mesmo ritmo de trabalho.",[makeQ("Se x×y=24 e x=6, quanto vale y?",["4","18","30","144"],0,"y=24/6=4."),makeQ("Numa proporcionalidade inversa, se x duplica, y:",["Duplica","Mantém-se","Fica reduzido a metade","Fica zero"],2,"O produto constante exige que a outra grandeza diminua na mesma proporção.")],["Produto constante","Inversa","Tabela","Gráfico"]);
  } else if(/função afim/.test(t)){
   d=lesson("Função afim","Uma função afim tem a expressão f(x)=mx+b. O gráfico é uma reta; m representa o declive e b a ordenada na origem.",["Se m>0, a função é crescente; se m<0, é decrescente.","O valor b indica onde a reta interseta o eixo dos yy.","Para construir o gráfico, calcula alguns pares (x,f(x))."],"Em f(x)=2x+1, o declive é 2 e a ordenada na origem é 1. Para x=2, f(2)=5.","Não confundas o declive com a ordenada na origem.",[makeQ("Na função f(x)=3x−2, qual é o declive?",["−2","3","2","−3"],1,"O coeficiente de x é o declive: m=3."),makeQ("Qual é a ordenada na origem de f(x)=3x−2?",["3","−2","1","0"],1,"A ordenada na origem é b=−2.")],["Declive","Ordenada na origem","Reta","Tabela"]);
  } else if(/áreas e volumes|áreas de|perímetro|volume/.test(t)){
   d=lesson("Perímetros, áreas e volumes","O perímetro mede o comprimento do contorno, a área mede a superfície e o volume mede o espaço ocupado por um sólido.",["Retângulo: A=b×h e P=2b+2h.","Triângulo: A=(base×altura)/2.","Paralelogramo: A=base×altura.","Prisma: V=área da base×altura."],"Um retângulo com 5 cm de comprimento e 3 cm de largura tem área 15 cm² e perímetro 16 cm.","Área mede-se em unidades quadradas; volume em unidades cúbicas. Não confundas as unidades.",[makeQ("Qual é a área de um retângulo 5 cm × 3 cm?",["8 cm²","15 cm²","16 cm²","30 cm²"],1,"A=5×3=15 cm²."),makeQ("Em que unidade se expressa o volume?",["cm","cm²","cm³","kg"],2,"O volume mede espaço e usa unidades cúbicas.")],["Perímetro","Área","Volume","Unidades"]);
  } else if(/probabilidades/.test(t)){
   d=lesson("Probabilidades","Num modelo de resultados equiprováveis, a probabilidade de um acontecimento é o quociente entre o número de casos favoráveis e o número de casos possíveis.",["A probabilidade varia entre 0 e 1.","Um acontecimento impossível tem probabilidade 0; um certo tem probabilidade 1.","P(A)=casos favoráveis/casos possíveis, quando os resultados são equiprováveis."],"Ao lançar um dado equilibrado, a probabilidade de sair um número par é 3/6=1/2.","A fórmula simples exige que os resultados considerados sejam equiprováveis.",[makeQ("Num dado equilibrado, qual é a probabilidade de sair 6?",["1/2","1/3","1/6","6"],2,"Há um caso favorável em seis resultados possíveis."),makeQ("Uma probabilidade pode ser:",["−1","1,5","0,4","3"],2,"As probabilidades estão entre 0 e 1.")],["Acontecimento","Casos favoráveis","Casos possíveis","Equiprovável"]);
  } else if(/média|medidas estatísticas|tratamento de dados|análise de dados/.test(t)){
   d=lesson("Organização e análise de dados","A Estatística permite recolher, organizar, representar e interpretar dados para responder a questões.",["Média: soma dos valores dividida pelo número de valores.","Mediana: valor central depois de ordenar os dados; se houver quantidade par, é a média dos dois centrais.","Moda: valor mais frequente.","Amplitude: diferença entre o maior e o menor valor."],"Nos dados 2, 3, 3, 8, a média é 4, a mediana é 3 e a moda é 3.","A mediana exige ordenar os dados antes de identificar o valor central.",[makeQ("Qual é a média de 2, 4 e 6?",["3","4","6","12"],1,"(2+4+6)/3=4."),makeQ("Qual é a moda de 1, 2, 2, 5?",["1","2","2,5","5"],1,"O valor 2 é o que aparece mais vezes.")],["Média","Mediana","Moda","Amplitude"]);
  }
 }
 if(!d)d=generic[subject]||generic["Ciências Naturais"];
 return d;
}
function renderTopicLesson(subject,year,topic,mode){
 const d=topicLibrary(subject,year,topic);
 const points=d.points.map(x=>`<li>${safeText(x)}</li>`).join("");
 const keywords=d.keywords.map(x=>`<span>${safeText(x)}</span>`).join("");
 let out=`<div class="definition"><strong>${safeText(d.title)}</strong><p>${safeText(d.definition)}</p></div><h3>O que precisas de saber</h3><ul>${points}</ul><h3>Exemplo explicado</h3><div class="example">${safeText(d.example)}</div>`;
 if(d.warning)out+=`<div class="warning"><strong>Atenção:</strong> ${safeText(d.warning)}</div>`;
 out+=`<h3>Palavras-chave</h3><div class="keyline">${keywords}</div><h3>Verifica a tua compreensão</h3><p>Antes de avançar, tenta explicar o conceito principal sem consultar o texto e resolve um exemplo semelhante.</p>`;
 if(mode==="summary")out=`<div class="definition"><strong>${safeText(d.title)}</strong><p>${safeText(d.definition)}</p></div><h3>Essencial</h3><ul>${points}</ul><div class="example"><strong>Exemplo:</strong> ${safeText(d.example)}</div>`;
 if(mode==="exercises"||mode==="testprep"){
  document.getElementById("exerciseArea").innerHTML=mode==="testprep"?'<div class="note"><strong>Preparação para o teste:</strong> responde sem consultar a matéria. No fim, vê as correções e volta a estudar os pontos em que tiveste dúvidas.</div>':'';
 }
 return out;
}
function openLesson(topic,mode){
 state.topic=topic;
 document.getElementById("lessonTitle").textContent=topic;
 const body=document.getElementById("lessonBody"),area=document.getElementById("exerciseArea");
 body.innerHTML="";area.innerHTML="";
 if(state.subject==="Matemática"&&cases[topic]&&topic==="Casos notáveis da multiplicação"){
  const c=cases[topic];
  body.innerHTML=mode==="summary"?`<p>${c.summary}</p>`:c.complete;
  if(mode==="exercises"||mode==="testprep")startQuiz([...c.questions].sort(()=>Math.random()-.5));
 }else{
  const d=topicLibrary(state.subject,state.year,topic);
  body.innerHTML=renderTopicLesson(state.subject,state.year,topic,mode);
  if(mode==="exercises"||mode==="testprep")startQuiz([...d.questions].sort(()=>Math.random()-.5));
 }
 page("study");
}
function startQuiz(qs){state.quiz=qs;state.index=0;state.score=0;renderQuestion()}
function renderQuestion(){let area=document.getElementById("exerciseArea");area.innerHTML="";let q=state.quiz[state.index];let meta=document.createElement("p");meta.className="quiz-meta";meta.textContent=`${tr("question")} ${state.index+1} ${tr("of")} ${state.quiz.length}`;area.appendChild(meta);let progress=document.createElement("div");progress.className="quiz-progress";progress.innerHTML=`<span style="width:${(state.index/state.quiz.length)*100}%"></span>`;area.appendChild(progress);let h=document.createElement("h3");h.textContent=q.q;area.appendChild(h);q.a.forEach((a,i)=>{let b=document.createElement("button");b.className="answer";b.textContent=a;b.setAttribute("aria-label",`Resposta ${i+1}: ${a}`);b.onclick=()=>answer(i);area.appendChild(b)})}
function answer(choice){let q=state.quiz[state.index];document.querySelectorAll(".answer").forEach((b,i)=>{b.disabled=true;if(i===q.c)b.classList.add("correct");if(i===choice&&i!==q.c)b.classList.add("wrong")});if(choice===q.c)state.score++;let area=document.getElementById("exerciseArea");let note=document.createElement("div");note.className="note";note.textContent=(choice===q.c?tr("correct"):tr("incorrect"))+q.e;area.appendChild(note);let next=document.createElement("button");next.textContent=state.index===state.quiz.length-1?tr("showResult"):tr("next");next.onclick=()=>{state.index++;if(state.index<state.quiz.length)renderQuestion();else result()};area.appendChild(next)}
function result(){let p=Math.round(state.score/state.quiz.length*100);let level=p<20?tr("levels")[0]:p<50?tr("levels")[1]:p<70?tr("levels")[2]:p<90?tr("levels")[3]:tr("levels")[4];let area=document.getElementById("exerciseArea");area.innerHTML=`<h2>${tr("result")}</h2><h1>${p}%</h1><p>${state.score} ${tr("of")} ${state.quiz.length} ${tr("right")}</p><strong>${level}</strong>`;let history=get("sb_history",[]);history.unshift({date:new Date().toLocaleString(currentLanguage==="en"?"en-GB":currentLanguage==="es"?"es-ES":"pt-PT"),year:state.year,subject:state.subject,topic:state.topic,percent:p});localStorage.setItem("sb_history",JSON.stringify(history.slice(0,100)));let b=document.createElement("button");b.textContent=tr("retry");b.onclick=()=>startQuiz([...state.quiz].sort(()=>Math.random()-.5));area.appendChild(b)}
function favKey(){return state.year+"|"+state.subject}
function toggleFavorite(){let fav=get("sb_favorites",[]),key=favKey();fav=fav.includes(key)?fav.filter(x=>x!==key):[...fav,key];localStorage.setItem("sb_favorites",JSON.stringify(fav));updateFav();renderFavorites()}
function updateFav(){document.getElementById("favBtn").textContent=get("sb_favorites",[]).includes(favKey())?(currentLanguage==="en"?"★ Saved":currentLanguage==="es"?"★ Guardado":"★ Guardado"):(currentLanguage==="en"?"☆ Save":currentLanguage==="es"?"☆ Guardar":"☆ Guardar")}
function renderFavorites(){let grid=document.getElementById("favoriteGrid");grid.innerHTML="";get("sb_favorites",[]).forEach(key=>{let [year,name]=key.split("|");let emoji=subjects.find(s=>s[0]===name)?.[1]||"📚";let b=document.createElement("button");b.className="subject";b.innerHTML=`<span>${emoji}</span><strong>${subjectLabel(name)}</strong><span>${currentLanguage==="en"?`${year}th grade`:currentLanguage==="es"?`${year}.º curso`:`${year}.º ano`}</span>`;b.onclick=()=>{state.year=year;document.getElementById("year").value=year;openSubject(name)};grid.appendChild(b)});if(!grid.children.length)grid.textContent=tr("emptyFav")}
if(localStorage.getItem("sb_dark")==="1")document.body.classList.add("dark");
applyLanguage();renderSubjects();
</script>
</body>
</html>
