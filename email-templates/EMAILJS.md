# Envio de e-mail do formulário (EmailJS)

O formulário de contato (`#subForm` em `index.html`) envia e-mail pelo **EmailJS**
(https://dashboard.emailjs.com), direto do navegador, sem backend. Cada envio dispara
dois e-mails:

| E-mail | Template | Destinatário |
|---|---|---|
| Aviso de novo lead | `owner-notification.html` | `enzoschitini.contact@gmail.com` |
| Confirmação ao visitante | `user-confirmation.html` | e-mail digitado no formulário |

O segundo e-mail sai 1,2 s depois do primeiro, porque o plano grátis do EmailJS limita
a cerca de 1 envio por segundo.

## Onde configurar no painel

Painel: https://dashboard.emailjs.com/admin

| Item | Onde no painel | Constante no `index.html` | Valor atual |
|---|---|---|---|
| Public Key | Account → General | `EMAILJS_PUBLIC_KEY` | `Kvl0j59dGcrlVm4Rl` |
| Service ID | Email Services (Gmail `enzoschitini.contact@gmail.com`) | `EMAILJS_SERVICE_ID` | `service_tbbqtk6` |
| Template do aviso | Email Templates | `EMAILJS_TEMPLATE_OWNER` | `template_dg9ri7n` |
| Template da confirmação | Email Templates | `EMAILJS_TEMPLATE_USER` | `template_4shukmk` |

As constantes ficam logo acima do handler do formulário, perto do fim do `index.html`.
A Public Key e os IDs não são segredos (ficam visíveis no site); a proteção é a
restrição de domínio em Account → Security.

## Configuração de cada template (aba Settings)

**Aviso (`template_dg9ri7n`)**
- To email: `enzoschitini.contact@gmail.com`
- Reply To: `{{email}}`
- Subject: `Novo lead: {{name}} - {{service}}`
- Conteúdo: HTML de `owner-notification.html`

**Confirmação (`template_4shukmk`)**
- To email: `{{email}}` (exatamente assim; se estiver vazio ou fixo, o visitante não recebe)
- Reply To: `enzoschitini.contact@gmail.com`
- Subject: `Recebemos seu pedido, {{name}} - SkyPixel`
- Conteúdo: HTML de `user-confirmation.html`

## Variáveis enviadas pelo site

Os nomes precisam ser exatamente estes, nos templates e no objeto `params` do `index.html`:

| Variável | Origem no formulário |
|---|---|
| `{{name}}` | campo Nome (`#subName`) |
| `{{email}}` | campo E-mail (`#email`) |
| `{{service}}` | campo Serviço (`#subService`) |
| `{{message}}` | campo Mensagem (`#subMsgText`); "(sem mensagem)" se vazio |
| `{{date}}` | data e hora do envio, `pt-BR` |

Use sempre `{{var}}` (duas chaves); o EmailJS escapa o conteúdo.

## Script no site

`index.html` carrega o SDK no `<head>`:
`https://cdn.jsdelivr.net/npm/@emailjs/browser@4.4.1/dist/email.min.js`

## Limites e cuidados

- Plano grátis: cerca de 200 e-mails por mês. Cada envio do formulário gasta 2, então
  são cerca de 100 contatos por mês.
- Restringir a Public Key aos domínios do site em Account → Security (incluir
  `127.0.0.1` para testes locais, se necessário).
- Se um e-mail não chegar: console do navegador (F12) mostra `EmailJS:` ou
  `EmailJS (confirmação):` com o motivo; a aba History/Logs do EmailJS mostra o que
  saiu; confira o spam.
