<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Atividade Avaliativa - Química Aplicada</title>
    <style>
        /* [Seu CSS permanece inalterado] */
        /* ... */
    </style>
</head>
<body>

    <div class="form-container">
        <!-- Cabeçalho da Escola -->
        <div class="header">
            <h1>E.E. MARIA LEONI</h1>
        </div>

        <!-- Conteúdo do Formulário -->
        <div class="form-content">
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

            <h2 style="text-align: center;">ATIVIDADE DE QUÍMICA APLICADA</h2>
            <p style="text-align: center;">TEMA: QUÍMICA ALIMENTAR</p>

            <div id="questoes-container"></div>

            <button onclick="enviarRespostas()">Enviar Respostas</button>
        </div>

    </div>

    <script>
        const questoes = [
            /* [Suas questões permanecem inalteradas] */
            /* ... */
        ];

        const cronometros = {}; // Objeto para armazenar os cronômetros de cada questão

        function iniciarCronometro(questaoId) {
            if (!cronometros[questaoId]) {
                let segundos = 0;
                const cronometro = document.getElementById(`cronometro-${questaoId}`);
                
                cronometros[questaoId] = setInterval(() => {
                    segundos++;
                    const minutos = Math.floor(segundos / 60);
                    const restoSegundos = segundos % 60;
                    cronometro.textContent = `${minutos.toString().padStart(2, '0')}:${restoSegundos.toString().padStart(2, '0')}`;
                }, 1000);
            }
        }

        function pararCronometro(questaoId) {
            if (cronometros[questaoId]) {
                clearInterval(cronometros[questaoId]);
                cronometros[questaoId] = null;
            }
        }

        function gerarQuestoes() {
            const container = document.getElementById('questoes-container');
            questoes.forEach((questao, index) => {
                const questaoId = index + 1;

                const questaoDiv = document.createElement('div');
                questaoDiv.classList.add('questao');

                // Cronômetro
                const cronometroDiv = document.createElement('div');
                cronometroDiv.classList.add('relogio');
                cronometroDiv.id = `cronometro-${questaoId}`;
                cronometroDiv.textContent = "00:00";
                questaoDiv.appendChild(cronometroDiv);

                // Pergunta com Numeração
                const pergunta = document.createElement('p');

                // Criar elemento para número da questão
                const numeroSpan = document.createElement('span');
                numeroSpan.classList.add('numero-questao');
                numeroSpan.textContent = `${questaoId}. `;

                // Adicionar número e texto da questão
                pergunta.appendChild(numeroSpan);
                pergunta.appendChild(document.createTextNode(questao.texto));
                questaoDiv.appendChild(pergunta);

                // Resposta
                if (questao.tipo === 'aberta') {
                    const resposta = document.createElement('textarea');
                    resposta.id = `resposta-${questaoId}`;
                    resposta.name = `resposta-${questaoId}`;
                    resposta.placeholder = "Digite sua resposta aqui...";
                    resposta.classList.add('resposta');
                    resposta.addEventListener('focus', () => iniciarCronometro(questaoId));
                    resposta.addEventListener('blur', () => pararCronometro(questaoId));
                    questaoDiv.appendChild(resposta);
                } else if (questao.tipo === 'multipla-escolha') {
                    const opcoesDiv = document.createElement('div');
                    opcoesDiv.classList.add('opcoes');

                    questao.opcoes.forEach(opcao => {
                        const label = document.createElement('label');
                        const input = document.createElement('input');
                        input.type = 'radio';
                        input.name = `resposta-${questaoId}`;
                        input.value = opcao.letra;
                        input.required = true;

                        // Criar um span para o texto da opção
                        const span = document.createElement('span');
                        span.textContent = ` ${opcao.letra}) ${opcao.texto}`;

                        label.appendChild(input);
                        label.appendChild(span);
                        opcoesDiv.appendChild(label);
                    });

                    // Adicionar evento para iniciar/parar cronômetro quando uma opção é selecionada/desselecionada
                    opcoesDiv.querySelectorAll('input[type="radio"]').forEach(radio => {
                        radio.addEventListener('change', () => {
                            if (radio.checked) {
                                iniciarCronometro(questaoId);
                            }
                        });
                        radio.addEventListener('blur', () => {
                            pararCronometro(questaoId);
                        });
                    });

                    questaoDiv.appendChild(opcoesDiv);
                }

                // Adicionar linha separadora entre questões, exceto após a última
                if (questaoId < questoes.length) {
                    const linha = document.createElement('hr');
                    linha.classList.add('linha-questao');
                    questaoDiv.appendChild(linha);
                }

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

            const totalQuestoes = questoes.length; // Número total de questões
            for (let i = 1; i <= totalQuestoes; i++) {
                if (questoes[i - 1].tipo === 'aberta') {
                    const resposta = document.getElementById(`resposta-${i}`).value;
                    respostas[`resposta-${i}`] = resposta;
                } else if (questoes[i - 1].tipo === 'multipla-escolha') {
                    const respostaSelecionada = document.querySelector(`input[name="resposta-${i}"]:checked`);
                    respostas[`resposta-${i}`] = respostaSelecionada ? respostaSelecionada.value : '';
                }
            }

            // Parar todos os cronômetros antes de enviar
            for (let i = 1; i <= totalQuestoes; i++) {
                pararCronometro(i);
            }

            try {
                const response = await fetch('https://script.google.com/macros/s/AKfycbzdbF1mTfBTWg-JN_86NLpjVEgFWbZHVOc6odHMu2Q8rnFpiVskUBmUxS0G3WfEzJ14/exec', { // Substitua por seu URL do Web App
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/x-www-form-urlencoded',
                    },
                    body: new URLSearchParams(respostas)
                });

                // Verificar se a resposta é válida
                const result = await response.json();

                if (result.result === 'success') {
                    // Limpar o formulário
                    document.getElementById('nome').value = "";
                    document.getElementById('serie').value = "";
                    document.getElementById('data').value = "";
                    for (let i = 1; i <= totalQuestoes; i++) {
                        if (questoes[i - 1].tipo === 'aberta') {
                            document.getElementById(`resposta-${i}`).value = "";
                        } else if (questoes[i - 1].tipo === 'multipla-escolha') {
                            const radios = document.getElementsByName(`resposta-${i}`);
                            radios.forEach(radio => radio.checked = false);
                        }
                        document.getElementById(`cronometro-${i}`).textContent = "00:00";
                    }

                    // Exibir pontuação e status de plágio
                    const pontuacao = result.row[result.row.length - 1];
                    const plagiado = result.row[result.row.length - 2];
                    alert(`Respostas enviadas com sucesso!\nPontuação Total: ${pontuacao}\nStatus de Plágio: ${plagiado}`);
                } else {
                    alert("Ocorreu um erro ao enviar as respostas: " + result.error);
                }
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
