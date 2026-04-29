# DEPLOY.md — Guida passo passo per mettere online fedebuilds.com

Brodi, segui queste istruzioni in ordine. Non saltare passaggi. Tempo totale stimato: 45-60 minuti.

---

## INDICE

- **Parte 1** — Comprare il dominio fedebuilds.com (10 min)
- **Parte 2** — Mettere il codice su GitHub (15 min)
- **Parte 3** — Connettere a Netlify e fare il primo deploy (10 min)
- **Parte 4** — Collegare il dominio a Netlify (15 min)
- **Parte 5** — Submitter il sito a Google (10 min)
- **Parte 6** — Test finali (5 min)

---

## PARTE 1 — Comprare il dominio (~10 min)

### Step 1.1
Vai su https://www.cloudflare.com/products/registrar/

### Step 1.2
Crea un account gratuito su Cloudflare (email + password).

### Step 1.3
Una volta dentro: clicca "Register a Domain" in alto a destra.

### Step 1.4
Cerca `fedebuilds.com`.
- Se libero: aggiungilo al carrello, costa circa 10€/anno. Procedi al pagamento.
- Se occupato: prova `fedebuilds.co` o `fedebuilds.io` o `fedebuilds.studio`. Sceglie qualcosa di pulito e ricordabile. **Avvisami quale hai preso** così aggiorno tutti i file (sono già tutti settati su `fedebuilds.com`).

### Step 1.5
Completa l'acquisto. Il dominio sarà tuo entro pochi minuti.

**ATTENZIONE**: NON comprare il dominio direttamente da Netlify. Costa di più e migrare dopo è un casino.

---

## PARTE 2 — Mettere il codice su GitHub (~15 min)

### Step 2.1
Vai su https://github.com/signup e crea un account se non ne hai uno.
Username consigliato: `fedebuilds` o `federicomicale`. Questo username apparirà negli URL di GitHub.

### Step 2.2
Una volta dentro GitHub, clicca il "+" in alto a destra → "New repository".

