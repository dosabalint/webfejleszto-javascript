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
>
> -   Van amikor nem szükséges indexelni, de végig kell szaladni minden elemen. Olyankor jól járahtunk egy for..in-nel.
> -   Van amikor nem léphetünk be a ciklusba, ha nem teljesül egy feltétel. Olyankor jó az előltesztelő.
> -   Van amikor be kell lépnünk a ciklusba, de ha a feltétel nem teljesül, akkor csak egyszer kell lefuttatnunk. Ilyenkor hasznos a hátultesztelő.

---

## Functiont mindig muszáj kiírni? Ha nem, akkor mikor nem?

> Többféleképp adhatunk meg függvényt

> Egyik általános fomája az alábbi. Ekkor van neki saját neve, ami alapján meghívhatjuk. Van neki továbbá saját scope-ja, ami alatt értendő, hogy saját this értéke van.

```js
// név szerint hívható függvény
function osszead(parameter1, parameter2) {
    return parameter1 + parameter2;
}
console.log(osszead(1, 2));
```

> Másik lehetőség, hogy anonim függvényt csinálunk belőle. Ez hasznos lehet egy mondjuk egy mappelésnél, ha nem akarjuk külön névvel ellátni. Másik lehetőség anonim függvényre, hogy nyíl függvényként adjuk meg. Ekkor azonban nem rendelkezik majd saját this-sel, azaz nem lesz scope-ja.

> Az alábbi példában a this-t nem használjuk, de akadnak olyan esetek, ahol ez jelentős különbség a kettő között.

```js
// anonim függvény saját scoppal
const tomb = [1, 2, 3];
console.log(
    tomb.map(function(elem) {
        return elem * elem;
    })
);
```

```js
// arrow függvény scope nélkül
const tomb = [1, 2, 3];
console.log(
    tomb.map(elem => {
        return elem * elem;
    })
);
```

---

## Mire jó az esemény?

> Az eseményeket úgy kell elképzelni, mint a kisgyermek ordítását, amivel azt jelzi, hogy valami nincs rendben. Ha nem a hétköznapi szemüvegünkkel nézzük a gyermek-ordítás-anya kontextust, akkor van két szereplőnk (gyermek, anya) és egy eseményünk (ordítás). A két szereplő nincsen összekötve fix pontok mentén, külön szereplőként látjuk őket magunk előtt. Ám ha a gyermek eltüzeli az ordítás eseményt, akkor erre az anyuka fel van iratkozva és reagál valamilyen cselekvéssel.
>
> Ha visszatérünk a webfejlesztéshez, akkor egy gombnak mint szereplőnek is vannak eseményei, például a click. Ezzel jelzi nekünk, hogy kattintottak rá egyet. Egy ilyen kattintásra reagálhatunk egy másik szereplővel, aki erre az eseményre feliratkozott. Például elküldheti egy szerver felé a formban összegyűjtött adatokat és jelezhet a felhasználónak, hogy sikeres vagy sikertelen volt a művelet.
>
> Az eseményeket tehát úgy vegyük mint kapcsolati pontokat szereplők között, amik mentén reagálni tudunk bizonyos történésekre. Ilyen történéseket hozhatunk létre mi is, de reagálhatunk már kész történésekre is. Ezek viszont nem úgy történnek, mint a fix függvényhívások, hanem sokkal kötetlenebb a kapcsolat a szereplők között.

```html
<button id="azEnGombom">0 kattintás</button>

<script>
    // elem kikeresése
    let gombElem = document.getElementById('azEnGombom');
    
    // számláló induló érték beállítása
    let szamlalo = 0;
    
    // eseményre feliratkozás
    gombElem.addEventListener('click', function (){
        szamlalo++;
        this.innerText = szamlalo + ' kattintás';
    });
</script>
```

---
