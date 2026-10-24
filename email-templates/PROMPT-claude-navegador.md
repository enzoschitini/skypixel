Você vai configurar o EmailJS para o formulário de contato de um site. Já estou logada(o) em https://dashboard.emailjs.com/admin. Faça tudo no painel e, no final, me devolva 4 valores. Se algum passo já existir (serviço ou template), reaproveite em vez de duplicar. Não me peça senhas e não altere nada além do descrito.

## Passo 1 — Serviço de e-mail
Em "Email Services", garanta que existe um serviço **Gmail** conectado à conta `enzoschitini.contact@gmail.com`. Se não existir, clique em "Add New Service", escolha Gmail e conecte essa conta (se pedir autorização do Google, me avise e eu confirmo). Anote o **Service ID** (formato `service_xxxxxxx`).

## Passo 2 — Template "Aviso" (chega para o dono)
Em "Email Templates" → "Create New Template". Nome: `SkyPixel - Aviso novo lead`.
- Aba Settings:
  - To email: `enzoschitini.contact@gmail.com`
  - Reply To: `{{email}}`
  - Subject: `Novo lead: {{name}} - {{service}}`
  - From name: `SkyPixel Site`
- Aba Content: troque para o editor de código (ícone `<>` / "Edit Content" → "Code Editor"), apague tudo e cole exatamente o HTML abaixo. Salve (Save).

```html
<!DOCTYPE html>
<html lang="pt-BR" xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="color-scheme" content="light dark">
<meta name="supported-color-schemes" content="light dark">
<title>Novo lead - SkyPixel</title>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;800&display=swap" rel="stylesheet">
<style>
  @media only screen and (max-width:620px){.wrap{width:100%!important}.pad{padding-left:20px!important;padding-right:20px!important}}
  @media (prefers-color-scheme:dark){
    .bg{background-color:#121212!important}
    .card{background-color:#1e1e1e!important}
    .t-ink{color:#f2f2f2!important}
    .t-muted{color:#9a9a9a!important}
    .line{border-color:#333333!important}
    .box{background-color:#2a2a2a!important}
    .btn-a{background-color:#d9e6a8!important;color:#111111!important}
  }
</style>
</head>
<body class="bg" style="margin:0;padding:0;background-color:#f2f2f2;-webkit-text-size-adjust:100%;">
<div style="display:none;max-height:0;overflow:hidden;opacity:0;">Novo contato de {{name}} sobre {{service}}.</div>
<table role="presentation" width="100%" cellpadding="0" cellspacing="0" border="0" class="bg" style="background-color:#f2f2f2;">
<tr><td align="center" style="padding:32px 12px;">
<table role="presentation" class="wrap" width="600" cellpadding="0" cellspacing="0" border="0" style="width:600px;max-width:600px;">
  <tr><td class="pad" style="padding:0 8px 20px 8px;font-family:Inter,'Segoe UI',Roboto,Arial,sans-serif;">
    <span class="t-ink" style="font-size:20px;font-weight:800;letter-spacing:.12em;color:#111111;">SKYPIXEL</span>
  </td></tr>
  <tr><td class="card" style="background-color:#ffffff;border-radius:20px;">
    <table role="presentation" width="100%" cellpadding="0" cellspacing="0" border="0">
      <tr><td bgcolor="#d9e6a8" class="pad" style="background-color:#d9e6a8;border-radius:20px 20px 0 0;padding:28px 36px;font-family:Inter,'Segoe UI',Roboto,Arial,sans-serif;">
        <div style="font-size:12px;font-weight:500;letter-spacing:.14em;text-transform:uppercase;color:#111111;">Novo lead pelo site</div>
        <div style="font-size:28px;line-height:1.2;font-weight:800;color:#111111;margin-top:8px;">{{name}} quer um orçamento.</div>
      </td></tr>
      <tr><td class="pad" style="padding:32px 36px 8px 36px;font-family:Inter,'Segoe UI',Roboto,Arial,sans-serif;">
        <table role="presentation" width="100%" cellpadding="0" cellspacing="0" border="0">
          <tr><td class="line" style="padding:14px 0;border-bottom:1px solid #dddddd;">
            <div class="t-muted" style="font-size:12px;letter-spacing:.08em;text-transform:uppercase;color:#6b6b6b;">Nome</div>
            <div class="t-ink" style="font-size:16px;font-weight:500;color:#111111;margin-top:4px;">{{name}}</div>
          </td></tr>
          <tr><td class="line" style="padding:14px 0;border-bottom:1px solid #dddddd;">
            <div class="t-muted" style="font-size:12px;letter-spacing:.08em;text-transform:uppercase;color:#6b6b6b;">E-mail</div>
            <div style="font-size:16px;font-weight:500;margin-top:4px;"><a href="mailto:{{email}}" class="t-ink" style="color:#111111;text-decoration:underline;">{{email}}</a></div>
          </td></tr>
          <tr><td class="line" style="padding:14px 0;border-bottom:1px solid #dddddd;">
            <div class="t-muted" style="font-size:12px;letter-spacing:.08em;text-transform:uppercase;color:#6b6b6b;">Serviço</div>
            <div class="t-ink" style="font-size:16px;font-weight:500;color:#111111;margin-top:4px;">{{service}}</div>
          </td></tr>
          <tr><td class="line" style="padding:14px 0;border-bottom:1px solid #dddddd;">
            <div class="t-muted" style="font-size:12px;letter-spacing:.08em;text-transform:uppercase;color:#6b6b6b;">Recebido em</div>
            <div class="t-ink" style="font-size:16px;font-weight:500;color:#111111;margin-top:4px;">{{date}}</div>
          </td></tr>
        </table>
      </td></tr>
      <tr><td class="pad" style="padding:20px 36px 8px 36px;font-family:Inter,'Segoe UI',Roboto,Arial,sans-serif;">
        <div class="t-muted" style="font-size:12px;letter-spacing:.08em;text-transform:uppercase;color:#6b6b6b;margin-bottom:8px;">Mensagem</div>
        <div class="box t-ink" style="background-color:#f2f2f2;border-radius:14px;padding:18px 20px;font-size:15px;line-height:1.6;color:#111111;white-space:pre-wrap;">{{message}}</div>
      </td></tr>
      <tr><td class="pad" style="padding:28px 36px 12px 36px;">
        <table role="presentation" cellpadding="0" cellspacing="0" border="0"><tr>
          <td bgcolor="#111111" class="btn-a" style="background-color:#111111;border-radius:999px;">
            <a href="mailto:{{email}}?subject=Sua%20proposta%20SkyPixel%20-%20{{service}}" class="btn-a" style="display:inline-block;padding:14px 30px;font-size:14px;font-weight:500;color:#ffffff;text-decoration:none;border-radius:999px;font-family:Inter,'Segoe UI',Roboto,Arial,sans-serif;">Responder a {{name}}</a>
          </td>
        </tr></table>
      </td></tr>
      <tr><td class="pad" style="padding:8px 36px 32px 36px;font-family:Inter,'Segoe UI',Roboto,Arial,sans-serif;">
        <div class="t-muted" style="font-size:13px;line-height:1.5;color:#6b6b6b;">Assunto sugerido: <span class="t-ink" style="color:#111111;">Sua proposta SkyPixel - {{service}}</span></div>
      </td></tr>
    </table>
  </td></tr>
  <tr><td align="center" class="pad t-muted" style="padding:20px 12px;font-family:Inter,'Segoe UI',Roboto,Arial,sans-serif;font-size:12px;color:#6b6b6b;">Mensagem automática do formulário do site SkyPixel.</td></tr>
</table>
</td></tr>
</table>
</body>
</html>
```

