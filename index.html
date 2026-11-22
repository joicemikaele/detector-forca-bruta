<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Detector de Força Bruta</title>
<style>
  :root { --fundo:#0f172a; --cartao:#1e293b; --texto:#e2e8f0; --destaque:#38bdf8; --alerta:#ef4444; --ok:#22c55e; }
  * { box-sizing: border-box; }
  body { margin:0; padding:32px 16px; background:var(--fundo); color:var(--texto); font-family:"Segoe UI",Arial,sans-serif; }
  main { max-width:800px; margin:0 auto; }
  h1 { color:var(--destaque); margin-bottom:4px; }
  .sub { color:#94a3b8; margin-top:0; }
  textarea { width:100%; height:180px; background:var(--cartao); color:var(--texto); border:1px solid #334155; border-radius:12px; padding:12px; font-family:Consolas,monospace; font-size:0.85rem; }
  .controles { display:flex; gap:12px; flex-wrap:wrap; align-items:center; margin:16px 0; }
  input[type=number] { width:70px; padding:6px; border-radius:8px; border:1px solid #334155; background:var(--cartao); color:var(--texto); }
  button { padding:10px 18px; border:0; border-radius:8px; background:var(--destaque); color:#0f172a; font-weight:bold; cursor:pointer; }
  button.sec { background:#334155; color:var(--texto); }
  .resumo { display:flex; gap:16px; margin:24px 0; flex-wrap:wrap; }
  .caixa { flex:1; min-width:180px; background:var(--cartao); padding:20px; border-radius:12px; }
  .numero { font-size:2.4rem; font-weight:bold; }
  .suspeitos .numero { color:var(--alerta); }
  table { width:100%; border-collapse:collapse; background:var(--cartao); border-radius:12px; overflow:hidden; }
  th, td { padding:14px 16px; text-align:left; }
  th { background:#334155; }
  tr.alerta td:first-child { border-left:4px solid var(--alerta); }
  tr.ok td:first-child { border-left:4px solid var(--ok); }
  tr.alerta .selo { color:var(--alerta); font-weight:bold; }
  tr.ok .selo { color:var(--ok); font-weight:bold; }
</style>
</head>
<body>
<main>
  <h1>🛡️ Detector de Força Bruta</h1>
  <p class="sub">Cole um log de login ou escolha um arquivo. A análise acontece no seu navegador; nada é enviado para a internet.</p>

  <textarea id="log" placeholder="2026-11-19 10:01:12 FAILED user=admin ip=192.168.1.50"></textarea>

  <div class="controles">
    <input type="file" id="arquivo" accept=".log,.txt">
    <label>Limite de falhas: <input type="number" id="limite" value="5" min="1"></label>
    <button id="analisar">Analisar</button>
    <button id="exemplo" class="sec">Carregar exemplo</button>
  </div>

  <section id="resultado" hidden>
    <div class="resumo">
      <div class="caixa"><div>IPs analisados</div><div class="numero" id="totalIps">0</div></div>
      <div class="caixa suspeitos"><div>IPs suspeitos</div><div class="numero" id="totalSuspeitos">0</div></div>
    </div>
    <table>
      <thead><tr><th>IP</th><th>Falhas</th><th>Usuários testados</th><th>Status</th></tr></thead>
      <tbody id="linhas"></tbody>
    </table>
    <p id="vazio" hidden>Nenhuma tentativa falha encontrada. Confira o formato do log.</p>
  </section>
</main>

<script>
  const padrao = /^(\S+ \S+) (FAILED|SUCCESS) user=(\S+) ip=(\S+)/;
  const EXEMPLO = [
    "2026-11-19 10:01:12 FAILED user=admin ip=192.168.1.50",
    "2026-11-19 10:01:15 FAILED user=admin ip=192.168.1.50",
    "2026-11-19 10:01:18 FAILED user=root ip=192.168.1.50",
    "2026-11-19 10:01:21 FAILED user=admin ip=192.168.1.50",
    "2026-11-19 10:01:24 FAILED user=admin ip=192.168.1.50",
    "2026-11-19 10:01:27 FAILED user=admin ip=192.168.1.50",
    "2026-11-19 10:02:03 SUCCESS user=maria ip=192.168.1.20",
    "2026-11-19 10:03:40 FAILED user=maria ip=192.168.1.20",
    "2026-11-19 10:05:10 FAILED user=joao ip=10.0.0.7",
    "2026-11-19 10:05:55 SUCCESS user=joao ip=10.0.0.7"
  ].join("\n");

  const $ = (id) => document.getElementById(id);

  $("exemplo").onclick = () => { $("log").value = EXEMPLO; };

  $("arquivo").onchange = async (e) => {
    const f = e.target.files[0];
    if (f) $("log").value = await f.text();
  };

  $("analisar").onclick = () => {
    const limite = parseInt($("limite").value, 10) || 5;
    const falhas = {};
    const usuarios = {};

    for (const linha of $("log").value.split("\n")) {
      const m = padrao.exec(linha.trim());
      if (m && m[2] === "FAILED") {
        const ip = m[4];
        falhas[ip] = (falhas[ip] || 0) + 1;
        if (!usuarios[ip]) usuarios[ip] = new Set();
        usuarios[ip].add(m[3]);
      }
    }

    const ips = Object.keys(falhas).sort((a, b) => falhas[b] - falhas[a]);
    const corpo = $("linhas");
    corpo.innerHTML = "";
    let suspeitos = 0;

    for (const ip of ips) {
      const alerta = falhas[ip] >= limite;
      if (alerta) suspeitos++;

      const tr = document.createElement("tr");
      tr.className = alerta ? "alerta" : "ok";
      const celulas = [
        ip,
        falhas[ip],
        [...usuarios[ip]].sort().join(", "),
        alerta ? "ALERTA" : "OK"
      ];
      celulas.forEach((texto, i) => {
        const td = document.createElement("td");
        td.textContent = texto;
        if (i === 3) td.className = "selo";
        tr.appendChild(td);
      });
      corpo.appendChild(tr);
    }

    $("totalIps").textContent = ips.length;
    $("totalSuspeitos").textContent = suspeitos;
    $("vazio").hidden = ips.length > 0;
    $("resultado").hidden = false;
  };
</script>
</body>
</html>
