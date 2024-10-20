<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Atividade Avaliativa - Química Aplicada</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f0f0f0;
            color: white;
        }
        h1, h2 {
            text-align: center;
            font-weight: bold;
            margin-top: 20px;
        }
        .form-container {
            background-color: rgba(0, 0, 0, 0.85);
            margin: 20px auto;
            padding: 20px;
            border-radius: 10px;
            width: 80%;
            max-width: 800px;
        }
        .cabecalho {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            margin-bottom: 20px;
        }
        .cabecalho div {
            width: 30%;
            min-width: 200px;
            margin-bottom: 10px;
        }
        .serie-dropdown {
            width: 25%;
            min-width: 150px;
            margin-bottom: 10px;
        }
        .relogio {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            font-size: 14px;
            display: flex;
            align-items: center;
            justify-content: center;
            background-color: white;
            color: black;
            font-weight: bold;
            border: 4px solid;
            border-image: linear-gradient(to bottom, blue, lime) 1;
            margin-right: 20px;
            margin-top: 10px;
        }
        input[type="date"], select {
            width: 100%;
            padding: 10px;
            margin-top: 5px;
            border-radius: 5px;
            border: none;
        }
        textarea {
            width: 100%;
            height: 100px;
            padding: 10px;
            margin-top: 5px;
            border-radius: 5px;
            border: none;
            resize: vertical;
            line-height: 1.5;
            background-image: repeating-linear-gradient(
                to bottom,
                #ccc 0px,
                #ccc 1px,
                transparent 1px,
                transparent 30px
            );
        }
        button {
            display: inline-block;
            margin: 10px 5px 30px auto;
            padding: 10px 20px;
            font-size: 14px;
            border: none;
            border-radius: 5px;
            background-color: #28a745;
            color: white;
            cursor: pointer;
        }
        button:hover {
            background-color: #218838;
        }
        /* Estilos para as questões e respostas */
        .questao {
            margin-bottom: 20px;
            background-color: rgba(255, 255, 255, 0.1);
            padding: 15px;
            border-radius: 8px;
        }
        .questao p {
            margin-bottom: 10px;
        }
        .resposta {
            width: 100%;
            padding: 10px;
            border-radius: 5px;
            border: none;
            resize: vertical;
            line-height: 1.5;
        }
    </style>
