# Lente

**L'iPhone diventa la webcam del PC.** Video in 1080p a 60 fps con filtri in tempo reale. Funziona con Safari e OBS: niente app da installare, niente da pagare.

👉 **Apri Lente: [haiikuu.github.io/Lente](https://haiikuu.github.io/Lente/)**

---

## Cosa fa

- **1080p a 60 fps.** L'iPhone codifica il video in H.264 con il suo chip, senza scaldare.
- **Dieci filtri:** Originale, Vivido, Caldo, Freddo, Cinema, Pastello, Vintage, B/N, Noir, Seppia.
- **Regolazioni dal telefono:** luminosità, contrasto, saturazione, temperatura, nitidezza, pelle liscia, vignettatura, grana, zoom, specchio, rotazione e torcia. Il PC si aggiorna mentre muovi il dito.
- **Diagnosi in diretta.** Sotto l'anteprima, l'iPhone ti dice cosa sta peggiorando l'immagine (luce, Wi‑Fi, orientamento, OBS) e come rimediare.
- **Si ricollega da solo** se la connessione cade o ricarichi la pagina.

## Cosa serve

- Un iPhone con Safari
- Un PC con [OBS Studio](https://obsproject.com) (gratuito)
- iPhone e PC sulla stessa rete Wi‑Fi

## Come si usa

1. **Aggiungi Lente a OBS.** Apri [la pagina di Lente](https://haiikuu.github.io/Lente/) sul PC e copia l'indirizzo del tuo collegamento. In OBS, nel riquadro *Fonti*, premi **+** › **Browser** e incollalo. Imposta larghezza 1920, altezza 1080 e frequenza fotogrammi personalizzata 60. In OBS compare un codice QR.
2. **Collega l'iPhone.** Apri la Fotocamera dell'iPhone e inquadra il QR. Si apre Safari: premi **Avvia la fotocamera**.
3. **Usala come webcam.** In OBS premi **Avvia fotocamera virtuale**. In Discord, Zoom, Meet o Teams scegli la fotocamera **OBS Virtual Camera**.

Per avere 60 fps imposta anche *OBS › Impostazioni › Video › FPS* a 60.

## Per un'immagine nitida e fluida

- **Tieni l'iPhone in orizzontale.** In verticale l'immagine viene tagliata e ingrandita.
- **Usa la fotocamera posteriore** (tasto *Cambia*): è la più nitida.
- **Più luce = più fluido.** Con poca luce iOS scende da solo a 30 fps. Disattiva anche *Risparmio energetico*.
- **Wi‑Fi a 5 GHz**, con l'iPhone vicino al router. Se puoi, collega il PC al router col cavo.
- **In OBS** lascia attiva *Impostazioni › Avanzate › Accelerazione hardware della sorgente browser*.

## Se qualcosa non va

| Problema | Soluzione |
| --- | --- |
| L'iPhone dice «PC non trovato» | OBS deve essere aperto con la sorgente Browser di Lente, e il QR deve essere quello del tuo codice. |
| Il video si blocca | Tieni Safari in primo piano e lo schermo acceso: in standby iOS mette in pausa la fotocamera. |
| In OBS vedo la versione vecchia | Doppio clic sulla sorgente Browser › **Aggiorna la cache della pagina corrente**. |
| Il video passa «via internet» | iPhone e PC non sono sulla stessa rete (attenzione alle reti «Ospiti»). |

## Come funziona

Lente è una sola pagina web (`index.html`) che fa tre cose diverse in base all'indirizzo:

- **Sul PC** mostra le istruzioni e il tuo collegamento.
- **Sull'iPhone** (`?cam=CODICE`) apre la fotocamera e invia il video.
- **In OBS** (`?rx=CODICE`) riceve il video e lo disegna con i filtri usando la scheda video (WebGL).

Il video viaggia dall'iPhone al PC con **WebRTC**, direttamente sulla tua rete Wi‑Fi. Il server gratuito di [PeerJS](https://peerjs.com) serve solo a far trovare i due dispositivi all'inizio, e non vede il video.

## Limiti

- Niente audio: per la voce usa il microfono del PC.
- Safari deve restare aperto con lo schermo acceso.
- Il collegamento avviene via Wi‑Fi. Il cavo USB serve solo a caricare l'iPhone.
