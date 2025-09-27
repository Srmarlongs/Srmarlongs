<!doctype html>
<html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Marlon Gomes — Portfolio</title>
  <meta name="description" content="Portfólio de Marlon Gomes — Desenvolvimento de Sistemas, HTML/CSS/JS, Java, montagem e manutenção de computadores." />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&display=swap" rel="stylesheet">
  <style>
    /* =====================
       Paleta: Preto + Madeira + Espaço
       ===================== */
    :root{
      --bg:#070707;            /* Preto profundo */
      --panel:#0f0f0f;         /* Painel escuro */
      --wood-1:#2b1f14;        /* Madeira escura */
      --wood-2:#3a2719;        /* Madeira média */
      --accent:#9bd3ff;       /* Azul espacial suave */
      --muted:#a9a9a9;
      --glass: rgba(255,255,255,0.03);
    }

    *{box-sizing:border-box}
    html,body{height:100%;margin:0;font-family:Inter,system-ui,-apple-system,Segoe UI,Roboto,'Helvetica Neue',Arial;color:#e9eef6;background:var(--bg);}

    /* Starfield (fundo espacial) */
    .starfield{
      position:fixed;inset:0;z-index:0;pointer-events:none;overflow:hidden;
      background: radial-gradient(ellipse at bottom, rgba(9,12,26,0.55), transparent 40%), transparent;
    }
    .starfield::before, .starfield::after{
      content:"";position:absolute;inset:0;background-repeat:repeat;mix-blend-mode:screen;opacity:0.9;
      background-image: radial-gradient(2px 2px at 20% 10%, rgba(255,255,255,0.9) 50%, transparent 51%),
                        radial-gradient(1px 1px at 70% 30%, rgba(255,255,255,0.85) 50%, transparent 51%);
      transform:translateZ(0);
    }
    .starfield::after{opacity:0.5;filter:blur(1px);transform:translateY(-50px);}

    /* Container central */
    .wrap{position:relative;z-index:2;max-width:1100px;margin:40px auto;padding:28px;display:grid;grid-template-columns:360px 1fr;gap:28px}

    /* Painel lateral - madeira estilizada */
    .panel{
      background: linear-gradient(180deg,var(--wood-1),var(--wood-2));
      padding:20px;border-radius:18px;box-shadow:0 8px 30px rgba(0,0,0,0.7);border:1px solid rgba(255,255,255,0.02);
      min-height:420px;display:flex;flex-direction:column;gap:16px;position:relative;overflow:hidden
    }
    .panel::after{
      /* leve vinheta para parecer madeira polida */
      content:"";position:absolute;inset:0;border-radius:18px;pointer-events:none;background:linear-gradient(120deg,rgba(0,0,0,0.12),transparent 20%);mix-blend-mode:overlay;
    }

    .avatar{
      width:100%;height:200px;border-radius:12px;background:linear-gradient(120deg,rgba(0,0,0,0.25),rgba(255,255,255,0.02));display:flex;align-items:center;justify-content:center;font-weight:800;font-size:28px;color:var(--accent);letter-spacing:1px
    }

    .name{font-size:22px;font-weight:800;color:#fff}
    .sub{color:var(--muted);font-size:13px;margin-top:6px}

    .tags{display:flex;flex-wrap:wrap;gap:8px;margin-top:6px}
    .tag{background:var(--glass);padding:8px 10px;border-radius:10px;font-size:13px;border:1px solid rgba(255,255,255,0.03)}

    /* Card skills */
    .card{background:linear-gradient(180deg,rgba(255,255,255,0.02),transparent);padding:14px;border-radius:12px;border:1px solid rgba(255,255,255,0.03)}
    .skill{display:flex;align-items:center;justify-content:space-between;margin:8px 0}
    .skill .bar{flex:1;height:8px;background:rgba(255,255,255,0.06);border-radius:999px;margin-left:12px;overflow:hidden}
    .skill .bar > i{display:block;height:100%;background:linear-gradient(90deg,var(--accent),#6dd3ff);border-radius:999px}

    /* Principal (direita) */
    main{background:linear-gradient(180deg, rgba(255,255,255,0.01), transparent);padding:26px;border-radius:18px;min-height:420px;border:1px solid rgba(255,255,255,0.02);box-shadow:0 8px 30px rgba(0,0,0,0.6)}
    header.main-header{display:flex;align-items:center;justify-content:space-between;gap:12px}

    .headline{display:flex;flex-direction:column}
    .headline h1{color:#fff;margin:0;font-size:26px}
    .headline p{color:var(--muted);margin:6px 0 0;font-size:14px}

    .planet{width:66px;height:66px;display:inline-block}

    .projects{display:grid;grid-template-columns:repeat(auto-fill,minmax(220px,1fr));gap:14px;margin-top:18px}
    .project{padding:14px;border-radius:12px;background:linear-gradient(180deg,rgba(255,255,255,0.015),transparent);border:1px solid rgba(255,255,255,0.03);min-height:110px}
    .project h3{margin:0 0 6px;font-size:15px}
    .project p{margin:0;color:var(--muted);font-size:13px}

    footer{margin-top:20px;color:var(--muted);font-size:13px}

    /* small screens */
    @media (max-width:880px){
      .wrap{grid-template-columns:1fr;gap:18px;padding:16px}
      .panel{min-height:160px}
    }

    /* Typing effect */
    .type{color:var(--accent);font-weight:700}

    /* subtle floating animation for planet */
    @keyframes floaty{0%{transform:translateY(0)}50%{transform:translateY(-8px)}100%{transform:translateY(0)}}
    .planet svg{animation:floaty 6s ease-in-out infinite}

    /* button */
    .cta{display:inline-flex;gap:8px;align-items:center;padding:10px 14px;border-radius:12px;border:1px solid rgba(255,255,255,0.04);background:linear-gradient(90deg,rgba(255,255,255,0.02),transparent);cursor:pointer;text-decoration:none;color:#fff}

  </style>
</head>
<body>
  <div class="starfield" aria-hidden="true"></div>

  <div class="wrap">
    <aside class="panel">
      <div class="avatar">Marlon<br/><span style="font-size:12px;opacity:0.8">Desenvolvedor & Técnico em TI</span></div>

      <div>
        <div class="name">Marlon Gomes da Silva <span style="font-size:12px;color:var(--muted);font-weight:600">(18 anos)</span></div>
        <div class="sub">Curso Técnico em Desenvolvimento de Sistemas — conhecimentos práticos em hardware e software</div>
      </div>

      <div class="card">
        <strong>Skills</strong>
        <div class="tags" style="margin-top:10px">
          <div class="tag">HTML</div>
          <div class="tag">CSS</div>
          <div class="tag">JavaScript</div>
          <div class="tag">Java</div>
          <div class="tag">Montagem PC</div>
          <div class="tag">Teste / QA</div>
        </div>

        <div style="margin-top:12px">
          <div class="skill"><small>Front-end</small><div class="bar"><i style="width:85%"></i></div></div>
          <div class="skill"><small>Java / Back-end</small><div class="bar"><i style="width:70%"></i></div></div>
          <div class="skill"><small>Hardware</small><div class="bar"><i style="width:80%"></i></div></div>
        </div>
      </div>

      <div class="card">
        <strong>Contato</strong>
        <p style="margin:8px 0 0;color:var(--muted);font-size:14px">Email: <a href="mailto:marlong2008silva@gmail.com" style="color:var(--accent);text-decoration:none">marlong2008silva@gmail.com</a></p>
        <p style="margin:8px 0 0;color:var(--muted);font-size:13px">Local: Esmeraldas - MG</p>
      </div>

      <div style="margin-top:auto;display:flex;gap:8px;align-items:center">
        <a class="cta" href="#projects">Projetos</a>
        <a class="cta" href="#contact">Currículo</a>
      </div>
    </aside>

    <main>
      <header class="main-header">
        <div class="headline">
          <h1>Portfólio — Marlon Gomes</h1>
          <p>Desenvolvedor web, entusiasta de hardware e aprendiz contínuo. <span class="type" id="typed">HTML • CSS • JS • Java</span></p>
        </div>

        <div class="planet" title="Espaço — visual">
          <!-- pequeno planeta SVG estilizado -->
          <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
            <defs>
              <radialGradient id="g" cx="30%" cy="30%">
                <stop offset="0%" stop-color="#a7e0ff" stop-opacity="0.9"/>
                <stop offset="100%" stop-color="#0b3b54" stop-opacity="1"/>
              </radialGradient>
            </defs>
            <circle cx="50" cy="50" r="28" fill="url(#g)" />
            <g opacity="0.12" fill="#000"><ellipse cx="58" cy="64" rx="20" ry="6" transform="rotate(-15 58 64)"/></g>
            <path d="M12 78 C30 60, 70 60, 88 78" stroke="#ffffff22" stroke-width="1.2" fill="none" />
          </svg>
        </div>
      </header>

      <section id="projects">
        <h2 style="margin:14px 0 8px;color:#fff;font-size:18px">Projetos recentes</h2>
        <div class="projects">
          <article class="project">
            <h3>Site Interativo — Cardápio</h3>
            <p>HTML/CSS/JS — cardápio interativo com categorias, filtros e animações. Ideal para restaurantes e pizzarias.</p>
          </article>

          <article class="project">
            <h3>Sistema Java + MySQL</h3>
            <p>Sistema de gestão com JavaFX e JDBC para controle de colaboradores, folha e treinamentos (nexus_db).</p>
          </article>

          <article class="project">
            <h3>Montagem e Testes de PCs</h3>
            <p>Montagem, diagnóstico e otimização de hardware — experiência prática em manutenção e testes.</p>
          </article>

          <article class="project">
            <h3>Bot de Chat / Automatização</h3>
            <p>Scripts e automatizações para rotinas simples e integrações web (ex.: formulários automatizados).</p>
          </article>
        </div>
      </section>

      <section style="margin-top:18px" id="about">
        <h2 style="color:#fff;font-size:18px;margin-bottom:10px">Sobre mim</h2>
        <p style="color:var(--muted);margin:0 0 8px">Tenho 18 anos, concluí o Curso Técnico em Desenvolvimento de Sistemas e já trabalhei em vários projetos práticos envolvendo front-end, back-end com Java, e montagem/testes de computadores. Procuro oportunidades como desenvolvedor júnior, assistente de TI ou estágios em tech.</p>

        <div style="display:flex;gap:12px;margin-top:12px;flex-wrap:wrap">
          <a class="cta" href="https://github.com/Srmarlongs" target="_blank" rel="noopener noreferrer">GitHub</a>
          <a class="cta" href="#contact">Baixar CV</a>
        </div>
      </section>

      <footer id="contact">
        <strong>Quer o código completo dos projetos?</strong>
        <p style="color:var(--muted);margin:8px 0 0">Posso organizar os repositórios com README detalhado, scripts de deploy e exemplos prontos. Se quiser, copie esse arquivo e publique como <code>index.html</code> em um repositório para usar com GitHub Pages.</p>
      </footer>
    </main>
  </div>

  <script>
    // texto com efeito simples (sem dependências)
    (function(){
      const el = document.getElementById('typed');
      const words = ['HTML • CSS • JS • Java','Montagem de PCs','Testes e QA','Sempre aprendendo'];
      let i=0,j=0,dir=1,display='';
      function tick(){
        const w = words[i];
        if(dir==1){ display = w.slice(0, j+1); j++; if(j===w.length) dir=-1; }
        else{ display = w.slice(0, j-1); j--; if(j===0){ dir=1; i=(i+1)%words.length; }}
        el.textContent = display;
        setTimeout(tick, dir==1?80:40);
      }
      tick();
    })();
  </script>
</body>
</html>
