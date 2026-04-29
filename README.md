# FedeBuilds — Personal Portfolio Site

Sito personale di Federico Micale (FedeBuilds), motion designer e video editor basato a Milano.

---

## Struttura del progetto

```
fedebuilds-site/
├── index.html           ← Il sito principale
├── netlify.toml         ← Configurazione hosting + sicurezza
├── robots.txt           ← Permessi per Google e AI bots
├── sitemap.xml          ← Mappa del sito per i motori di ricerca
├── site.webmanifest     ← Configurazione "app-like" su mobile
├── favicon.svg          ← Icona del sito (placeholder, da sostituire)
└── README.md            ← Questo file
```

---

## File da creare/sostituire prima del deploy

Il sito è completo nel codice ma alcuni asset visivi sono **placeholder**. Sostituiscili quando hai tempo:

### Obbligatori (per non avere il sito "rotto"):

1. **`og-image.jpg`** (1200×630 px, JPG, max 200 KB)
   È l'immagine che si vede quando incolli il link su LinkedIn, WhatsApp, Discord, Twitter, etc.
   Deve essere bella perché è il tuo "biglietto da visita social".
   Suggerimento: sfondo cream `#F4F1EC`, testo "FEDEBUILDS / Motion Designer / Milan" in Inter Tight bold nero.
   Mettila nella root della cartella accanto a index.html.

2. **`favicon-32.png`, `favicon-16.png`** (PNG, le dimensioni del nome)
   Versioni PNG del favicon per browser vecchi. Esporta dal tuo logo.

3. **`apple-touch-icon.png`** (180×180 px, PNG)
   Icona quando uno aggiunge il sito alla home iPhone.

4. **`favicon-192.png`, `favicon-512.png`** (PNG, le dimensioni del nome)
   Per il webmanifest. Stesso logo, dimensioni diverse.

### Da sostituire quando hai i contenuti:

5. **I video dei progetti** (.webm e .mp4 in cartella `/videos/`)
   Quando li avrai, dimmi e te li integro nel codice.

---

## Cosa serve per il deploy

- Account GitHub (gratis): https://github.com/signup
- Account Netlify (gratis): https://app.netlify.com/signup → "Sign up with GitHub"
- Dominio `fedebuilds.com` (~10€/anno)
  - Consigliato: comprarlo su Cloudflare Registrar o Namecheap (NON su Netlify, costa di più)

---

## Guida completa al deploy

Vedi il file `DEPLOY.md` per la procedura passo-passo.

---

## Manutenzione

- **Aggiorna `<lastmod>` in `sitemap.xml`** ogni volta che fai modifiche importanti
- **Aggiungi un nuovo progetto al mese** se possibile (Google premia i siti vivi)
- **Aggiorna il banner "Available — Q2 2026"** quando cambia trimestre

---

## Contatti

Federico Micale
Milan, Italy
micale.federicoo@gmail.com
