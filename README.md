# 🔐 Balioak 4.0 — Escape Room

Aula interaktiborako (horma + mahaia) diseinatutako Escape Room hibridoa (fisikoa + digitala), FP Euskadiko **Balioak 4.0** markoa (iTlent) ezagutu eta barneratzeko. CIFP Don Bosco LHII — Errenteria.

**Iraupena:** ~35-40 minutu · **Taldea:** 7-8 ikasle (talde osoa hormaren perimetroan banatuta) · **Hizkuntza:** euskara

---

## 🌐 Nola ikusi (GitHub Pages)

Repositorio hau GitHub Pages bidez argitaratuta badago, sartu hemen (`index.html` denez, ez da fitxategi-izena idatzi behar):

```
https://<zure-erabiltzailea>.github.io/<repo-izena>/
```

> Aldatu `index.html` orriaren `<head>`-eko esteka eta gainerako `href`ak ez dira aldatu behar — fitxategi guztiak **karpeta berean** egon behar dute, izenez estekatzen baitira.

> **Irudiak:** `img/` karpeta ere igo behar da (HTMLekin batera, karpeta berean). GitHub-en, bai errepositorioaren fitxategi-zerrendan bai GitHub Pages bidez irekitako orrietan, irudiak ondo ikusiko dira — path erlatiboak erabiltzen dituzte (`img/izena.jpg`), ez URL absoluturik.

## 🖥️ Nola martxan jarri aula interaktiboan (kiosk moduan)

1. Ireki **Chrome** edo **Edge** hormako/mahaiko ordenagailuan (multitouch ondo onartzen dute).
2. Kiosk moduan abiarazteko (gomendatuena, ikasleek nabigatzaile-barra ez ikusteko):
   ```
   chrome.exe --kiosk --touch-events "https://<zure-erabiltzailea>.github.io/<repo-izena>/"
   ```
   Edo lokalki badago: `--kiosk --touch-events "C:\bidea\index.html"`
3. Egiaztatu **multitouch-a** funtzionatzen duela: ireki Gela 1 eta probatu bi hatzekin (edo bi pertsonarekin) aldi berean ukitzen bi bola desagertzen direla.
4. Sarrera-bideoak (hub-ean) **internet konexioa** behar du (YouTube). Konexiorik ez badago, ordeztu `index.html`-eko `<iframe>` bideo lokal batekin.

## 📁 Egitura

| Fitxategia | Deskribapena |
|---|---|
| `index.html` | Gida nagusia (urratsez urrats): sarrera-bideoa, 4 gelen bidalketa (kokapenekin), azken kandadua |
| `balioak-gela1-solidaritatea.html` | Gela 1 — Solidaritatea (Taldeka jolasa, 8 postu) |
| `balioak-gela2-inklusioa.html` | Gela 2 — Inklusioa (Marraztu jolasa, 8 postu paralelo) |
| `balioak-gela3-ekimena.html` | Gela 3 — Ekimena (2 robot-labirinto paralelo) |
| `balioak-gela4-interdependentzia.html` | Gela 4 — Interdependentzia (Arrastatu jolasa, multitouch benetakoa) |
| `balioak-4-0-escape-room.html` | Diseinu-orria: azalpena, gelen xehetasunak, antolaketa eta grabaketarako gidoia |
| `img/` | iTlent-en Balioak 4.0 liburuxkatik ateratako irudiak (ikus beheko oharra) |

## 🎮 Nola funtzionatzen du

