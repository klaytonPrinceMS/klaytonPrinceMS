<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Python | Segurança da Informação</title>
    <style>
        :root {
            --bg-primary: #0a0a0f;
            --bg-secondary: #1a1a2e;
            --neon-cyan: #00f0ff;
            --neon-magenta: #ff2a6d;
            --neon-green: #05ffa1;
            --neon-yellow: #fcee0a;
            --text-main: #ffffff;
            --text-secondary: #a0a0a0;
            --glitch-offset: 2px;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Courier New', monospace;
            background: var(--bg-primary);
            color: var(--text-main);
            overflow-x: hidden;
            line-height: 1.6;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Neon Glow */
        .neon-cyan {
            color: var(--neon-cyan);
            text-shadow:
                0 0 5px var(--neon-cyan),
                0 0 10px var(--neon-cyan),
                0 0 20px var(--neon-cyan),
                0 0 40px var(--neon-cyan);
        }

        .neon-magenta {
            color: var(--neon-magenta);
            text-shadow:
                0 0 5px var(--neon-magenta),
                0 0 10px var(--neon-magenta),
                0 0 20px var(--neon-magenta),
                0 0 40px var(--neon-magenta);
        }

        .neon-green {
            color: var(--neon-green);
            text-shadow:
                0 0 5px var(--neon-green),
                0 0 10px var(--neon-green),
                0 0 20px var(--neon-green),
                0 0 40px var(--neon-green);
        }

        /* Glitch Effect */
        .glitch {
            position: relative;
            animation: glitch 2s infinite;
        }

        @keyframes glitch {
            0% { transform: translate(0); }
            20% { transform: translate(-1px, 1px); }
            40% { transform: translate(-1px, -1px); }
            60% { transform: translate(1px, 1px); }
            80% { transform: translate(1px, -1px); }
            100% { transform: translate(0); }
        }

        .glitch::before,
        .glitch::after {
            content: attr(data-text);
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            opacity: 0.8;
        }

        .glitch::before {
            animation: glitch-top 1s infinite;
            clip-path: polygon(0 0, 100% 0, 100% 33%, 0 33%);
            background: var(--neon-cyan);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .glitch::after {
            animation: glitch-bottom 1.5s infinite;
            clip-path: polygon(0 67%, 100% 67%, 100% 100%, 0 100%);
            background: var(--neon-magenta);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        @keyframes glitch-top {
            0%, 95% { transform: translate(0); }
            97% { transform: translate(-2px, -2px); }
            99% { transform: translate(2px, 2px); }
            100% { transform: translate(0); }
        }

        @keyframes glitch-bottom {
            0%, 90% { transform: translate(0); }
            93% { transform: translate(2px, 2px); }
            95% { transform: translate(-2px, -2px); }
            97% { transform: translate(2px, 2px); }
            100% { transform: translate(0); }
        }

        /* Header */
        .header {
            text-align: center;
            padding: 40px 0;
            border: 2px solid var(--neon-cyan);
            box-shadow:
                0 0 20px var(--neon-cyan),
                inset 0 0 20px rgba(0, 240, 255, 0.1);
            margin-bottom: 40px;
            position: relative;
        }

        @keyframes borderRotate {
            100% { transform: rotate(360deg); }
        }

        h1 {
            font-size: 3.5em;
            margin-bottom: 10px;
            font-weight: bold;
        }

        .subtitle {
            font-size: 1.5em;
            color: var(--text-secondary);
            margin-bottom: 20px;
        }

        /* ASCII Art */
        .ascii-art {
            font-size: 12px;
            line-height: 1.2;
            color: var(--neon-green);
            text-align: center;
            margin: 20px 0;
            animation: flicker 1.5s infinite alternate;
        }

        @keyframes flicker {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.8; }
        }

        /* Stats */
        .stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 40px 0;
        }

        .stat-card {
            background: var(--bg-secondary);
            padding: 20px;
            border-radius: 10px;
            border: 1px solid var(--neon-cyan);
            box-shadow: 0 0 15px rgba(0, 240, 255, 0.3);
            text-align: center;
            transition: transform 0.3s;
        }

        .stat-card:hover {
            transform: scale(1.05);
            box-shadow: 0 0 25px var(--neon-cyan);
        }

        .stat-number {
            font-size: 2em;
            color: var(--neon-magenta);
        }

        /* Skills */
        .skills {
            margin: 40px 0;
        }

        .skill-item {
            display: flex;
            align-items: center;
            margin: 15px 0;
            padding: 15px;
            background: var(--bg-secondary);
            border-left: 4px solid var(--neon-green);
        }

        .skill-icon {
            font-size: 2em;
            margin-right: 15px;
        }

        /* Responsive */
        @media (max-width: 768px) {
            h1 { font-size: 2.5em; }
            .subtitle { font-size: 1.2em; }
            .ascii-art { font-size: 10px; }
        }

        /* Scanlines */
        body::after {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image:
                linear-gradient(rgba(0,0,0,0.1) 1px, transparent 1px),
                linear-gradient(90deg, rgba(255,0,0,0.03) 1px, transparent 1px);
            background-size: 100% 2px, 3px 100%;
            pointer-events: none;
            z-index: 1000;
            opacity: 0.5;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1 class="glitch neon-cyan" data-text="CYBERHACKER">Analista de Sistemas</h1>
            <p class="subtitle neon-magenta">PRINCE, K.B</p>
            <div class="ascii-art">





            </div>
        </div>

        <section class="stats">

            <div class="stat-card">
                <div class="stat-number neon-yellow">Analista de Sistemas</div>
                <div>Prefeitura de Monte Santo de Minas</div>
            </div>
            <div class="stat-card">
                <div class="stat-number neon-magenta">Sócio fundador</div>
                <div>T! SOS Sistemas</div>
            </div>
        </section>





        <section class="skills">
            <h2 class="neon-cyan glitch" data-text="Habilidades" style="text-align: center; margin-bottom: 30px; font-size: 2em;">Habilidades</h2>
            <div class="skill-item">
                <span class="skill-icon">🐍</span>
                <div>
                    <h3 class="neon-green">Python</h3>
                    <p>Scripting, Automação, Ferramentas de Pentest</p>
                </div>
            </div>
            <div class="skill-item">
                <span class="skill-icon">🔒</span>
                <div>
                    <h3 class="neon-magenta">Cibersegurança</h3>
                    <p>Ethical Hacking, Pentesting, Análise de Vulnerabilidades</p>
                </div>
            </div>
            <div class="skill-item">
                <span class="skill-icon">🛡️</span>
                <div>
                    <h3 class="neon-yellow">Segurança da Informação</h3>
                    <p>Criptografia, Compliance, Gestão de Riscos</p>
                </div>
            </div>
        </section>

        <section style="text-align: center; margin: 40px 0;">
            <p class="neon-cyan" style="font-size: 1.2em;">
                Entrando na Matrix... <span style="animation: blink 1s infinite;">█</span>
            </p>
        </section>
    </div>

    <script>
        // Adiciona efeito de digitação no título
        const title = document.querySelector('h1');
        const originalText = title.textContent;
        title.textContent = '';
        let i = 0;
        function typeWriter() {
            if (i < originalText.length) {
                title.textContent += originalText.charAt(i);
                i++;
                setTimeout(typeWriter, 100);
            }
        }
        setTimeout(typeWriter, 500);

        // Efeito de blink
        const style = document.createElement('style');
        style.textContent = `
            @keyframes blink {
                0%, 50% { opacity: 1; }
                51%, 100% { opacity: 0; }
            }
        `;
        document.head.appendChild(style);
    </script>
</body>
</html>
