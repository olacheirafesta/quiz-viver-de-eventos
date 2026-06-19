# Quiz · Será que viver de eventos é mesmo para ti?

Réplica em HTML do quiz do Typeform (`zwy0TTKZ`), para alojar no GitHub e embeber no Wix.
Uma pergunta de cada vez, paleta **beige + verde** do EBS Summer Camp (fundo `#FAF7F1`, verde `#2E5135`, títulos `#1F2A1B`), Playfair + Helvetica.

## O que faz
- 7 perguntas (pontuação idêntica ao Typeform) → email → nome → resultado.
- **Routing por pontuação** (decisão: os 2 do topo vão para O Plano):
  | Pontos | Resultado | Vai para |
  |---|---|---|
  | 22–27 | Estás pronta para o próximo nível | **O Plano** (com UTMs) |
  | 17–21 | É para ti | **O Plano** (com UTMs) |
  | 12–16 | Estás a começar pelo sítio errado | YouTube `j-wETMZmQ6o` |
  | 7–11 | O medo está a falar mais alto | YouTube `xF7hqBVo-go` |
  | 0–6 | Talvez ainda não seja o teu momento | YouTube `zkzTgQLjEk8` |
- **UTMs no Plano:** `?utm_source=quiz&utm_medium=site&utm_campaign=viver-de-eventos&utm_content=<resultado>` — para veres no Stripe/Woo quem comprou vindo do quiz.
- **Captura de leads:** email + nome → grupo MailerLite **"LM - Quizz - Abril 2026"** (o mesmo do Typeform), via endpoint público do formulário (sem expor chaves).

## Ficheiros
- `index.html` — o quiz (auto-contido, só depende de `assets/`).
- `assets/playfair.css` — fonte Playfair embutida.
- `assets/monogram-white.png` — monograma.
- `.nojekyll` — evita que o GitHub Pages ignore ficheiros `_…`.
- `server.py` — só para pré-visualizar localmente (`python3 server.py` → http://localhost:8120).

## Publicar no GitHub Pages
1. Criar um repositório novo (ex. `olacheirafesta/quiz-viver-de-eventos`).
2. Carregar o conteúdo desta pasta para a raiz do repo.
3. **Settings → Pages → Branch: `main` / `/root` → Save.**
4. Fica disponível em `https://olacheirafesta.github.io/quiz-viver-de-eventos/`.

## Embeber no Wix
1. Adicionar um elemento **Embed → Incorporar um site (iFrame)**.
2. URL: o link do GitHub Pages acima.
3. Altura sugerida: **~640px** (os resultados longos fazem scroll dentro do iframe).
4. Os botões usam `target="_top"`, por isso o Plano/YouTube abrem na janela inteira (não dentro do iframe).

## Mudar coisas (tudo no topo do `<script>` em `index.html`)
- **Link do Plano / UTMs:** objecto `CONFIG.plano`.
- **Grupo / captura MailerLite:** `CONFIG.mailerlite.endpoint` (`enabled:false` desliga a captura).
- **Perguntas e pontos:** array `QUESTIONS`.
- **Resultados, vídeos e quem vai para o Plano:** array `OUTCOMES` (`type:'plano'` ou `type:'youtube'`).

## Nota · double opt-in
O formulário MailerLite ligado a este quiz ficou com **double opt-in ligado** por defeito — ou seja, o lead recebe um email de confirmação e só entra na lista activa depois de confirmar. Se quiseres que entrem logo (como no Typeform), desliga o double opt-in nas definições do formulário/conta no MailerLite.