</head>
<body>

    <div class="form-container">
        <h1>E.E. MARIA LEONI</h1>
        <div class="cabecalho">
            <div>
                <p>NOME: 
                    <select id="nome" name="nome" required>
                        <option value="" disabled selected>Selecione seu nome</option>
                        <option>ANA CLARA PETRONI DE SOUZA</option>
                        <option>ANTHONY LEONARDI DOS SANTOS</option>
                        <option>BEATRIZ BORTOLO CANDIDO</option>
                        <option>BEATRIZ CAMARGO</option>
                        <option>BEATRIZ DA SILVA VELOSO</option>
                        <option>DAVI CRUZ SIBINELLI</option>
                        <option>ERICK SALVADOR</option>
                        <option>FELIPE PEREIRA DA SILVA</option>
                        <option>GABRIEL ALVES DOS SANTOS SILVA</option>
                        <option>GABRIELA DOS ANJOS ALVES</option>
                        <option>GIOVANA CRISTINA ALVES DOMINGUES</option>
                        <option>GRAZIELLA DOS ANJOS MELO</option>
                        <option>GUSTAVO ALMEIDA DA SILVA</option>
                        <option>GUSTAVO RONDON</option>
                        <option>JESSYCA VITORIA COSTA VASCONCELOS</option>
                        <option>HELOISA ALVES DA SILVA</option>
                        <option>ISABELA FERREIRA CLEMENTE</option>
                        <option>ISABELLY MARTINS DE SIQUEIRA CORTEZ</option>
                        <option>JOAO VICTOR MONTEIRO DA SILVA</option>
                        <option>KAUA DE DEUS MESQUITA LEONARDO</option>
                        <option>KLEBER GABRIEL SAMPAIO VARELLA</option>
                        <option>MANUELLA QUEIROZ DOS SANTOS</option>
                        <option>MARIA CLARA DA SILVA BARBOSA SAMPAIO</option>
                        <option>MARIA EDUARDA LOPES DE OLIVEIRA</option>
                        <option>MATEUS VITOR PINHEIRO GONCALES</option>
                        <option>MATHEUS DOS SANTOS SOUSA</option>
                        <option>MATHEUS FERREIRA DE OLIVEIRA</option>
                        <option>NICOLAS FERNANDO SANTANA VIEIRA</option>
                        <option>SOPHIA ALVIN SILVA</option>
                        <option>THAISSA RAMOS DA SILVA</option>
                        <option>THAYNÁ VIEIRA SANTOS</option>
                    </select>
                </p>
            </div>
            <div class="serie-dropdown">
                <p>SÉRIE: 
                    <select id="serie" name="serie" required>
                        <option value="" disabled selected>Selecione a série</option>
                        <option value="3ª SÉRIE A">3ª SÉRIE A</option>
                        <option value="3ª SÉRIE B">3ª SÉRIE B</option>
                    </select>
                </p>
            </div>
            <div class="serie-dropdown">
                <p>DATA: <input type="date" id="data" name="data" required></p>
            </div>
        </div>

        <h2>ATIVIDADE DE QUÍMICA APLICADA</h2>
        <p style="text-align: center;">TEMA: QUÍMICA ALIMENTAR</p>

        <div id="questoes-container"></div>

        <button onclick="enviarRespostas()">Enviar Respostas</button>
    </div>

    <script>
        const questoes = [
            "A importância da conservação sustentável de alimentos em 2024: Como novas tecnologias, como embalagens biodegradáveis e sistemas modulares sem energia elétrica, podem minimizar os impactos ambientais da conservação de alimentos?",
            "Internet das Coisas (IoT) na conservação e segurança alimentar: Explique como o uso da IoT pode garantir a qualidade dos alimentos e evitar desperdícios, considerando tanto a indústria alimentícia quanto o consumo doméstico.",
            "Aditivos alimentares e saúde pública: Como os avanços na química dos alimentos estão possibilitando a substituição de aditivos sintéticos por conservantes naturais? Discuta vantagens e desafios dessa transição.",
            "Alimentos ultraprocessados e saúde pública em 2024: Como as inovações na formulação de alimentos ultraprocessados podem mitigar seus efeitos negativos e promover um consumo mais saudável?",
            "Legislação e segurança alimentar: Avalie como as normas estabelecidas por órgãos como a ANVISA e o Codex Alimentarius ajudam a garantir a segurança dos alimentos em 2024. Quais desafios permanecem?",
            "Mudanças climáticas e conservação de alimentos: Como tecnologias de conservação, como a liofilização e embalagens inteligentes, podem ajudar a mitigar os impactos das mudanças climáticas na segurança alimentar?",
            "Composição nutricional e alimentação personalizada: Como o conhecimento sobre a composição química dos alimentos e avanços em nutrição personalizada podem melhorar a saúde e o bem-estar da população?",
            "Sustentabilidade e redução do desperdício de alimentos: Quais métodos inovadores de conservação podem contribuir para a redução do desperdício de alimentos, tanto em ambientes urbanos quanto rurais?",
            "Embalagens inteligentes como solução para conservação eficiente: Quais benefícios essas embalagens proporcionam à indústria e aos consumidores?",
            "Química dos alimentos e alimentos fortificados: Qual é um exemplo prático de alimentos fortificados disponíveis em 2024?"
        ];

        const cronometrosAtivos = {};

        function iniciarCronometro(questaoId) {
            const cronometro = document.getElementById(`cronometro-${questaoId}`);
            let segundos = 0;

            const interval = setInterval(() => {
                segundos++;
                const minutos = Math.floor(segundos / 60);
                const restoSegundos = segundos % 60;
                cronometro.textContent = `${minutos.toString().padStart(2, '0')}:${restoSegundos.toString().padStart(2, '0')}`;
            }, 1000);

            cronometrosAtivos[questaoId] = interval;
        }

        function pararCronometro(questaoId) {
            clearInterval(cronometrosAtivos[questaoId]);
        }

        function gerarQuestoes() {
            const container = document.getElementById('questoes-container');
            questoes.forEach((texto, index) => {
                const questaoDiv = document.createElement('div');
                questaoDiv.classList.add('questao');

                const pergunta = document.createElement('p');
                pergunta.textContent = `Questão ${index + 1}: ${texto}`;
                questaoDiv.appendChild(pergunta);

                const resposta = document.createElement('textarea');
                resposta.id = `resposta-${index + 1}`;
                resposta.name = `resposta-${index + 1}`;
                resposta.placeholder = "Digite sua resposta aqui...";
                questaoDiv.appendChild(resposta);

                const cronometroDiv = document.createElement('div');
                cronometroDiv.classList.add('relogio');
                cronometroDiv.id = `cronometro-${index + 1}`;
                cronometroDiv.textContent = "00:00";
                questaoDiv.appendChild(cronometroDiv);

                const iniciarBtn = document.createElement('button');
                iniciarBtn.textContent = "Iniciar";
                iniciarBtn.style.marginRight = "10px";
                iniciarBtn.type = "button"; // Evita que o botão submeta o formulário
                iniciarBtn.onclick = () => iniciarCronometro(index + 1);
                questaoDiv.appendChild(iniciarBtn);

                const pararBtn = document.createElement('button');
                pararBtn.textContent = "Parar";
                pararBtn.type = "button";
                pararBtn.onclick = () => pararCronometro(index + 1);
                questaoDiv.appendChild(pararBtn);

                container.appendChild(questaoDiv);
            });
        }

        async function enviarRespostas() {
            const nome = document.getElementById('nome').value;
            const serie = document.getElementById('serie').value;
            const data = document.getElementById('data').value;

            if (!nome || !serie || !data) {
                alert("Por favor, preencha todos os campos antes de enviar.");
                return;
            }

            let respostas = {};
            respostas['nome'] = nome;
            respostas['serie'] = serie;
            respostas['data'] = data;

            const totalQuestoes = 10; // Número total de questões
            for (let i = 1; i <= totalQuestoes; i++) {
                const resposta = document.getElementById(`resposta-${i}`).value;
                respostas[`resposta-${i}`] = resposta;
            }

            try {
                const response = await fetch('https://script.google.com/macros/s/SEU_SCRIPT_ID/exec', { // Substitua por seu URL do Web App
                    method: 'POST',
                    mode: 'no-cors', // Necessrio para evitar problemas de CORS
                    headers: {
                        'Content-Type': 'application/x-www-form-urlencoded',
                    },
                    body: new URLSearchParams(respostas)
                });

                // Limpar o formulário após o envio
                document.getElementById('nome').value = "";
                document.getElementById('serie').value = "";
                document.getElementById('data').value = "";
                for (let i = 1; i <= totalQuestoes; i++) {
                    document.getElementById(`resposta-${i}`).value = "";
                    document.getElementById(`cronometro-${i}`).textContent = "00:00";
                }

                alert("Respostas enviadas com sucesso!");
            } catch (error) {
                console.error('Erro ao enviar respostas:', error);
                alert("Ocorreu um erro ao enviar as respostas. Por favor, tente novamente.");
            }
        }

        // Inicializa as questões ao carregar a página
        window.onload = gerarQuestoes;
    </script>

</body>
</html>
