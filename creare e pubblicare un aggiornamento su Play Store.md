# GUIDA: Build e Deploy su Google Play Store (Vite + Capacitor)

Questa guida illustra i passaggi per creare una nuova versione (Release) dell'app e caricarla sul Google Play Store.

## 1. Aggiornare la Versione dell'App

Prima di compilare, devi dire ad Android che questa è una versione nuova, altrimenti Google Play la rifiuterà.

1. Apri il file `android/app/build.gradle`.
2. Trova la sezione `defaultConfig`.
3. Modifica questi due valori:
   - `versionCode`: Aumentalo di 1 rispetto al precedente (es. da `5` a `6`). È un numero intero.
   - `versionName`: Aggiornalo per gli utenti (es. da `"1.0.2"` a `"1.0.3"`).
4. Salva il file.
   _(Nota: se Google richiede un aggiornamento delle API, ricordati di aggiornare anche `compileSdkVersion` e `targetSdkVersion` nel file `android/variables.gradle`)._

## 2. Compilare e Sincronizzare

Apri il terminale del progetto ed esegui i comandi per creare la build web e passarla ad Android:

1. Crea la build di produzione:
   ```bash
   npm run build
   ```
2. Sincronizza l'applicazione su Android:
   ```bash
   npx cap sync
   ```

## 3. Generare il file Bundle (.aab) per lo Store

1. Apri Android Studio dal terminale:
   ```bash
   npx cap open android
   ```
2. Attendi in basso a destra che il "Gradle Sync" sia completato senza errori.
3. Nel menù in alto, clicca su **Build > Generate Signed Bundle / APK...**
4. Seleziona **Android App Bundle** e vai Avanti.
5. Sotto _Key store path_, assicurati che sia selezionato il tuo file Keystore (la chiave dell'app).
6. Inserisci la **Keystore password** e la **Key password** (di solito sono identiche).
7. Clicca Avanti, seleziona la variante **release** e clicca su **Create**.
8. Attendi la notifica di successo in basso a destra e clicca su **locate** per trovare il file `app-release.aab`.

## 4. Caricare su Google Play Console

1. Accedi alla [Google Play Console](https://play.google.com/console/) e seleziona la tua app.
2. Dal menù di sinistra, vai su **Rilascio > Produzione**.
3. Clicca in alto a destra su **Crea nuova release**.
4. Trascina il file `app-release.aab` nel riquadro di caricamento.
5. Inserisci le **Note di rilascio** (cosa c'è di nuovo in questo aggiornamento).
6. Clicca su **Avanti**, poi su **Salva**.
7. Infine, clicca su **Invia le modifiche per la revisione** per mandare l'app in approvazione a Google.

```

```
