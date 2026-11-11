<!DOCTYPE html>
<html lang="pt">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Study Brain</title>
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
</style>
</head>
<body>
<header>
<div class="brand"><span class="logo">🧠</span>Study Brain</div>
<button class="ghost" onclick="toggleTheme()" id="themeBtn">🌙 Tema</button>
</header>
<nav>
<button class="active" onclick="page('home',this)">⌂ Início</button>
<button onclick="page('subjects',this)">📚 Disciplinas</button>
<button onclick="page('favorites',this)">★ Favoritos</button>
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
<div class="row"><div><h1>Disciplinas</h1><p class="muted">Escolhe o ano e a disciplina.</p><p class="muted">Temas de referência. Algumas disciplinas aparecem como apoio nos anos em que não fazem parte da matriz curricular nacional; confirma a oferta da tua escola.</p></div>
<select id="year" onchange="renderSubjects()">
<option value="6">6.º ano</option><option value="7">7.º ano</option><option value="8">8.º ano</option><option value="9" selected>9.º ano</option>
</select></div>
<input id="search" placeholder="🔎 Pesquisar disciplina ou tema..." oninput="renderSubjects()">
<div id="subjectGrid" class="grid"></div>
</section>

<section id="favorites" class="page hidden">
<h1>Favoritos</h1><div id="favoriteGrid" class="grid"></div>
</section>

<section id="detail" class="page hidden">
<button class="secondary" onclick="page('subjects')">← Voltar</button>
<div class="panel">
<div class="row"><div><p id="yearLabel" class="muted"></p><h1 id="subjectTitle"></h1></div><button class="ghost" id="favBtn" onclick="toggleFavorite()">☆ Guardar</button></div>
<div class="actions">
<button onclick="showTopics('summary')">Resumos</button>
<button class="secondary" onclick="showTopics('exercises')">Exercícios</button>
<button class="secondary" onclick="showTopics('complete')">Matéria completa</button>
</div>
<div id="topics"></div>
</div>
</section>

<section id="study" class="page hidden">
<button class="secondary" onclick="page('detail')">← Voltar</button>
<div class="panel">
<h1 id="lessonTitle"></h1>
<div id="lessonBody" class="lesson"></div>
<div id="exerciseArea"></div>
</div>
</section>
</main>
<footer>Study Brain · O futuro começa agora. 💚</footer>

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

