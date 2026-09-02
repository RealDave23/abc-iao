# A-B-C-iao! — stato del progetto

_Ultimo aggiornamento: 2 settembre 2026_

Gioco web interattivo in italiano per imparare **lettere, sillabe e numeri**, pensato
per una bambina di 6 anni che inizia la **prima elementare il 14 settembre 2026**.
Un solo file (`index.html`), nessuna build, funziona offline dopo il primo caricamento.

---

## Dove si trova

| Cosa | Link |
|---|---|
| **Sito live (produzione)** | https://abc-iao.vercel.app |
| Repo GitHub | https://github.com/RealDave23/abc-iao |
| Pannello Vercel | https://vercel.com/real-dave3d/abc-iao |
| Claude Artifact (copia) | https://claude.ai/code/artifact/853b8813-108d-44d1-abd4-3911ca35d75e |

Progetto Vercel `abc-iao` (team RealDave3d). Il repo GitHub **non è ancora collegato**
a Vercel: per l'auto-deploy on-push va installata la Vercel GitHub App
(https://github.com/apps/vercel) sul repo. Finché non è collegato, i deploy si fanno a mano.

---

## Il nome e l'identità

- **A-B-C-iao!** = "ABC" + "Ciao!". Si capisce subito che è un gioco per bambini.
- **Logo/wordmark**: le lettere A, B, C come cubetti arrotondati e inclinati
  (arancio, blu, verde), trattini grigi, poi "iao" viola e "!" arancio.
- **Icona**: gli stessi tre cubetti A/B/C su fondo crema.
- **Font**: Fredoka (titoli/lettere) + Nunito (testo).
- **Palette per vocali**: A arancio · E blu · I verde · O viola · U giallo.
- File grafici pronti (PNG): logo trasparente, icona quadrata 1024/512/180,
  card social 1080×1080 / 1200×630 / 1080×1920.

---

## Cosa contiene (9 attività + collezione)

1. **L'alfabeto** — A→Z, ogni lettera con parola + disegno, maiuscola/minuscola, badge "lettera straniera" per J K W X Y.
2. **Le sillabe** — 3 modalità:
   - *Impara*: il sillabario (MA-ME-MI-MO-MU per 14 consonanti) + parola esempio.
   - *Gioca*: ascolta la sillaba e toccala tra 4 scelte.
   - *Parole*: unisci le sillabe nell'ordine giusto per fare la parola (CASA, BANANA…).
3. **I numeri** — da 1 a 20: cifra grande + parola + tanti oggetti da contare.
4. **Ricalca col dito** — segui lettere/numeri (stampato maiuscolo) col dito sul "quaderno".
5. **Ascolta e tocca** — senti la lettera/numero e trovalo, senza aiuto a schermo.
6. **Trova la lettera** — vedi la lettera grande e tocca quella uguale tra 4.
7. **Conta gli oggetti** — "quanti ne vedi?" con 3 numeri tra cui scegliere.
8. **Scrivi tu!** — ascolta e scrivi la lettera/numero col dito; riconoscimento
   della calligrafia (tolleranza generosa, si accetta anche dopo qualche tentativo).
9. **La mia collezione** — le stelle guadagnate sbloccano **18 adesivi** + 1 speciale
   ("la coppa d'oro" a 350⭐ quando li hai tutti). Sblocco con jingle e festa.

Feedback: audio italiano (voce del dispositivo), suoni WebAudio (giusto = arpeggio,
sbagliato = suono dolce, sblocco = jingle magico), coriandoli. Nessuna penalità:
gli errori incoraggiano e basta. Tema chiaro e scuro. Rispetta "riduci animazioni".

---

## Note tecniche

- **Un file**: `index.html` (~81 KB) = tutta l'app. `favicon` SVG inline.
- **Icone/manifest**: `apple-touch-icon.png`, `icon-192.png`, `icon-512.png`,
  `manifest.webmanifest`. Nell'`index.html` l'apple-touch-icon punta alle immagini
  su `raw.githubusercontent.com/RealDave23/abc-iao/main/…` (limite degli strumenti
  di deploy: le immagini binarie passano solo così).
- **Mobile**: ogni schermata di gioco sta in `100dvh` **senza scroll**
  (layout flex verticale, riquadro di disegno limitato a `40dvh`, note nascoste
  sotto i 780px di altezza). Scorrono solo la home e la collezione.
- **Salvataggi**: stelle, adesivi e impostazione audio in `localStorage`
  (chiavi `lettere-numeri-stelle`, `lettere-numeri-muto`). Restano su quel
  dispositivo/browser, non si sincronizzano.
- Sorgente di lavoro: `lettere-numeri.html` (formato Claude Artifact). La versione
  Vercel si genera avvolgendolo in un documento HTML completo.

---

## Come aggiornare il sito

**Ora (repo non collegato):** si rifà un deploy manuale (`deploy_to_vercel`).
I file di testo (`index.html`, `manifest.webmanifest`) passano direttamente;
le immagini restano su GitHub raw.

**Meglio:** installare la Vercel GitHub App sul repo `abc-iao` → collegarlo a Vercel
→ da lì basta `git push` e Vercel ridistribuisce da solo.

---

## Idee / richieste aperte

- [x] **Schermata di benvenuto al primo avvio**: chiede nome ed età, li salva sul
      dispositivo (`localStorage`, chiave `abciao-utente`), personalizza il saluto in
      home ("Ciao Sofia!") e mostra chi sta giocando nella collezione (con "cambia").
      Sotto i 6 anni "Conta gli oggetti" e "Ascolta e tocca (123)" restano entro il 5.
      _(fatto — 2 set 2026, live)_
- [ ] Collegare il repo GitHub a Vercel per l'auto-deploy.
- [ ] Eventuale dominio più corto (`abciao.vercel.app` o dominio proprio).
- [ ] Modalità "ricalca le sillabe" e sillabe come gioco a parte (proposte, non fatte).
