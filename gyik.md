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

## Melyik ciklus mikor hasznos?

> Egyet hátralépve: Milyen ciklusok vannak?

### for

> Valamilyen számtól valamilyen számig fut, mi határozzuk meg a léptéket.
>
> Futtathatjuk mondjuk 1-től 10-ig, egyesével növekedve léptetve: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10
>
> Lehet csökkenő is a számsorunk 10-től 0-ig is kettesével.

```js
// ciklus 1-től, 10-ig, egyesével
// for ( mettől; meddig; mekkora léptékkel)
for (let index = 1; index <= 10; index++) {
    console.log(index);
}
```

```js
// ciklus 10-től, 0-ig, 2-esével
for (let index = 10; index >= 0; index = index - 2) {
    console.log(index);
}
```

### for..in

> Tömb elemein vagy objektum kulcsain szaladhatunk végig vele.

```js
// ciklus egy tömbben
// for (léptetőVáltozó in tömb)
for (index in [1, 2, 3, 4, 5]) {
    console.log(index);
}
```

```js
// ciklus egy objektumban
// for (kulcsLéptetőVáltozó in objektum)
const userProfile = {
    name: 'John Doe',
    email: 'john.doe@gmail.com',
    age: 34,
    job: 'Developer'
};
for (let key in userProfile) {
    console.log(key + ':', userProfile[key]);
}
```

### while

> Addig fut, amíg a megadott feltétel igaz. Anno előltesztelő ciklusként tanultam.
>
> Az előltesztelő annyit jelent, hogy az előtt vizsgálja meg a feltételt, hogy lefuttatná a benne leírt kódot.

```js
let counter = 0;
// 1-től futunk 10-ig, egyesével növelve
while (counter <= 10) {
    console.log(counter);
    counter++;
}
```

```js
// megkereshetünk vele elemet egy tömbben
let index = 0; // tömb indexelés 0-val kezdődik
const items = [1, 2, 4, 2, 1, 3, 5, 1, 2, 3, 6];
const searchFor = 3;
while (index <= items.length && items[index] !== searchFor) {
    index++;
}

if (index > items.length) {
    console.log('Nem találtuk meg az elemet');
} else {
    console.log('Megtaláltuk az elemet, az ' + index + '. helyen');
}
```

### do..while

> Hátultesztelő ciklus. Azaz a ciklusmagot követi a feltétel vizsgálata. Tehát egyszer biztosan lefut.

```js
let counter = 0;
// 1-től futunk 10-ig, egyesével növelve
do {
    console.log(counter);
    counter++;
} while (counter <= 10);
```

### Melyiket mikor használjuk?

> Ezt teljes mértékben a feladat határozza meg. 
> * Van amikor nem szükséges indexelni, de végig kell szaladni minden elemen. Olyankor jól járahtunk egy for..in-nel. 
> * Van amikor nem léphetünk be a ciklusba, ha nem teljesül egy feltétel. Olyankor jó az előltesztelő.
> * Van amikor be kell lépnünk a ciklusba, de ha a feltétel nem teljesül, akkor csak egyszer kell lefuttatnunk. Ilyenkor hasznos a hátultesztelő.

---

## Functiont mindig muszáj kiírni? Ha nem, akkor mikor nem?

> folyamatban

---

## Mire jó az esemény?

> folyamatban

---
