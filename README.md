[README.md](https://github.com/user-attachments/files/31980144/README.md)
# Mundo Amarelo — site de conscientização e denúncia anônima

Site estático (HTML/CSS/JS puro, sem build), pronto para publicar no **GitHub Pages**.

## Estrutura

```
index.html              → Início
isso-e-bullying.html    → Isso é bullying?
estou-sofrendo.html     → Estou sofrendo
presenciei.html         → Presenciei
ajuda.html              → Onde pedir ajuda
denuncia.html           → Formulário de denúncia anônima (envia por e-mail)
style.css               → Estilo (amarelo + branco)
nav.js                  → Menu mobile
```

## 1. Configurar o envio para o seu e-mail (Formspree — gratuito)

Como o GitHub Pages só hospeda sites estáticos (sem servidor próprio), o formulário
usa o serviço gratuito **Formspree** para receber os dados e encaminhar por e-mail.
Isso leva ~2 minutos:

1. Acesse **https://formspree.io** e crie uma conta gratuita (até 50 envios/mês).
2. Clique em **"+ New Form"**, dê um nome (ex: "Denúncia Mundo Amarelo") e informe
   o e-mail para onde as denúncias devem chegar — o seu.
3. O Formspree vai te dar um endpoint parecido com:
   `https://formspree.io/f/abcdwxyz`
4. Abra o arquivo **`denuncia.html`** e troque `SEU_ID_AQUI` (aparece 1 vez,
   no atributo `action` do `<form>`) pelo código que você recebeu:

   ```html
   <form id="report-form" action="https://formspree.io/f/abcdwxyz" method="POST">
   ```

5. Salve. Pronto — toda denúncia enviada pelo site cai no seu e-mail automaticamente.
6. Na primeira denúncia de teste, o Formspree manda um e-mail de confirmação —
   é só confirmar uma vez para ativar o formulário de vez.

> O formulário não pede nome nem e-mail (o campo de e-mail é opcional, para quem
> quiser resposta). Nenhum outro dado de identificação é coletado.

## 2. Publicar no GitHub Pages

1. Crie um repositório novo no GitHub (pode ser público), ex: `mundo-amarelo`.
2. Envie todos os arquivos desta pasta para a raiz do repositório
   (pelo site do GitHub: "Add file" → "Upload files", ou via git):

   ```bash
   git init
   git add .
   git commit -m "Site Mundo Amarelo"
   git branch -M main
   git remote add origin https://github.com/SEU_USUARIO/mundo-amarelo.git
   git push -u origin main
   ```

3. No repositório, vá em **Settings → Pages**.
4. Em "Source", escolha a branch `main` e a pasta `/ (root)`. Salve.
5. Em alguns minutos o site estará em:
   `https://SEU_USUARIO.github.io/mundo-amarelo/`

## 3. Personalizar (opcional)

- **Cores**: todas ficam no topo do `style.css`, dentro de `:root { ... }`.
- **Textos**: cada página é um `.html` separado — edite o texto direto no arquivo.
- **Nome do site**: procure "Mundo Amarelo" e troque em todos os arquivos
  (título da aba do navegador, cabeçalho e rodapé).
- **Limite de denúncias grátis**: se passar de 50/mês no Formspree, dá para
  trocar por outro serviço parecido (ex: Web3Forms, EmailJS) só mudando o
  `action` do formulário e o endereço no `fetch`.

## Aviso importante

Este site é informativo e de encaminhamento. Ele não substitui atendimento em
situação de risco imediato: nesse caso, oriente a ligar para o **190** (Polícia)
ou **188** (CVV).
