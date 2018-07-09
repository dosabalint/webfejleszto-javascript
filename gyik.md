# Gyakran Ismételt kérdések

## GetElementById-t mikor es hogyan kell alkalmazni?

**Mit csinál?**

> Megadunk neki egy paramétert (a HTML elem azonosítóját (továbbiakban ID)), majd ő megkeresi és visszaadja nekünk az elemet.

**Mikor alkalmazzuk?**

> Ha ID szerint szeretnénk megtalálni egy elemet és azon valamit végrehajtani.

**Példa**

```html
<button id="azEnGombom">Loading...</button>

<script>
    let gombElem = document.getElementById('azEnGombom');
    console.log('gombElem:', gombElem);
</script>
```

**Másik példa**

> Ha módosítani szeretnénk a gombnak a szövegét, akkor azt például így tehetjük meg.

```html
<button id="azEnGombom">Loading...</button>

<script>
    // elem összeszedése
    let gombElem = document.getElementById('azEnGombom');
    console.log(
        'gombElem:',
        gombElem
    );

    // elem szövegének kiírása
    console.log(
        'gombElem szövege:',
        gombElem.innerText
    );

    // szöveg módosítása
    gombElem.innerText = 'Beküldés';

    // a módosított szöveg
    console.log(
        'gombElem új szövege:',
        gombElem.innerText
    );
</script>
```

---

## Melyik ciklus mikor jó?

> Egyet hátralépve: Milyen ciklusok vannak?

### for

> Valamilyen számtól valamilyen számig fut, mi határozzuk meg a léptéket.
>
> Futtathatjuk mondjuk 1-től 10-ig, egyesével léptetve: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10
>
> Lehet fordítva 10-től 1-ig is egyesével.

```html
<script>
    // ciklus 1-től, 10-ig, egyesével
    // for ( mettől; meddig; mekkora léptékkel)
    for ( let index = 1; index <= 10; index++ ) {
        console.log(index);
    }
</script>
```

```html
<script>
    // ciklus 10-től, 0-ig, 2-esével
    for ( let index = 10; index >= 0; index = index - 2 ) {
        console.log(index);
    }
</script>
```

### for..in ciklus

> folyamatban

### for..in ciklus

> folyamatban

### for..in ciklus

> folyamatban

---

## Melyik ciklus mikor hasznos?

> folyamatban

---

## Functiont mindig muszáj kiírni? Ha nem, akkor mikor nem?

> folyamatban

---

## Mire jó az esemény?

> folyamatban

---