### Step 2.3
Compila il form:
- **Repository name**: `fedebuilds-site`
- **Description**: "Personal portfolio — Federico Micale"
- **Visibility**: scegli **Public** (più semplice da deployare gratis su Netlify, e non c'è nulla di segreto qui)
- **NON** spuntare "Add a README file", "Add .gitignore", "Choose a license" → lascia tutto vuoto
- Clicca "Create repository"

### Step 2.4
GitHub ti mostrerà una pagina con varie istruzioni. **Ignorale tutte**. Andiamo per la via facile.

### Step 2.5
Clicca su "uploading an existing file" (è un link blu nella pagina che ti appare appena creato il repo).
URL diretto: `https://github.com/TUO-USERNAME/fedebuilds-site/upload/main`

### Step 2.6
Si apre una pagina di drag-and-drop.
**Trascina dentro tutti i file della cartella `fedebuilds-site/`** che ti ho dato:
- `index.html`
- `netlify.toml`
- `robots.txt`
- `sitemap.xml`
- `site.webmanifest`
- `favicon.svg`
- `README.md`
- `DEPLOY.md` (questo file)

Aspetta che caricano (vedrai tutti i nomi nella lista).

### Step 2.7
Scorri in fondo alla pagina. Trovi un campo "Commit changes":
- Lascia il messaggio default ("Add files via upload") o scrivi "Initial commit"
- Lascia "Commit directly to the main branch" selezionato
- Clicca il pulsante verde **"Commit changes"**

### Step 2.8
Fatto. Il tuo codice è su GitHub. Lo vedi all'URL `https://github.com/TUO-USERNAME/fedebuilds-site`.

---

## PARTE 3 — Connettere a Netlify e fare il primo deploy (~10 min)

### Step 3.1
Vai su https://app.netlify.com/signup

### Step 3.2
Clicca **"Sign up with GitHub"** (è la via più semplice — Netlify ti chiederà di connettere l'account GitHub e basta).

### Step 3.3
Una volta dentro Netlify, vedrai una dashboard. Clicca il pulsante **"Add new site"** → "Import an existing project".

### Step 3.4
Clicca **"Deploy with GitHub"**.

### Step 3.5
Netlify ti chiederà di autorizzare l'accesso ai tuoi repository GitHub. Clicca "Authorize".

Ti chiederà se vuoi dargli accesso a **tutti** i repo o **solo a uno**:
- Scegli **"Only select repositories"**
- Seleziona `fedebuilds-site`
- Clicca "Install"

### Step 3.6
Torni su Netlify. Vedrai il tuo repo `fedebuilds-site` nella lista. Cliccaci sopra.

### Step 3.7
Netlify ti mostra le impostazioni di deploy. Lascia **TUTTO COSÌ COM'È** (sono già impostate giuste grazie al `netlify.toml` che ho creato).

Le opzioni saranno:
- Branch to deploy: `main`
- Build command: (vuoto)
- Publish directory: `.`

Clicca **"Deploy fedebuilds-site"** in fondo.

### Step 3.8
Netlify inizia il deploy. Aspetta 30-60 secondi.

Quando vedi "Site is live" (o "Published"), il sito è online.

### Step 3.9
Netlify ti darà un URL temporaneo tipo `https://random-words-12345.netlify.app`.
**Cliccaci sopra** per controllare che il sito funzioni.

Se carica correttamente con tutti gli stili e le animazioni → step 3 completato. Procedi.

Se vedi qualcosa di strano (testo nero su sfondo bianco, niente font), aspetta 2 minuti e ricarica. A volte i font ci mettono.

---

## PARTE 4 — Collegare il dominio fedebuilds.com a Netlify (~15 min)

Questa è la parte tecnica. Stai calmo, è solo seguire le istruzioni.

### Step 4.1 — Aggiungere il dominio in Netlify

Nella dashboard del tuo sito su Netlify:
- Vai su **"Site configuration"** → **"Domain management"** → **"Add a domain"**
- Inserisci `fedebuilds.com` → "Verify"
- Netlify ti chiederà se sei il proprietario → "Yes, add domain"
- Netlify aggiungerà sia `fedebuilds.com` sia `www.fedebuilds.com` automaticamente

### Step 4.2 — Capire i DNS records di Netlify

Netlify ti mostrerà a un certo punto due informazioni che ti serviranno:
- **Un record A** che punta a un IP (tipo `75.2.60.5`)
- **Un record CNAME** per il www

**Lascia questa pagina aperta** in una scheda del browser, ti serve.

### Step 4.3 — Configurare i DNS su Cloudflare

Apri una nuova scheda. Vai su https://dash.cloudflare.com → entra → clicca su `fedebuilds.com`.

Clicca su **"DNS"** nel menu laterale.

Vedrai una lista di record DNS già esistenti (Cloudflare ne mette alcuni di default).

**Cancella** tutti i record A e CNAME esistenti (tasto "Edit" → "Delete"). Lascia stare i record MX se ci sono (servono per le mail).

Ora aggiungi i record di Netlify. Clicca **"Add record"**:

**Record 1 — A record**
- Type: `A`
- Name: `@` (questo significa "il dominio nudo, fedebuilds.com")
- IPv4 address: `75.2.60.5` (oppure quello che ti dà Netlify, controlla)
- Proxy status: **DNS only** (la nuvola GRIGIA, non arancione)
- TTL: Auto
- Save

**Record 2 — CNAME**
- Type: `CNAME`
- Name: `www`
- Target: `tuo-sito-netlify.netlify.app` (l'URL temporaneo che Netlify ti aveva dato, senza `https://`)
- Proxy status: **DNS only** (nuvola GRIGIA)
- TTL: Auto
- Save

**ATTENZIONE**: la nuvola DEVE essere grigia (DNS only), non arancione (Proxied). Se è arancione, l'HTTPS di Netlify si rompe.

### Step 4.4 — Aspettare la propagazione DNS

I cambiamenti DNS impiegano da 5 minuti a 24 ore per propagarsi nel mondo. Di solito 10-30 minuti.

Per controllare se sono attivi: vai su https://dnschecker.org → inserisci `fedebuilds.com` → controlla. Quando vedi semafori verdi globali, sei a posto.

### Step 4.5 — Abilitare HTTPS

Torna su Netlify → "Domain management" → in fondo c'è la sezione "HTTPS".

Aspetta che il pulsante "Verify DNS configuration" diventi verde (potrebbero servire qualche minuto dopo che i DNS si propagano).

Poi clicca "Provision certificate". Netlify genera un certificato Let's Encrypt gratis, ci mette 1-2 minuti.

Quando vedi "Your site has HTTPS enabled" → fatto. Il sito è ora `https://fedebuilds.com`.

### Step 4.6 — Settare il dominio principale

Sempre in "Domain management" su Netlify:
- Trova `fedebuilds.com` nella lista
- Cliccaci sopra → "Set as primary domain"

Questo dice a Netlify che `fedebuilds.com` è il dominio "vero", e `www.fedebuilds.com` (e l'URL temporaneo) ridirigono a quello.

### Step 4.7 — Test

Apri queste URL nel browser. Devono tutte portarti a `https://fedebuilds.com`:
- `http://fedebuilds.com` → ridirige automaticamente a https
- `https://fedebuilds.com` → carica il sito
- `http://www.fedebuilds.com` → ridirige a https://fedebuilds.com
- `https://www.fedebuilds.com` → ridirige a https://fedebuilds.com

Se tutto funziona → parte 4 completata.

---

## PARTE 5 — Submetterti a Google e Bing (~10 min)

Senza questo, Google non sa che esisti.

### Step 5.1 — Google Search Console

Vai su https://search.google.com/search-console
- Login con il tuo account Google
- Clicca "Add property"
- Scegli "URL prefix" (NON "Domain")
- Inserisci `https://fedebuilds.com`
- Clicca "Continue"

Google ti chiederà di verificare che il sito sia tuo. Ti darà varie opzioni.

**Opzione consigliata: HTML tag**

- Google ti darà un meta tag tipo `<meta name="google-site-verification" content="abc123xyz" />`
- Copialo
- Vai sul tuo file `index.html` su GitHub
- Cliccalo → click sull'icona matita (in alto a destra) per editare
- Trova la sezione `<!-- ==================== SEARCH ENGINES ==================== -->`
- Aggiungi sotto i meta robots la riga che ti ha dato Google
- Scrolla in fondo, "Commit changes"
- Aspetta 30 secondi che Netlify ridepoy automaticamente
- Torna su Google Search Console → clicca "Verify"

Una volta verificato:
- Vai su "Sitemaps" nel menu laterale
- Inserisci `sitemap.xml`
- Clicca "Submit"

Da ora Google inizierà a indicizzare il sito. Aspettati 24-72 ore prima di vedere risultati.

### Step 5.2 — Bing Webmaster Tools

Stesso processo su https://www.bing.com/webmasters
- Login (puoi usare Google login)
- Add a site → `https://fedebuilds.com`
- Verifica (puoi importare automaticamente da Google Search Console — comodo)
- Submetti la sitemap: `https://fedebuilds.com/sitemap.xml`

Bing alimenta DuckDuckGo, Yahoo, e ChatGPT search. Importante.

### Step 5.3 — Aggiornare i social

Aggiungi il link `https://fedebuilds.com` ovunque:
- LinkedIn (sezione "Contact info")
- Behance (profilo)
- Vimeo (profilo)
- Instagram bio
- Twitter/X bio
- Email signature

Ogni link da queste piattaforme è un "voto" per Google. Più ne hai, prima ti indicizzano e meglio ti posizionano.

---

## PARTE 6 — Test finali (~5 min)

Vai su queste URL e fai i test. Se qualcosa non va, scrivimi.

### Test 1 — Velocità
https://pagespeed.web.dev/
- Inserisci `https://fedebuilds.com`
- Clicca "Analyze"
- Target: 90+ su mobile e desktop

### Test 2 — Sicurezza
https://securityheaders.com/
- Inserisci `fedebuilds.com`
- Target: A o A+

### Test 3 — Mobile-friendly
https://search.google.com/test/mobile-friendly
- Inserisci `https://fedebuilds.com`
- Deve dire "Page is mobile friendly"

### Test 4 — Schema valido
https://validator.schema.org/
- Inserisci `https://fedebuilds.com`
- Deve trovare 3 oggetti: Person, ProfessionalService, WebSite, FAQPage
- Tutti senza errori

### Test 5 — Open Graph (preview link)
https://www.opengraph.xyz/
- Inserisci `https://fedebuilds.com`
- Vedrai come appare quando incolli il link su LinkedIn, Twitter, etc.
- (Apparirà brutto finché non sostituisci `og-image.jpg` con un'immagine vera)

---

## E adesso?

Hai un sito online, ottimizzato, sicuro e indicizzato.

Cose da fare nei prossimi giorni:
1. Crea l'`og-image.jpg` (1200x630, sfondo cream, tipografia tipo "FEDEBUILDS / MOTION DESIGNER / MILAN")
2. Crea i favicon mancanti (puoi usare https://realfavicongenerator.net/)
3. Aggiungi i video dei progetti veri (avvisami e ti aiuto a integrarli)
4. Inizia a fare cold outreach a studi linkando il sito

Ogni volta che vuoi modificare qualcosa:
1. Vai su GitHub → tuo repo → file da modificare
2. Click matita per editare
3. Modifica
4. Commit changes
5. Netlify ridepoy automatico in 30 secondi

---

## Problemi comuni

**"Il sito non carica"**
- Aspetta 5 minuti, i DNS impiegano
- Controlla su https://dnschecker.org se il dominio è propagato

**"HTTPS non funziona"**
- Vai su Netlify → Domain management → HTTPS → "Renew certificate"
- Aspetta 5 minuti

**"Ho fatto una modifica ma non si vede"**
- Vai su Netlify → Deploys → controlla se c'è un deploy in corso
- Hard refresh sul browser: Ctrl+Shift+R (Mac: Cmd+Shift+R)
- Se ancora non si vede: è cache del browser. Aspetta o usa modalità incognito.

**"Google non mi indicizza"**
- Aspetta 1-2 settimane
- Su Search Console vai su "URL Inspection" → inserisci https://fedebuilds.com → "Request indexing"

---

Se ti blocchi a qualche step, fammi sapere quale e ti sblocco. In bocca al lupo brodi.
