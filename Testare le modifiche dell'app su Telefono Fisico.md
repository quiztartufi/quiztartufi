# GUIDA: Testare le modifiche dell'App su Telefono Fisico

Segui questi passaggi ogni volta che modifichi il codice dell'app (HTML/JS/CSS su Vite) e vuoi testare il risultato nativo sul tuo telefono fisico tramite Android Studio.

## 1. Preparare il Telefono

1. Collega il tuo telefono Android al PC tramite cavo USB.
2. Assicurati di aver attivato le **Opzioni Sviluppatore** sul telefono (si attivano toccando 7 volte il "Numero build" nelle Info del telefono).
3. Nelle Opzioni Sviluppatore, assicurati che il **Debug USB** sia ATTIVO.
4. Quando colleghi il cavo, se il telefono ti chiede "Consenti debug USB da questo computer?", metti la spunta su "Sì/Consenti".

## 2. Compilare le modifiche del codice

Visto che usi Capacitor, il codice nativo Android non vede in automatico le modifiche fatte su Vite. Devi ricompilarle.
Apri il terminale ed esegui:

1. Aggiorna la build del codice:
   ```bash
   npm run build
   ```
2. Trasferisci i nuovi file alla cartella Android:
   ```bash
   npx cap sync
   ```

## 3. Avviare l'app sul telefono da Android Studio

1. Apri Android Studio tramite il terminale:
   ```bash
   npx cap open android
   ```
2. Attendi che il caricamento di Gradle (in basso a destra) sia terminato.
3. Guarda nella barra degli strumenti in alto (vicino all'icona del martello verde). Vedrai un menù a tendina con i dispositivi.
4. Clicca sul menù a tendina: dovresti vedere **il nome del tuo telefono fisico** (es. _Samsung SM-G998B_). Selezionalo.
5. Clicca sul pulsante **Play (Run 'app')** a forma di triangolo verde (o premi `Shift + F10`).
6. Attendi che Android Studio compili l'app. Al termine, l'app si aprirà automaticamente sullo schermo del tuo telefono!

_Suggerimento: Per visualizzare eventuali errori o i tuoi `console.log()` mentre l'app gira sul telefono, apri la scheda **Logcat** in basso su Android Studio._