1. Irakasleak `index.html` irekitzen du — **urratsez urrats gida** da: sarrera-bideoa, gero gela bakoitza banan-banan.
2. Urrats bakoitzean, hub-ak esaten du **nora bidali taldea** (horma nagusia, mahai interaktiboa...) eta "Ireki Gela X" botoia dauka.
3. Gela bakoitzean, taldeak **4 proba** gainditu behar ditu, hurrenkeran:
   1. **🔍 Bilaketa** — galdera bat, erantzuna PDFan edo Interneten bilatuz.
   2. **🔧 Kode fisikoa** — irakasleak gelan prestatutako ariketa fisiko bat (giltzarrapoa, Braillea, zubia, giltza bikoitza...); kode bat sartu behar da webgunean aurrera egiteko.
   3. **📝 Galderak** — 6tik 3 zuzen erantzun behar dira.
   4. **✋ Jolas digitala** — hormaren/mahaiaren perimetro osoa erabiltzen duen jokoa, multitouch benetakoarekin.
4. Jolasa gaindituta, gela bakoitzak **digitu bat** ematen du.
5. Irakasleak hub-era itzuli eta "Hurrengo gelara" sakatzen du, hurrengo taldea/kokapena bidaltzeko.
6. Azkenik, 4 digituak azken kandaduan sartu → kutxa nagusia irekitzen da. Ez dago hausnarketa-atalik inon; dena proba objektiboak dira, benetako eszape room baten moduan.

## ⚙️ Konfigurazioa (irakaslearentzat)

**Digitalak (kodeak).** Gela bakoitzaren kodea (`CODE` aldagaia, JS-aren hasieran) hub-eko `CODES` zerrendarekin bat etorri behar da:

```js
// index.html
const CODES = ['4','8','1','6']; // Solidaritatea, Inklusioa, Ekimena, Interdependentzia
```

**Fisikoak (kode fisikoak).** Gela bakoitzeko fitxategian `PHYSICAL_CODE` aldagai bat dago — irakasleak gelan jarritako ariketa fisikoarekin (giltzarrapo, Braille txartel, zubi...) bat etorri behar du:

```js
// adibidez balioak-gela1-solidaritatea.html
const PHYSICAL_CODE='SOL4';
```

Balio lehenetsiak: Gela 1 `SOL4`, Gela 2 `INK2`, Gela 3 `EKI3`, Gela 4 `INTER4`. Aldatu nahi badituzu, aldatu fitxategi bakoitzean.

**Gelen arteko sekuentzia (blokeoa).** Gela 2, 3 eta 4k **sarrera-ate** bat dute: ezin da gela horiek ireki (galderarik ere ikusi gabe) aurreko gelaren kodea sartu gabe. Gela 1ek ez du atea, hasierako gela baita. Hau `PREV_CODE` aldagaian dago ezarrita gela bakoitzaren fitxategian:

```js
// adibidez balioak-gela2-inklusioa.html
const PREV_CODE='4'; // Gela 1eko kodea
```

Horrek taldea benetan behartzen du ordena errespetatzera: ezin dute Gela 3 zuzenean ireki Gela 1 eta 2 egin gabe, nahiz eta URLa ezagutu.

**Kokapenak.** Hub-eko `LOCATIONS` objektuan ezarri gela bakoitza non dagoen (horma, mahai...):

```js
// index.html
const LOCATIONS = {
  1: '📍 Horma nagusia — ezkerreko panela',
  2: '📍 Mahai interaktiboa',
  3: '📍 Horma nagusia — eskuineko panela',
  4: '📍 Mahai interaktiboa (4 bikote, 8 postu)'
};
```

Kodeak aldatu nahi badituzu, aldatu **bi lekuetan**: gela bakoitzeko `CODE` aldagaian eta hub-eko `CODES` zerrendan, ordena berean.

## 📚 Iturria

Edukia iTlent-en (LHko Talentuaren Euskal Institutua) **"Balioak 4.0"** liburuxka ofizialean oinarritua dago: itlent.eus.

`img/` karpetako irudiak liburuxka horretatik atera dira (barne erabilerarako, FP Euskadiko sarearen baitan). Garapen Iraunkorrerako 17 Helburuen grafikoa NBEren material ofiziala da, liburuxkan bertan agertzen den bezala.

---

*ETHAZI · AA Lantaldea · CIFP Don Bosco LHII*
