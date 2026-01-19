<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IMPÉRIO CITY | RECRUTAMENTO</title>
    <style>
        body { background: #050507; color: #fff; font-family: sans-serif; display: flex; justify-content: center; padding: 20px; }
        .card { width: 100%; max-width: 500px; background: #111; border: 1px solid #00f2ff; padding: 25px; border-radius: 15px; box-shadow: 0 0 20px #00f2ff33; }
        h1 { color: #00f2ff; text-align: center; font-size: 1.5rem; text-shadow: 0 0 10px #00f2ff; text-transform: uppercase; }
        input, textarea { width: 100%; padding: 12px; margin: 10px 0; background: #000; border: 1px solid #333; color: #fff; border-radius: 5px; box-sizing: border-box; }
        .btn { width: 100%; padding: 15px; background: transparent; border: 2px solid #00f2ff; color: #00f2ff; font-weight: bold; cursor: pointer; transition: 0.3s; }
        .btn:hover { background: #00f2ff; color: #000; }
    </style>
</head>
<body>

<div class="card">
    <h1>🛡️ IMPÉRIO CITY</h1>
    <form id="formLog">
        <input type="text" id="n" placeholder="Nome RP" required>
        <input type="text" id="r" placeholder="Nick Roblox" required>
        <textarea id="m" placeholder="Por que quer fazer parte do Império City?" rows="4" required></textarea>
        <button type="submit" class="btn" id="b">ENVIAR PARA STAFF</button>
    </form>
</div>

<script>
    document.getElementById('formLog').addEventListener('submit', function(e) {
        e.preventDefault();
        
        // Seu Webhook já configurado
        const LINK_WEBHOOK = "https://discord.com/api/webhooks/1462910114800472311/Ss0lztssB9GScoy0MdYGMSj2lh7eYoJvig-IWsoNIj0n535MS0y-1WwRYhtrALyROFju";

        const btn = document.getElementById('b');
        btn.innerText = "ENVIANDO...";
        btn.disabled = true;

        const dados = {
            content: "🔔 **NOVO FORMULÁRIO RECEBIDO!** <@1395820830847668274>",
            embeds: [{
                title: "🛡️ RECRUTAMENTO - IMPÉRIO CITY",
                description: "Uma nova ficha foi enviada pelo site.",
                color: 65535,
                fields: [
                    { name: "👤 Nome RP", value: document.getElementById('n').value, inline: true },
                    { name: "🎮 Roblox", value: document.getElementById('r').value, inline: true },
                    { name: "📝 Motivo/Mensagem", value: document.getElementById('m').value }
                ],
                footer: { text: "Império City Logs" },
                timestamp: new Date()
            }]
        };

        fetch(LINK_WEBHOOK, {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify(dados)
        }).then(() => {
            alert("✅ Enviado com sucesso para o Império City!");
            btn.innerText = "ENVIADO!";
        }).catch(() => {
            alert("❌ Erro ao enviar.");
            btn.disabled = false;
            btn.innerText = "TENTAR NOVAMENTE";
        });
    });
</script>
</body>
</html>