const state={year:"9",subject:"",topic:"",mode:"summary",quiz:[],index:0,score:0};
function get(key,fallback){try{return JSON.parse(localStorage.getItem(key))??fallback}catch{return fallback}}
function page(id,btn){document.querySelectorAll(".page").forEach(x=>x.classList.add("hidden"));document.getElementById(id).classList.remove("hidden");if(btn){document.querySelectorAll("nav button").forEach(x=>x.classList.remove("active"));btn.classList.add("active")}if(id==="subjects")renderSubjects();if(id==="favorites")renderFavorites();window.scrollTo(0,0)}
function toggleTheme(){document.body.classList.toggle("dark");let d=document.body.classList.contains("dark");localStorage.setItem("sb_dark",d?"1":"0");document.getElementById("themeBtn").textContent=d?"☀️ Tema":"🌙 Tema"}
function renderSubjects(){state.year=document.getElementById("year").value;let q=document.getElementById("search").value.toLowerCase();let grid=document.getElementById("subjectGrid");grid.innerHTML="";subjects.forEach(([name,emoji])=>{let topics=curriculum[name][state.year]||[];if(!name.toLowerCase().includes(q)&&!topics.some(t=>t.toLowerCase().includes(q)))return;let b=document.createElement("button");b.className="subject";b.innerHTML=`<span>${emoji}</span><strong>${name}</strong><span>${topics.length} temas</span>`;b.onclick=()=>openSubject(name);grid.appendChild(b)});if(!grid.children.length)grid.textContent="Não foram encontrados resultados."}
function openSubject(name){state.subject=name;document.getElementById("subjectTitle").textContent=name;document.getElementById("yearLabel").textContent=state.year+".º ano";updateFav();page("detail");showTopics("summary")}
function showTopics(mode){state.mode=mode;let area=document.getElementById("topics");area.innerHTML="";let h=document.createElement("h2");h.textContent=mode==="exercises"?"Exercícios":mode==="complete"?"Matéria completa":"Resumos";area.appendChild(h);curriculum[state.subject][state.year].forEach(topic=>{let b=document.createElement("button");b.className="topic";b.innerHTML=`<strong>${topic}</strong><span>${mode==="exercises"?"Praticar":"Abrir matéria"}</span>`;b.onclick=()=>openLesson(topic,mode);area.appendChild(b)})}
function openLesson(topic,mode){state.topic=topic;document.getElementById("lessonTitle").textContent=topic;let body=document.getElementById("lessonBody");body.innerHTML="";let area=document.getElementById("exerciseArea");area.innerHTML="";if(state.subject==="Matemática"&&topic==="Casos notáveis da multiplicação"){if(mode==="summary"){body.innerHTML="<p>Os <strong>casos notáveis</strong> são fórmulas que permitem desenvolver produtos algébricos rapidamente.</p><div class='formula'>(a+b)² = a² + 2ab + b²</div><div class='formula'>(a-b)² = a² - 2ab + b²</div><div class='formula'>(a+b)(a-b) = a² - b²</div>"}else if(mode==="complete"){body.innerHTML=cases[topic].complete}else{body.innerHTML="<p>Revê as fórmulas e resolve as perguntas seguintes.</p>";startQuiz(cases[topic].questions)}}else{let content=generic[state.subject];body.innerHTML=mode==="summary"?`<p>${content.summary}</p>`:content.complete;if(mode==="exercises"){let qs=cases[topic]?.questions||[];if(qs.length)startQuiz(qs);else area.innerHTML="<p class='muted'>Ainda não existem perguntas específicas para este tema.</p>"}}page("study")}
function startQuiz(qs){state.quiz=qs;state.index=0;state.score=0;renderQuestion()}
function renderQuestion(){let area=document.getElementById("exerciseArea");area.innerHTML="";let q=state.quiz[state.index];let h=document.createElement("h3");h.textContent=`Pergunta ${state.index+1}/${state.quiz.length}: ${q.q}`;area.appendChild(h);q.a.forEach((a,i)=>{let b=document.createElement("button");b.className="answer";b.textContent=a;b.onclick=()=>answer(i);area.appendChild(b)})}
function answer(choice){let q=state.quiz[state.index];document.querySelectorAll(".answer").forEach((b,i)=>{b.disabled=true;if(i===q.c)b.classList.add("correct");if(i===choice&&i!==q.c)b.classList.add("wrong")});if(choice===q.c)state.score++;let area=document.getElementById("exerciseArea");let note=document.createElement("div");note.className="note";note.textContent=(choice===q.c?"Correto! ":"Não está correto. ")+q.e;area.appendChild(note);let next=document.createElement("button");next.textContent=state.index===state.quiz.length-1?"Ver resultado":"Próxima pergunta";next.onclick=()=>{state.index++;if(state.index<state.quiz.length)renderQuestion();else result()};area.appendChild(next)}
function result(){let p=Math.round(state.score/state.quiz.length*100);let level=p<20?"Fraco":p<50?"Insuficiente":p<70?"Suficiente":p<90?"Bom":"Muito Bom";let area=document.getElementById("exerciseArea");area.innerHTML=`<h2>Resultado</h2><h1>${p}%</h1><p>${state.score} de ${state.quiz.length} respostas certas.</p><strong>${level}</strong>`;let history=get("sb_history",[]);history.unshift({date:new Date().toLocaleString("pt-PT"),year:state.year,subject:state.subject,topic:state.topic,percent:p});localStorage.setItem("sb_history",JSON.stringify(history.slice(0,100)));let b=document.createElement("button");b.textContent="Tentar novamente";b.onclick=()=>startQuiz(state.quiz);area.appendChild(b)}
function favKey(){return state.year+"|"+state.subject}
function toggleFavorite(){let fav=get("sb_favorites",[]),key=favKey();fav=fav.includes(key)?fav.filter(x=>x!==key):[...fav,key];localStorage.setItem("sb_favorites",JSON.stringify(fav));updateFav();renderFavorites()}
function updateFav(){document.getElementById("favBtn").textContent=get("sb_favorites",[]).includes(favKey())?"★ Guardado":"☆ Guardar"}
function renderFavorites(){let grid=document.getElementById("favoriteGrid");grid.innerHTML="";get("sb_favorites",[]).forEach(key=>{let [year,name]=key.split("|");let emoji=subjects.find(s=>s[0]===name)?.[1]||"📚";let b=document.createElement("button");b.className="subject";b.innerHTML=`<span>${emoji}</span><strong>${name}</strong><span>${year}.º ano</span>`;b.onclick=()=>{state.year=year;document.getElementById("year").value=year;openSubject(name)};grid.appendChild(b)});if(!grid.children.length)grid.textContent="Ainda não guardaste favoritos."}
if(localStorage.getItem("sb_dark")==="1"){document.body.classList.add("dark");document.getElementById("themeBtn").textContent="☀️ Tema"}
renderSubjects();
</script>
</body>
</html>
