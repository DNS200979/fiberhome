<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Resumo Estratégico - Fiberhome</title>
    <style>
        /* Paleta de Cores Fiberhome */
        :root {
            --fiber-blue: #004B87;
            --fiber-orange: #FF6A13;
            --bg-dark: #002D52;
            --text-dark: #333;
            --text-light: #fff;
        }

        body {
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background: linear-gradient(135deg, var(--fiber-blue) 0%, var(--bg-dark) 100%);
            color: var(--text-dark);
            line-height: 1.6;
            margin: 0;
            padding: 40px 20px;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            background-color: #ffffff;
            border-radius: 10px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            overflow: hidden;
            padding: 40px;
            border-top: 8px solid var(--fiber-orange);
        }

        h1 {
            color: var(--fiber-blue);
            font-size: 2.2em;
            margin-top: 0;
            border-bottom: 2px solid #eee;
            padding-bottom: 15px;
        }

        h2 {
            color: var(--fiber-orange);
            font-size: 1.5em;
            margin-top: 30px;
            margin-bottom: 15px;
        }

        p {
            font-size: 1.1em;
        }

        ul {
            list-style-type: none;
            padding: 0;
        }

        ul li {
            background-color: #f8f9fa;
            margin-bottom: 15px;
            padding: 20px;
            border-radius: 8px;
            border-left: 4px solid var(--fiber-blue);
        }

        /* Destaque para os links do Edital */
        .edital-link {
            display: inline-block;
            color: var(--fiber-blue);
            font-weight: bold;
            text-decoration: none;
            background-color: #e6f0fa;
            padding: 4px 8px;
            border-radius: 4px;
            border-bottom: 2px solid var(--fiber-blue);
            transition: all 0.3s ease;
            margin: 5px 0;
        }

        .edital-link:hover {
            background-color: var(--fiber-blue);
            color: var(--text-light);
        }

        .edital-link::before {
            content: '📄 ';
        }

        /* Destaque para Perguntas Estratégicas */
        .question-highlight {
            background-color: var(--fiber-orange);
            color: var(--text-light);
            padding: 15px 20px;
            border-radius: 6px;
            font-weight: bold;
            font-size: 1.1em;
            margin-top: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
            box-shadow: 0 4px 10px rgba(255, 106, 19, 0.3);
        }

        .question-highlight::before {
            content: '❓';
            font-size: 1.5em;
        }

        .solution {
            color: #27ae60;
            font-weight: 600;
        }

        .combo-box {
            background-color: #e6f0fa;
            padding: 20px;
            border-radius: 8px;
            border: 2px dashed var(--fiber-blue);
            margin-top: 20px;
        }

        .combo-box ul li {
            background-color: transparent;
            border: none;
            padding: 5px 0;
            margin: 0;
            font-size: 1.1em;
            font-weight: bold;
            color: var(--fiber-blue);
        }
        
        .combo-box ul li::before {
            content: '✓ ';
            color: var(--fiber-orange);
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Resumo Estratégico - Adesão ao Edital 021/2025</h1>
        <p>Baseado na análise do Edital de Concorrência Pública nº 021/2025 da Prefeitura de Pindamonhangaba (Smart City as a Service - SCaaS) e no portfólio de produtos Fiberhome.</p>

        <h2>1. O que a Fiberhome atende perfeitamente</h2>
        <ul>
            <li>
                <strong>Rede Metro Ethernet e Concentradores (Core/Edge):</strong><br>
                <a href="#link-edital-olt" class="edital-link" title="Clique para ver o item no edital">Requisito do Edital: O projeto exige pontos de concentração com "Hybrid XGS-PON/GPON OLT"</a><br>
                <span class="solution">Solução Fiberhome:</span> Série AN6000 (AN6000-15 e AN6000-17), plataformas híbridas GPON/XGS-PON (e até 50G PON).
            </li>
            <li>
                <strong>Equipamentos de Borda e Wi-Fi 6 (CPEs):</strong><br>
                <a href="#link-edital-wifi" class="edital-link" title="Clique para ver o item no edital">Requisito do Edital: Conectividade Wi-Fi 6 em prédios públicos e ruas</a><br>
                <span class="solution">Solução Fiberhome:</span> SR1041Y (Wi-Fi 6), com suporte a TR-369 para telemetria avançada.
            </li>
            <li>
                <strong>ONTs Ópticas Padrão:</strong><br>
                <a href="#link-edital-pontos" class="edital-link" title="Clique para ver o item no edital">Requisito do Edital: Pontos de monitoramento e prédios com necessidade apenas de link óptico</a><br>
                <span class="solution">Solução Fiberhome:</span> Modelos HG6154F3, HG6145F e HG6245D.
            </li>
        </ul>

        <h2>2. Onde será necessário compor com parceiros ou validar roadmap</h2>
        <ul>
            <li>
                <strong>Wi-Fi 7 Indoor/Outdoor:</strong> 
                Necessário validar disponibilidade e prazos de equipamentos certificados no Brasil.
            </li>
            <li>
                <strong>Next Generation Firewall (NGFW) e SD-WAN:</strong> 
                Requisito atendido por marcas especializadas (Fortinet, Palo Alto, Cisco).
                <div class="question-highlight">
                    Pergunta Estratégica: A Fiberhome deve focar estritamente em transporte e acesso ou buscar parcerias oficiais para compor a camada de segurança NGFW?
                </div>
            </li>
            <li>
                <strong>Conectividade 5G/LTE e Satélite:</strong> 
                Prexx pode validar a disponibilidade para compor o projeto com modems/SIM cards de operadoras móveis.
            </li>
        </ul>

        <h2>Resumo da Estratégia Comercial Sugerida</h2>
        <p>
            A Fiberhome fornece o "coração" da rede óptica exigida pelo município. A abordagem junto aos ISPs e integradores deve destacar o combo:
        </p>
        
        <div class="combo-box">
            <ul>
                <li>Hybrid OLTs (AN6000)</li>
                <li>Wi-Fi 6 ONTs (HG6145F1 e HG6145F3)</li>
            </ul>
        </div>

        <p style="margin-top: 20px;">
            O argumento principal de venda é a robustez dos OLTs para suportar tráfego intenso de câmeras e sensores, aliado às capacidades de gestão avançada (TR-369) dos roteadores Wi-Fi 6, reduzindo drasticamente o OPEX para o provedor vencedor através do monitoramento remoto.
        </p>
    </div>
</body>
</html>