Anote o **Template ID** (formato `template_xxxxxxx`) como "TEMPLATE_AVISO".

## Passo 3 — Template "Confirmação" (chega para o visitante)
Crie outro template. Nome: `SkyPixel - Confirmação visitante`.
- Aba Settings:
  - To email: `{{email}}`
  - Reply To: `enzoschitini.contact@gmail.com`
  - Subject: `Recebemos seu pedido, {{name}} - SkyPixel`
  - From name: `SkyPixel`
- Aba Content: editor de código, apague tudo e cole exatamente o HTML abaixo. Salve.

```html
<!DOCTYPE html>
<html lang="pt-BR" xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="color-scheme" content="light dark">
<meta name="supported-color-schemes" content="light dark">
<title>Recebemos seu pedido - SkyPixel</title>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;800&display=swap" rel="stylesheet">
<style>
  @media only screen and (max-width:620px){.wrap{width:100%!important}.pad{padding-left:20px!important;padding-right:20px!important}}
  @media (prefers-color-scheme:dark){
    .bg{background-color:#121212!important}
    .card{background-color:#1e1e1e!important}
    .t-ink{color:#f2f2f2!important}
    .t-muted{color:#9a9a9a!important}
    .box{background-color:#2a2a2a!important}
  }
</style>
</head>
<body class="bg" style="margin:0;padding:0;background-color:#f2f2f2;-webkit-text-size-adjust:100%;">
<div style="display:none;max-height:0;overflow:hidden;opacity:0;">Recebemos seu pedido e voltamos com uma proposta em breve.</div>
<table role="presentation" width="100%" cellpadding="0" cellspacing="0" border="0" class="bg" style="background-color:#f2f2f2;">
<tr><td align="center" style="padding:32px 12px;">
<table role="presentation" class="wrap" width="600" cellpadding="0" cellspacing="0" border="0" style="width:600px;max-width:600px;">
  <tr><td class="pad" style="padding:0 8px 20px 8px;font-family:Inter,'Segoe UI',Roboto,Arial,sans-serif;">
    <span class="t-ink" style="font-size:20px;font-weight:800;letter-spacing:.12em;color:#111111;">SKYPIXEL</span>
  </td></tr>
  <tr><td class="card" style="background-color:#ffffff;border-radius:20px;">
    <table role="presentation" width="100%" cellpadding="0" cellspacing="0" border="0">
      <tr><td bgcolor="#d9e6a8" class="pad" style="background-color:#d9e6a8;border-radius:20px 20px 0 0;padding:36px;font-family:Inter,'Segoe UI',Roboto,Arial,sans-serif;">
        <div style="font-size:12px;font-weight:500;letter-spacing:.14em;text-transform:uppercase;color:#111111;">Pedido recebido</div>
        <div style="font-size:30px;line-height:1.2;font-weight:800;color:#111111;margin-top:8px;">Obrigado, {{name}}!</div>
      </td></tr>
      <tr><td class="pad" style="padding:32px 36px 8px 36px;font-family:Inter,'Segoe UI',Roboto,Arial,sans-serif;">
        <p class="t-ink" style="margin:0 0 16px 0;font-size:16px;line-height:1.6;color:#111111;">Recebemos o seu contato e já estamos analisando. Em breve voltamos com uma proposta sob medida para o seu projeto.</p>
        <p class="t-muted" style="margin:0;font-size:14px;line-height:1.6;color:#6b6b6b;">Enviado em {{date}}</p>
      </td></tr>
      <tr><td class="pad" style="padding:20px 36px 8px 36px;font-family:Inter,'Segoe UI',Roboto,Arial,sans-serif;">
        <div class="box" style="background-color:#f2f2f2;border-radius:14px;padding:20px;">
          <div class="t-muted" style="font-size:12px;letter-spacing:.08em;text-transform:uppercase;color:#6b6b6b;">Serviço</div>
          <div class="t-ink" style="font-size:16px;font-weight:500;color:#111111;margin:4px 0 16px 0;">{{service}}</div>
          <div class="t-muted" style="font-size:12px;letter-spacing:.08em;text-transform:uppercase;color:#6b6b6b;">Sua mensagem</div>
          <div class="t-ink" style="font-size:15px;line-height:1.6;color:#111111;margin-top:4px;white-space:pre-wrap;">{{message}}</div>
        </div>
      </td></tr>
      <tr><td class="pad" style="padding:24px 36px 36px 36px;font-family:Inter,'Segoe UI',Roboto,Arial,sans-serif;">
        <p class="t-ink" style="margin:0;font-size:16px;line-height:1.6;color:#111111;">Até já,<br><strong style="font-weight:800;letter-spacing:.12em;">SKYPIXEL</strong><br><span class="t-muted" style="font-size:13px;color:#6b6b6b;">Filmagem e fotografia com drone em 4K</span></p>
      </td></tr>
    </table>
  </td></tr>
  <tr><td align="center" class="pad t-muted" style="padding:20px 12px;font-family:Inter,'Segoe UI',Roboto,Arial,sans-serif;font-size:12px;line-height:1.5;color:#6b6b6b;">Você recebeu este e-mail porque enviou o formulário em nosso site.<br>Se quiser acrescentar algo, é só responder esta mensagem.</td></tr>
</table>
</td></tr>
</table>
</body>
</html>
```

Anote o **Template ID** como "TEMPLATE_CONFIRMACAO".

## Passo 4 — Public Key
Em "Account" → aba "General", copie a **Public Key**.

## Passo 5 — Segurança (opcional, só se for simples)
Em "Account" → "Security", se houver opção de restringir domínios permitidos, me diga o que aparece; não altere sem me perguntar.

## O que me devolver (exatamente neste formato)
```
PUBLIC_KEY: ...
SERVICE_ID: ...
TEMPLATE_AVISO: ...
TEMPLATE_CONFIRMACAO: ...
```
Se algo falhar ou pedir confirmação minha (autorização do Google, plano, limite), pare e me diga em vez de improvisar.
