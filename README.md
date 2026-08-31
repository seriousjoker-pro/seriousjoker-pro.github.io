# EquaVoce — calendario editoriale "E voi... lo sapevate?"

Dashboard locale per pianificare una rubrica musicale/editoriale di EquaVoce: per ogni slot
editoriale associa una canzone, un taglio tematico, una lettura e i materiali di pubblicazione.
È un progetto autonomo e non dipende dalla pipeline MKC/VaultForge/AgentePM.

## Stato e uso previsto

Il percorso quotidiano è aprire `EquaVoce_calendario_editoriale.html` nel browser tramite
`file://`. Non richiede server, build, npm o Python. La dashboard è la modalità supportata per
aggiungere canzoni, assegnare date, modificare dettagli e generare i materiali editoriali.

## Componenti principali

| File/cartella | Ruolo |
|---|---|
| `EquaVoce_calendario_editoriale.html` | Dashboard statica: interfaccia, logica e dati iniziali incorporati. |
| `equavoce_dati_calendario.json` | Fonte dati da usare fuori dalla dashboard o tramite salvataggio su file reale. |
| `EquaVoce_bozze_post.md` | Archivio cronologico di bozze e post. |
| `copertine/` | Copertine generate. |
| `spotify_codes/` | PNG dei codici Spotify associati ai brani. |
| `README_spotify_code.md` | Procedura e formato per i codici Spotify. |
| `genera_copertina.py` | Generatore Pillow di riserva; la dashboard resta il percorso principale. |

## Flusso editoriale

1. Apri la dashboard e aggiungi/modifica una canzone attraverso i form, non editando il JSON a
   mano.
2. Assegna o sposta il brano nel calendario con drag-and-drop; lo stato editoriale e gli eventi
   seguono il brano.
3. Completa il testo/post e conserva lo storico in `EquaVoce_bozze_post.md`.
4. Seleziona o scarica il codice Spotify e genera la copertina dalla dashboard.
5. Esporta periodicamente il backup JSON dalla dashboard prima di interventi manuali importanti.

## Persistenza e recupero

La dashboard conserva lo stato in `localStorage` e, quando autorizzata, usa la File System Access
API per salvare sul file dati reale. L'export/import JSON è il meccanismo di recupero previsto.
Poiché il progetto ha avuto in passato corruzioni causate da editing testuale automatico, JSON e
HTML non devono essere modificati con comandi non strutturati o da agenti LLM per operazioni
editoriali di routine.

## Limiti e sicurezza

- Il download automatico dei codici Spotify può essere bloccato da CORS o da una rete limitata;
  il browser dell'utente resta il percorso di fallback.
- Le copie `EquaVoce_*` storiche sono conservate in `C:\Code\Archivio\DEI-root-copies` e non
  sono la fonte di verità rispetto a questa cartella.
- Prima della pubblicazione GitHub, rivedere bozze, cover e codici Spotify per contenuti che non
  devono essere distribuiti.

## Ripresa del progetto

`CLAUDE.md` descrive nel dettaglio architettura, persistenza, vincoli e problemi storici. Leggilo
prima di qualunque intervento tecnico sulla dashboard.
