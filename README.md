# SITO-V3
Il sito per compito di TPSIT

[Link sito](https://cosmin702.github.io/SITO-V3/ "Homepage")

Un semplice sito che mostra vari esempi di proprietá in CSS esterno, interno e inline

## Homepage

Nella homepage viene descritto il contenuto della pagina e per di accedere al resto degli esempi tramite la navbar.
Si puó giá notare che il mio nome e la navbar appaiono con un animazione, e che il background non é una semplice immagine ma é un svg animato.

L'animazione viene creata con @keyframes, il quale permette d'impostare certe proprietá che cambiamo in un certo periodo, in questo caso con una percentuale.

Ad esempio nel mio nome ho creato questa animazione:
```css
@keyframes comparsa {
    0% {
        transform: scale(200%);
        opacity: 0;
    }
    50%{
        transform: scale(100%);
    }
    100% {
        opacity: 1;
    }
}
```
Al inizio il testo é i doppio della sua grandezza e ha un opacitá 0, quindi non é visibile.

Al 50% dell'animazione (quindi mezzo secondo) il testo é alla sua grandezza originale.

Al 100% (1s - fine animazione) il testo é visibile.

## Navigation bar
La navbar, come detto dal nome, ci permette di navigare la interno del sito.

Questa di base é minimizzata avendo una grandezza di 5 rem (5 * 16px).

Quando passiamo il mouse sopra la navbar, essa si espande e rivela il suo contenuto, del testo che prima era nascosto.

La prima icona si anima e ruota di -180 gradi nel sito desktop e 90 gradi nel sito mobile, oltre a questo cambia anche colore, diminuendo il filtro grayscale.

![ezgif com-gif-maker (2)](https://user-images.githubusercontent.com/75899266/211056906-7a078ac7-9ea8-42a0-b7f3-05651f120ca0.gif)

Le icone interne anche cambiano colore quando si passa il mouse sopra, oltre a questo si espande e mostra un dropdown menu con tutti i link.

Ovviamente anche questo é animato ma questo volta, invece di usare i keyframe, ho usato una transition che quando appunto il mouse passa sopra l'icona o il testo affianco, i link cambiano di altezza e diventano visibili.

Transition permette di specificare la velocitá di questo passaggio e quale proprietá viene animata, facendo in modo che il testo non appaia direttamente ma la sua altezza cambi linearmente.

Come si vedeva giá nel video, il sito cambia forma in base alla grandezza della finestra, migliorando cosí l'esperienza per gli utenti mobile.

La navbar si sposta in alto e il testo si riduce in grandezza.

Questa funzione c'é in tutte le pagine, ognuna con funzioni diverse.

Tutto questo avviene con:
```css
@media only screen and (max-width: 612px) 
@media only screen and (min-width: 612px) 
```
Possiamo impostare un grandezza massima o una minima (in questo caso 612px)

Un altra cosa bella (consigliata da Alessando Porpiglia) é il cambio automatico del tema della pagina in base al tema usato sul dispositivo del utente.

Sempre con @media possiamo rilevare che tema usa l'utente e quindi cambiare colore ti tutta la pagina.
```css
@media (prefers-color-scheme: light)
@media (prefers-color-scheme: dark)
```
Il cambio del colore non sarebbe possibile senza l'assegnazione di variabili, che poi verranno usate in tutto il codice.

Questo mi permette di cambiare facilmente colore a tutto ció che c'é nel sito.

L'assegnazione avviene nel root:
```css
:root {
    --nome-variabile: valore;
 }
```
E viene usata con:
```css
background: var(--background1);
```
## Esempio 1 BORDERS

Non ce molto da commentare su questa parte perché sono solo semplici proprietà, l'unica cosa interessante é la grandezza dinamica del testo degli esempi.

Con la funzione clamp possiamo assegnare un valore minimo, uno che cambia e un valore massimo.
```css
.esempo{
    font-size: clamp(1rem, 1.8vw, 1.8rem); 
}
```
Al posto di usare i pixel ho usato rem, che é un valore relativo alla grandezza del testo impostata sul root.

In pratica 5rem sarebbero 5 * x pixel impostati.

## Esempio 2 FLOAT

Gli esempi della pagina dopo un certo valore di grandezza della pagina, stanno due per riga.

Questo perché sfruttando @media only screen e display: grid, mi permette di create una griglia con x colonne e x righe.
```css
@media only screen and (min-width: 900px){
    .esempi{
        display: inline-grid;
        grid-template-columns: auto auto;
        gap: 8%;
    }
}
```
![ezgif com-gif-maker (3)](https://user-images.githubusercontent.com/75899266/211062157-ecca00b2-e5b1-4b15-be17-f1cfe4e47cfc.gif)

## Esempio 3 ROUNDED CORNERS

Pure nel terzo esempio usiamo display grid cosí che ogni elemento viene visualizzato piú per riga.

![Immagine 2023-01-06 185200](https://user-images.githubusercontent.com/75899266/211069877-b36a863e-fa75-4f81-b299-3304b0227a9c.png)

```css
.esempi{
    display: inline-grid;
    grid-template-columns: repeat(auto-fit, 250px); 
    width: 100%;
    justify-items: center; 
}
```
Possiamo scegliere il numero di colonne, in questo caso lo impostiamo automaticamente.
Con repeat ripetiamo un pattern di colonne, con una grandezza di 250px.
