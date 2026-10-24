# Templates de e-mail (EmailJS)

Variáveis usadas em ambos: `{{name}}`, `{{email}}`, `{{service}}`, `{{message}}`, `{{date}}`.
Cole o HTML do arquivo no editor "Code" do template no EmailJS.

## owner-notification.html (aviso ao dono)
- **Subject:** `Novo lead: {{name}} - {{service}}`
- **To email:** `enzoschitini.contact@gmail.com`
- **Reply To:** `{{email}}`
- O botão "Responder" abre `mailto:{{email}}` com assunto sugerido.

## user-confirmation.html (confirmação ao visitante)
- **Subject:** `Recebemos seu pedido, {{name}} - SkyPixel`
- **To email:** `{{email}}`
- **Reply To:** `enzoschitini.contact@gmail.com`
