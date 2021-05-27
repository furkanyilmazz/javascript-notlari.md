# Table Of Contents

> İçerik Tablosu

- [Kurs Notları](#kurs-notlari)
  1. [Bölüm 1](#bolum-1)
  2. [Bölüm 2](#bolum-2)
  3. [Bölüm 3](#bolum-3)
  4. [Bölüm 4](#bolum-4)
  5. [Bölüm 5](#bolum-5)
  6. [Bölüm 6](#bolum-6)
  7. [Bölüm 7](#bolum-7)
- [ES6 Notları](#ecmascript-6)
  1. [Arrow Functions](#Arrow-Functions)
  2. [Property destructing](#Property-destructing)
  3. [Template literals](#Template-literals)
  4. [Rest/Spread operators](#Rest-Spread-operators)
     - [Spread](#SPREAD)
     - [Rest](#REST)
  5. [Property-value shorthand notation](#Property-value-shorthand-notation)
- [Clean Coding in JavaScript](#clean-coding-in-javascript)

# KURS NOTLARI

## BOLUM-1

### JAVASCRİPT NEDİR?

basit html ile oluşturulmuş bir sayfanın kullanıcı ile etkileşime girmesini sağlamak için oluşturulmuş bir yazlım dilidir.

**[Başa Git](#table-of-contents)**

## BOLUM-2

> (Yazım standardı ile ilgili bölüm)

- ASI = Automatic semicolon ınsertion.
- ASI sıkıntılar çıkarabilir noktalı virgül koyarak kodlamak daha sağlıklı.

---

- the one true brace style şeklinde yazmaya dikkat edilmeli.(süslü parantezlerin yeri ile ilgili unutursam google)

---

- `` ile multiline string yazabilirsin

---

değişken alma
`` javascript `bbbb bb ${degisken} bbb` , "bbbb bb "+degisken" bbb"  ``

---

- Indentation (Giirintileme): okunaklı kod yazmak adına tab vermenin terim adı. (JavaScript 2 space kullanır)

---

- geçici değişkenlerin başına alt tire konur (\_i,\_kullanıcıID,...)

**[Başa Git](#table-of-contents)**

## BOLUM-3

> (JavaScript'in Temelleri)

sayi --;
-- sayi;
ikisi de bir azaltır ama aralarındaki fark

```javascript
sayi = 20;
yeniSayi = sayi--;
sayi = 19;
yeniSayi = 20;
```

olurken

```javascript
sayi = 20;
yeniSayi = --sayi;
sayi = 19;
yeniSayi = 19;
olur;
```

---

```javascript
if (true && true) {
  console.log("Doğru");
} else {
  console.log("Yanlış");
}

// Ternary

console.log(true && true ? "Doğru" : "Yanlış");
```

ikisi de aynı şey

---

- recursive = kendi kendini çağıran fonksiyonların temel adı.

---

### RegularExpressions (Regex)

```javascript
/*
'+90 555 300 8080'

'35 KRL 2000'

telefon = 'Ülke Kodu (+ ile başlar) + Operatör Kodu 3 haneli sayı (5 ile başlar) + 3 haneli sayı + 2 haneli sayı + 2 haneli sayı'

plaka = 'sehir kodu (2 rakamlı sayi) + 1, 2 ya da 3 harf + 2 ile 4 rakam arasında bir sayı'
*/

telefon = /((\+|00)(\d{1,3})|0)\s?(\d{3})\s?(\d{3})\s?(\d{2})\s?(\d{2})/ //şeklinde olur

/((\+|00)(\d{1,3})|0)\s?(\d{3})\s?(\d{3})\s?(\d{2})\s?(\d{2})/.test('+90 555 300 8080') //regex testi bu şekilde yapılır

"Merhaba Telefonum +90 555 300 8080".replace(/((\+|00)(\d{1,3})|0)\s?(\d{3})\s?(\d{3})\s?(\d{2})\s?(\d{2})/, '***')//verilen text içinde regex e uyan numarayı bulup *** ile değiştirir

"Merhaba Telefonum +90 555 300 8080".match(/((\+|00)(\d{1,3})|0)\s?(\d{3})\s?(\d{3})\s?(\d{2})\s?(\d{2})/)

plaka = /(\d{2})\s?([A-Z]{1,3})\s?(\d{2,4})/

/\d/ = /[0-9]/
/\D/ = /[^0-9]/
/\w/ = /[A-Z]/
/\W/ = /[^A-Z]/
/\s/ = boşluk

/\d{1,}/ = /\d+/
/\d{0,}/ = /\d*/

[abc] = a veya b veya c ... = (a|b|c)

[0-9], [0-9a-c],
```

**[Başa Git](#table-of-contents)**

## BOLUM-4

> (JavaScript ve OOP)

[değişkenlerin özel fonksiyonları ile ilgili videodaki kaynak](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---

```javascript
function topla() {
  var sayilar = Array.from(arguments);
  return sayilar.reduce(function (x, y) { return x + y; }, 0);

var sonuc = topla(2, 3, 4);
var sonuc2 = topla(2, 3, 4, 10, 20);
```

```javascript
function topla(x) {
  return function (y) {
    return function (z) {
      return x + y + z;
    };
  };
}

const topla = (x) => (y) => (z) => x + y + z;
```

fonksiyon dönen fonksiyonlar yukarıdaki iki örnek aynı işlevi yerine getirir

---

### Eski JavaScript ile class tanımı

```javascript
function Insan(name, surname, age) {
  var x = 10; // private
  var y = function () {
    // private
    console.log("Merhaba arkadaşlar" + x);
  };
  return {
    name: name,
    surname: surname,
    age: age,
    speak: function () {
      y();
      console.log("Merhaba arkadaşlar" + x);
    },
  };
}

var fatih = new Insan("fatih", "akin", 28);
```

---

- JavaScript function scope a sahip bir dildir bu da bir fonksiyon içinde tanımladığınız bir değişkenin o fonksiyon içinde scope olması anlamına gelir

1. var = variable kısaltması üst üste değişebilen bir değişken (global scope)
2. let = bu da üst üste değişebilen bir değişken ama yazıldığı scope içerisinde kalır (block scope)
3. const = bir kere tanımlanır değiştirilemez değişken tanımı

- let ve const değişkenleri ES6 ile gelmekte

---

### JavaScriptte değişkenler ve fonksiyonlar yukarıya hoist edilir peki hoist nedir?

```javascript
// HOISTING

(function () {
  var a = 1;
  console.log(b);
  var b = function () {
    return 1;
  };
})()(
  // aslında böyle çalışır:

  function () {
    var a, b;
    console.log(b);
    b = function () {
      return 1;
    };
  }
)()(
  //////////////////////

  function () {
    var a = 1;
    console.log(b);
    function b() {
      return 1;
    }
  }
)()(
  // aslında böyle çalışır:
  function () {
    var a = 1;
    function b() {
      return 1;
    }
    console.log(b);
  }
)()(
  ////////////////////////

  function () {
    return b();

    function b() {
      return 1;
    }
  }
)()(
  // aslında böyle çalışır:

  function () {
    function b() {
      return 1;
    }
    return b();
  }
)()(
  ///////////////////////

  function () {
    return b();

    var b = function () {
      return 1;
    };
  }
)()(
  // aslında böyle çalışır:

  function () {
    var b;
    return b();

    b = function () {
      return 1;
    };
  }
)();
```

---

### CONTEXT VE THİS

bir fonksiyonun bağlı olduğu obje onun contextidir ve bir fonksiyon contextine this ile ulaşır.

```javascript
var fatih = {
  name: "fatih",
  surname: "akin",
  fullname: function () {
    return this.name + " " + this.surname;
  },
};
```

- contexti değiştiren üç adet fonksiyon vardır bunlar(context switching)

1. .bind : bağla
2. .call : çağır
3. .apply : çağır, parametreler dizi olarak.

```javascript
// Klasik
var fatih = {
  name: "fatih",
  surname: "akin",
  fullname: function () {
    var that = this;
    function b() {
      return that.name;
    }
    return b() + " " + this.surname;
  },
};

// ES5
var fatih = {
  name: "fatih",
  surname: "akin",
  fullname: function () {
    function b() {
      return this.name;
    }
    return b.call(this) + " " + this.surname;
  },
};

// ES6
var fatih = {
  name: "fatih",
  surname: "akin",
  fullname: function () {
    const b = () => this.name;
    return b() + " " + this.surname;
  },
};
```

ES6 için bulunan örnekte arrow function kullanılmıştır ES6 ile eklenen arrow functionların kendi contexti yoktur bir üst objenin contextini kullanırlar.

---

```javascript
// ES6 Kalıtım örneği

class Insan {
  constructor() {}
  konus() {}
  yurur() {
    console.log("yuru");
  }
}

class Ogretmen extends Insan {
  constructor() {
    super();
  }
  dersver() {}
  yurur() {
    super.yurur();
    console.log("sinifta gez");
  }
}

// Prototip tabanlı

function Insan() {}

Insan.prototype.konus = function () {};

Insan.prototype.yurur = function () {
  console.log("yuru");
};

function Ogretmen() {}

Ogretmen.prototype = Object.create(Insan.prototype);
Ogretmen.prototype.constructor = Ogretmen;
Ogretmen.prototype.super = function () {
  return this.__proto__.__proto__;
};

Ogretmen.prototype.yurur = function () {
  this.super().yurur();
  console.log("sinifta gez");
};
```

**[Başa Git](#table-of-contents)**

## BOLUM-5

> (Tarayıcıda JavaScript)

- DOM = Document Object Model

- window nesnesi = o anda açık olan tarayıcı penceresinin en genel (evrensel) objesidir.

- element = dom üzerinde oluşturulan her açılış kapanış tagi bulunan blocklara element denir javascript ile sayfaya element eklenip düzenlenebilir (lazım olursa GOOGLE=>js elements)

- event = olay anlamına gelen sözcük javascript te kullanıcı ile iletişime geçen elementlere kabiliyet kazandırmayı sağlar.

```javascript
//EVENT

var btn = document.getElementById("btn");

btn.addEventListener("click", function () {
  alert(1);
});
```

[Bütün eventlerin bulunduğu bir doküman](https://developer.mozilla.org/en-US/docs/Web/Events)

---

### DEVELOPER TOOLS

taryacıda geliştirme yapılan veya hazırda açık olan bir siteye sağ tıklayıp inspect seçildiği zaman developer tool açılır.

en başta html ve css style kodlarının bulunduğu element bulunur burada html kodu üzerinde istediğimiz elemente sağ tıklayarak açılan menüde bulunan özelliklerini anlık olarak değiştirebiliriz bu değişiklikler kalıcı olmaz.
element tabında herhangi bir elemente sağ tıklayarak debug işlemlerinde kullanılan breakpoint atayabilirsin.
html kodunun yanında açılan kısımdan styles bölümünü seçerek yine sayfanın css kodları ile anlık olarak değişiklik yapıp nasıl göründüğünü sınayabiliriz bu değişiklikler kalıcı olmaz.

console tab, bir javascript konsoludur javascript kodlarını çalıştıran bir konsoldur her tarayıcıda bulunur.

sources kısmı sitenin bütün dosyalarına erişiliebilen bir kısımdır debug işlemlerinin büyük bir çoğunluğu bu tab da yapılır.

---

### local storage ve cookies

local storage her sayfanın sahip olduğu bir depolama alanı gibi düşünülebilir string değerler tutar istersek json formatında verileri stringfy ederek daha sonrasında parse ederek bu alanda tutabiliriz cookielere göre daha yeni bir yapıdır.
cookies local storage ile çok benzer bir şekilde sitenin ön yüzünde veri tutmaya yarar local storage a göre çok daha kısıtlı ve kullanması daha zordur.
bunlara developer tools da bulunan application altında local storage ve cookies i görebiliriz.

---

### AJAX

AJAX = Asynchronous JavaScript and XML
Eğer HTML veriyi göstermek için tasarlandıysa, XML veriyi kapsamak ve taşımak için tasarlanmıştır.
Hem JavaScript, hem de XML AJAX’da eşzamanlı olmadan çalışır. Sonuç olarak, AJAX kullanan herhangi bir web uygulaması tüm sayfayı yenileme ihtiyacı olmadan veri yollayabilir ve alabilir.

**[Başa Git](#table-of-contents)**

## BOLUM-6

> (İşletim sisteminde JavaScript)

### NodeJs

Node en basit hali ile tarayıcıda bulunan javascript motorunun işletim sistemi üzerinde çalışan versiyonudur.
herhangi bir javascript kodunu terminal üzerinden **node dosyaismi.js** şeklinde çağırarak çalıştırabilirsin.
başka bir dosyadan **require('./dosyaismi.js')** şeklinde kodu çağırabiliriz.

```javascript
//Değişkene require etme

//main.js

var x = require("./data.js");
console.log(x.toUpperCase());

//data.js

module.exports = "cengo";
```

burada module.exports yapısı istenen çıktıyı main.js'de değişkene atadığımız için return gibi işlev görür.
toUpperCase() fonksiyonu sayesinde mesajı cengo olarak değil CENGO olarak bastırır.

---

### NVM

NVM = Node Version Manager
farklı dosyalarda farklı projelerde farklı node sürümünü kullanmayı sağlar ihtiyaç olursa GOOGLE

---

### NPM

NPM = Node Packager Manager
hazır paketlerin paylaşıldığı platform
npm paketi kurmadan önce mevcut projede **npm init** yapıp o proje için tutulacak olan bilgilerin ve paketlerin bulunduğu json dosyasını oluştur.
ardından **npm install paketismi** ile kurulumu gerçekleştirip kullanmaya başlayabilirsin.

---

### ES6

ES6 = EcmaScript 6
Yeni js yazılım yapısıdır. JavaScriptin gelecekteki hali

### BABEL

ES6 yapısını desteklenmeyen tarayıcılarda çalışması için düzenleyen bir çeviricidir.
**npm install babel-cli** ile projeye kurulabilir zaman içerisinde değişmiş olabilir güncell kurulumu => GOOGLE

---

### Lint

lint yazdığınız kod içerisinde bulunan muhtemel hataları söyleyen programlara denir bu işlemede linting denir.
ESLint bu işi yapar kullanımı için => dokümantasyonlar, GOOGLE

**[Başa Git](#table-of-contents)**

## BOLUM-7

> (Temel Tasarım şablonları)

### MVC

MVC = Model-View-Controller

View - user ın gördüğü her şey
Controller - arkada gerçek işi yapan bölüm
Model - arkada data olarak duran bilgi

Backend kısmı gibi düşünebiliriz.
sitenin requestine göre database'den gelen model veriyi view a çevirip istenilen şekilde kullanmayı sağlar veya tam tersi.
Modellar ve Viewlar arasında bir köprüdür.

```javascript
var Views = {
  users: function (users) {
    var html = "<ul>";
    for (var i = 0; i < users.length; i++) {
      html += "<li>" + users[i].name + "</li>";
    }
    html += "</ul>";
    return html;
  },
};

var Controllers = {
  "#/": function () {
    console.log("hosgeldiniz");
  },
  "#/users": function () {
    var view = Views["users"]([
      { name: "fatih" }, // model
      { name: "dogukan" }, // model
    ]);
    document.body.innerHTML = view;
  },
};

window.onhashchange = function () {
  new Controllers[location.hash]();
};

new Controllers["#/"]();
```

yukarıdaki kodu eğer online bir siteye gidip konsolde çalıştırırsak öncelikle konsola hosgeldiniz yazdıracak sonrasında tanımladığımız şekilde .com dan sonra hash ile users a yollarsak
gelen name leri view daki for da html listesine çevirecek ve model da innerHTML ile oluşan HTML kodunu alıp anlık sayfanın içerisine dolduravcak ve kendi girdiğimiz name ler sayfaya düzgün bir şekilde yansımış olacak

---

### MVVM

MVVM = ModelView-ViewModel
bu yapı MVC den farklı olarak bir controller içermez fakat ViewModellar benzer işi görürler.
MVVM model ve viewın birbirine herzaman bağlı olduğunu söyler. Model çok önemlidir oradaki değişiklik view a bağlı olduğu için anlık değişimi sağlar
MVVM Framework Modelları Observe(takip) eder ve değişiklik olduğunda html i ona göre günceller.

```javascript
function usersView(users) {
  var html = "<ul>";
  for (var i = 0; i < users.length; i++) {
    html += "<li>" + users[i].name + "</li>";
  }
  html += "</ul>";
  return html;
}

var models = [
  { name: "fatih" }, // model
  { name: "dogukan" }, // model
];

var ViewModel = function () {
  setInterval(function () {
    document.body.innerHTML = usersView(models);
  }, 1000);
};
```

bu örnek kodda model ları observe eden bir yapı yok onun yerine observe ediyormuş gibi yapmak adına setInterval yapısı kullanılmış saniyede bir viewı yeniden yükler.
MVVM de yukarıdaki örnek yanlış bir yapıdır çünkü normalde obje değiştikçe bu değişen kısmı yenilemeli ama mantığını anlamak adına güzel bir örnek.
Angular, Vue ve Knockout MVVM frameworklere örneklerdir.

---

### DOM Manipülasyonu nedir

javascript kodları ile domun içerisindeki elementlere müdahele etmeye DOM manipülasyonu denir. DOM manipülasyonu html in dinamik olmasını sağlar

```javascript
//JS DOM Manipulation
var div = document.createElement("div");
div.innerHTML = "Fatih";

document.body.innerHTML = "";
document.body.appendChild(div);
//JQuery version
$("body").html("").append($("<div/>").html("Fatih"));

//JS DOM Manipulation
document.getElementById("button").addEventListener("click", function () {});
//JQuery version
$("#button").click(function () {});
```

jquery bu işi daha kolay yapmayı sağlayan bir kütüphanedir.
yukarıda js ve jquery ile aynı işlemleri yapan kod blokları bulunmakta.daha fazla bilgi için dokümantasyon.

---

### LODASH

çok kullanılan bir utility tool (faydalı araçların bulunduğu bir paket)
dokümantasyonuna kesinlikle bakmalı.

**[Başa Git](#table-of-contents)**

## BOLUM-8

> (TDD (Test Güdümlü Geliştirme))

### TDD NEDİR?

TDD = Test Driven Development
objelerin birbiriyle çok bağlantılı olduğu çok büyük projelerde bir obje içerisinde yapılan ufak bir değişiklik kodun büyük bir kısmını etkileyebilir ve bu içinden çıkılmayan buglara yol açabilir
kodun yapabileceği her şeyi koda assert edersin her türlü durumu bunun üzerinden test ederek kodunu assert ettiğin durumlar için kusursuz kılarsın bu yüzden bütün durumları assert etmek çok önemli
bu işi yapan frameworkler mevcut.

**[Başa Git](#table-of-contents)**

# ECMASCRIPT 6

## Arrow Functions

- callback'lerin ES6'da ki yazım stili.
- kendi contexti yok kendini kapsayan yapının contextini kullanır.

```javascript
fetchData().then((res) => {
  return res.data;
});
```

fonksiyon tanımında kullanılan **=>** sembolüne **'fat arrow'** denir.

```javascript
const getId = (res) => {
        return res.id;
    });
```

bu şekilde arrow functionlar bir değişkenede atanabilir.

```javascript
//sadece bir değişken alıyorsa parantezlere gerek duyulmaz bu örnekte res objesini alıp o objenin id değişkenini return etmekte.

const getId = (res) => {
  return res.id;
};

//yukarıdaki örnek bu şekilde de yazılabilir.

const getId = (res) => res.id;

//hiç değişken almıyorsa yada birden fazla alıyorsa parantezlere ihtiyaç duyulur.

const doSomething = () => {
  something();
};

const doSomething2 = (a, b) => {
  something();
};
```

- Arrow functionlar this kelimesinin kullanımını düzeltirler.

Eski javascript ile yazılmış bir constructor method.

```javascript
function MyConstructor(data, transport) {
  this.data = data;
  var self = this;
  //bir diğer hali:
  var _this = this;
  //kod self için devam etmektedir.
  transport.on("data", function () {
    alert(self.data);
  });
}
```

> Javascript dilinde her fonksiyon birer obje olduğundan, hepsinin içerisindeki this kendi context’ine ait. O yüzden callback içerisinde kullanılacak this artık MyConstructor’u göstermediğinden onu değişkene atıp o şekilde kullanıyorduk. Ancak arrow function’larda bu problem çözülmüş durumda. Bir arrow function’ın içinde çağırdığınız this parent objeye referans veriyor.

```javascript
// yukarıdaki örneğin arrow function ile düzenlenmiş halidir.
function MyConstructor(data, transport) {
  this.data = data;
  transport.on("data", () => {
    alert(this.data);
  });
}
```

**[Başa Git](#table-of-contents)**

## Property destructing

- Bir obje içerisinden kullanılacak özellikleri alıp ayrı bir değişkene atama olayına denir.

```javascript
let obj = {
  id: 1,
  type: 2,
  name: "Test",
};

const { id, type } = obj; // obj objesinin içerisinden sadece id ve type alınıp iki ayrı const değişkene atanır.
getById(id);

///////////////////////////

const getById = ({ id }) => {
  return doSthWithId(id);
};

getById(obj);
//burada ise objenin içindeki sadece id değerini alıp getById() metodunda döndürmek istiyorum.
```

**[Başa Git](#table-of-contents)**

## Template literals

ES6 ile gelen bir diğer özellik stringlerin `` işaretleri arasında çoklu satırlarda ve \${} operatörü kullanılarak değer döndürmek sağlanabilir.

```javascript
//eskiden:
var isim = "Durul";
console.log("Merhaba" + isim);

//Template literals ile
const name = "Durul";
console.log(`Merhaba ${name}`);
//Merhaba Durul

const obj = {
  name: "Okuyucu",
};
console.log(`Merhaba ${obj.name}`);
//Merhaba Okuyucu

const getName = () => {
  return "Test";
};
console.log(`Merhaba ${getName()}`);
//Merhaba Test

console.log(`Merhaba ${obj.name},
Bugün
Kendini
Nasıl
Hissediyorsun?`);

/*
Merhaba Okuyucu,
Bugün
Kendini
Nasıl
Hissediyorsun?
*/
```

- \${} karakterleri literal içerisinde özeldir kullanabilmek için escape etmek gerekir.

```javascript
console.log(
  `Template literal \` işaretleri içine \${} işaretleri kullanılarak yazılır.`
);

//Template literal ` işaretleri içine ${} işaretleri kullanılarak yazılır.

// ${} işaretinin tek başına escape edilmesi yeterlidir, \${} şeklinde.
```

### Tagged Literal

- tagged literal da literal string oluşmasından önce bir **tag function** denilen fonksiyondan geçiyor.

```javascript
function selamla(str, nameArg) {
  return `selamlar! hoşgeldin ${nameArg}`;
}

let name = "Okuyucu";
selamla`Merhaba ${name}`;
//selamlar! hoşgeldin Okuyucu
```

Bu sayede template literal’inin nasıl oluşacağına karar veriyoruz. Bu method içinde işlem de yapabilirsiniz.

**[Başa Git](#table-of-contents)**

## Rest Spread operators

> Obje ve dizi rest/spread operatörleri

### SPREAD

- spread operatörü bir dizinin elemanlarını başka bir diziye ekleyebilir.

```javascript
const eklenecekler = ["elma", "armut", "üzüm"];

const meyveler = ["çilek", ...eklenecekler, "kiraz", "karpuz", "kavun"];

console.log(meyveler);
//["çilek", "elma", "armut", "üzüm", "kiraz", "karpuz", "kavun"]
```

- bir dizideki elemanları bir fonksiyona girdi olarak verebilir.

```javascript
function topla(a, b, c) {
  console.log(a + b + c);
}

const toplanacaklar = [1, 2, 3];
topla(...toplanacaklar);
//6
```

- dizilerin elemanlarını başka dizilere kopyalayabilir.

```javascript
const arr = [1, 2, 3];
const arr1 = [...arr];

console.log(arr1);
//[1, 2, 3]
```

- dizileri birleştirebilir.

```javascript
let arr = [0, 1, 2];
let arr1 = [3, 4, 5];

arr1 = [...arr, ...arr1];
//aynı diziyi yeniden tanımladığım için const kullanamam.

console.log(arr1);
//[0, 1, 2, 3, 4, 5]
```

**[Başa Git](#table-of-contents)**

### REST

- görünüş olarak spread ile aynıdır ama spread'in tam tersini yapar. spread olan bir dizinin elemanlarını saçarken rest girilen elemanları toplayıp array haline getirir.

```javascript
function diziyiCarp(carpan, ...girdiler) {
  return girdiler.map(function (element) {
    return carpan * girdiler;
  });
}
```

bu örnek ilk girilen değer dışında bütün girilen sayıları dizi haline getirir ve ilk girilen carpan sayısı ile çarpar ve sonucu yine bir dizi olarak verir.

**[Başa Git](#table-of-contents)**

## Property value shorthand notation

- Bir objeye property atarken eğer atayacağınız değişkenin ismi ile property ismi aynı ise tekrar kendisini yazmanıza gerek kalmıyor.

```javascript
const name = "Okuyucu";
const obj = {
  id: 1,
  name,
};
```

**[Başa Git](#table-of-contents)**

# Clean Coding in JavaScript

Kötü yazılmış bir kod bir programcıyı ya da projeyi her zaman yavaşlatır peki neden hala kötü kod yazılır gelecek cevap basittir çünkü işin hızlı bitmesi gerekir bu cümledeki mantıksal sıkıntı kodumuzu neden düzgün temiz kullanılabilir ve okunabilir yazmamızın gerekçesidir. temiz kod yazmaya ayırılan zaman her zaman işleri hızlandırır.

## Kötü Kod Kedir?

Kötü kod en basit haliyle okuduğunuzda ne yaptığını anlamadığınız koddur çünkü temiz yazılmış bir kod ne yaptığını anlatmalıdır.

## Kötü Kod Bizi Nasıl Yavaşlatır?

- Kötü kodu değiştirmek istediğinizde genelde başka bir yeri çöker buna **rigidity** (türkçesi ile sertlik denilebilir) denir.
  > Rigidity: Kodun değiştirmesi zor olması durumuna denir. sistemdeki her modüle dokunan her şeyden izole bir değişiklik yapması zor olan koda rigit (katı) kod denir.
- Kötü kodu bir kısmını değiştirmek istediğinizde alakasız başka bir bölümden hata alırsınız buna **fragility** (türkçesi ile kırılganlık denilebilir)denir.
  > Fragility: Kodun anlamsız yerlerde hata çıkarması
- Yazıldığı yerin dışında kullanılamayan kod da kötü koddur. eğer bir arkadaşınızın yazdığı kodun sadece istediğiniz bir bölümünü alıp kendi kodunuzda yazdığı her şey farklı bölümlerden parçalar barındırdığı için kullanamıyorsanız kötü kod yazan bir arkadaşınız var demektir bu olaya da **immobility** denir.

  > Immobility: Kodu orijinal içeriği dışında kullanamama durumuna denir.

- Otomatik açılan cama sahip bir arabanız olduğunu düşünün ama camlardan biri bozuk arabanıza binip tamirciye gittiniz ve tamirci size sorunu yarına çözeceğini söyledi yarın olduğunda ve arabanızı almaya gittiğinizde tamirci size yaptığı işten gururlu bir şekilde camın açılıp kapandığını gösterdi mutlu bir şekilde arabanıza bindiniz marşa bastınız ama o da ne motor çalışmıyor. O tamircinin işini bilmediğini düşünür ve bir daha o tamirciye gitmezsiniz. yukarıdaki durumlar bu örneğe benzer bir gün ürününüzde bir hata çıktığında yapmanız gereken ufak bir değişiklik sürmesi gerekenden çok daha fazla zaman alıyorsa kimse sizin iyi bir yazılımcı olduğunuzu düşünmez temiz kod yazmak bu yüzden çok önemlidir.

- Bu üç kötü kod tanımının asıl sorunu coupling'dir. Coupling ise bir sistemde bulunan modüllerin birbirine olan bağımsızlığını temsil eden bir derecelendirmedir. O zaman kötü bir kodu alıp bütün bağımlılıklarını kesersem onu düzeltmiş olurum peki bunu nasıl yaparım cevap çok basit Object Oriented Programming (Nesne Yönelimli Programlama) ile tam olarak bu noktada temiz kod yazmak adına işin içine SOLID principles (KATI prensipler) dahil olur.

## SOLID principles

SOLID principles class dizaynı için olan kurallardır ve bir kısaltmadır her harf bir prensipe denk gelir

| S                                       | O                             | L                                     | I                                       | D                                      |
| --------------------------------------- | ----------------------------- | ------------------------------------- | --------------------------------------- | -------------------------------------- |
| SRP:the Single Responsibility principle | OCP:the Open/Closed Principle | LSP:the Liskov Substitution Principle | ISP:the Interface Segregation Principle | DIP:the Dependency Inversion Principle |

### The Single Responsibility Principle

Türkçesi ile tek amaç prensibi denilebilir. Bu prensip der ki bir modülün ya da classın sadece ama sadece değişmek için tek amacı olmalıdır veya tek şeyi değiştirmelidir de denilebilir.

```javascript
//Bad

class UserSettings {
  constructor(user) {
    this.user = user;
  }

  changeSettings(settings) {
    if (this.verifyCredentials()) {
      // ...
    }
  }

  verifyCredentials() {
    // ...
  }
}

//Good

class UserAuth {
  constructor(user) {
    this.user = user;
  }

  verifyCredentials() {
    // ...
  }
}

class UserSettings {
  constructor(user) {
    this.user = user;
    this.auth = new UserAuth(user);
  }

  changeSettings(settings) {
    if (this.auth.verifyCredentials()) {
      // ...
    }
  }
}
```

- Yukarıda görmüş olduğunuz örnekte ilk durumda kötü kullanımda UserSettings class'ının değişmek için iki fonksiyonu bulunuyor bu da beklemdiğiniz bir zamanda iki fonksiyonun değişikliklerinin birbirini etkilemesine neden olabilir çözüm ise çok basit bu iki değişiklik yapan fonksiyonu iki ayrı class'a ayırarak bu sorunu çözebiliriz

### The Open/Closed Principle

Bir mobil uygulamanız olduğunu düşünün uygulamanıza yeni bir özellik ekleyeceksiniz ama eskiden yazılmış olan hiçbir kodu değiştirmemeniz gerek bu tek şarta uygun bir uygulama yazdıysanız bu prensibi başarıyla gerçekleştirmişsiniz demektir.

```javascript
// BAD
var iceCreamFlavors=["chocolate","vanilla"];
var iceCreamMaker={
 makeIceCream (flavor) {
  if(iceCreamFlavors.indexOf(flavor)>-1){
   console.log("Great success. You now have ice cream.")
  }else{
   console.log("Epic fail. No ice cream for you.")
  }
 }
}
export default iceCreamMaker;

// GOOD
var iceCreamFlavors=["chocolate","vanilla"];
var iceCreamMaker={
 makeIceCream (flavor) {
  if(iceCreamFlavors.indexOf(flavor)>-1){
   console.log("Great success. You now have ice cream.")
  }else{
   console.log("Epic fail. No ice cream for you.")
  }
 }
 addFlavor(flavor){
  iceCreamFlavors.push(flavor);
 }
}
export default iceCreamMaker;
```

- Yukarıda gördüğünüz örnekte kötü kullanımda dondurma yapma fonksiyonunuzu yine çalıştırabilirsiniz ama yeni bir flavor eklemek istediğinizde ne olacak girip eskiden yazmış olduğunuz flavor dizisinde değişiklik yapmanız gerekecek bu da bu prensibin tek şartına uymaz. İyi kullanım örneğinde ise sadece addFlavor fonksiyonu ile bu işi çözmüş olduk.

### The Liskov Substitution Principle

Türetilmiş classlar kendi base classlarının özelliklerini kullanabilir olmalı. Bu prensip bir örnekle daha güzel anlaşılabilir.

```javascript
// BAD

class Rectangle {
  constructor() {
    this.width = 0;
    this.height = 0;
  }

  setColor(color) {
    // ...
  }

  render(area) {
    // ...
  }

  setWidth(width) {
    this.width = width;
  }

  setHeight(height) {
    this.height = height;
  }

  getArea() {
    return this.width * this.height;
  }
}

class Square extends Rectangle {
  setWidth(width) {
    this.width = width;
    this.height = width;
  }

  setHeight(height) {
    this.width = height;
    this.height = height;
  }
}

function renderLargeRectangles(rectangles) {
  rectangles.forEach((rectangle) => {
    rectangle.setWidth(4);
    rectangle.setHeight(5);
    const area = rectangle.getArea(); // BAD: Returns 25 for Square. Should be 20.
    rectangle.render(area);
  });
}

const rectangles = [new Rectangle(), new Rectangle(), new Square()];
renderLargeRectangles(rectangles);

// GOOD

class Shape {
  setColor(color) {
    // ...
  }

  render(area) {
    // ...
  }
}

class Rectangle extends Shape {
  constructor(width, height) {
    super();
    this.width = width;
    this.height = height;
  }

  getArea() {
    return this.width * this.height;
  }
}

class Square extends Shape {
  constructor(length) {
    super();
    this.length = length;
  }

  getArea() {
    return this.length * this.length;
  }
}

function renderLargeShapes(shapes) {
  shapes.forEach((shape) => {
    const area = shape.getArea();
    shape.render(area);
  });
}

const shapes = [new Rectangle(4, 5), new Rectangle(4, 5), new Square(5)];
renderLargeShapes(shapes);
```

- Kötü kullanımda gördüğümüz üzere bir dikdörtgen classı tanımlanmış ve ondan bir kare classı türetilmiş daha sonrasında renderLargeRectangles fonksiyonu ile bir render fonksiyonu yazılmış daha sonra dikdörtgenlerin olduğu bir dizi oluşturulup içerisine iki dikdörtgen bir kare konulmuş ve render fonksiyonuna yollanmış burada ki sıkıntı kare de başlar kare onun base classı olan dikdörtgenin aksine yükseklik ve genişliktense sadece tek bir uzunluğa ihtiyaç duyduğu için istenilen gibi davranışlar gösteremez.
- Bu durumu düzeltmek için iyi örnekte bir Shape (şekil) classı oluşturulmuş ve iki geometrik şekilde bu class'tan türetilmiş ve ikisinede ayrı constructor fonksiyonlar yazılmış ve gördüğünüz gibi en son şekillerin bulunacağı diziyi hazırlarken istediğimiz uzunluk değerini istediğimiz şekile olamsı gerektiği gibi atayıp render edebiliyoruz.
  > Geometrik olarak Kareler her ne kadar dikdörtgen olsalarda kodlarken kareler dikdörtgen gibi davranmazlar.

---

> **"If it looks like a duck, quacks like a duck, but needs batteries you probably have the wrong abstraction"**

### The Interface Segregation Principle

Belirli methodların interfaceleri
iyi ayrılmış hale getirilmeli. JavaScript dilinde diğer dillerde olduğu gibi interfaceler yoktur ama bu maddeyi şu şekilde bir örnek yardımı ile açıkalaybiliriz.

```javascript
//BAD

var Shape = function () {};
Shape.prototype.area = function () {
  /*........*/
};
Shape.prototype.volume = function () {
  /*........*/
};
//We cannot assume that the shape is 3D
var Triangle = function (base, height) {
  this.base = base;
  this.height = height;
};

Triangle.prototype = Object.create(Shape.prototype);
//Now triangle has an unnecessary volume method

//GOOD

var Shape = function () {};
Shape.prototype.area = function () {
  /*........*/
};

var SolidShape = function () {};
Shape.prototype.volume = function () {
  /*........*/
};

var cube = new SolidShape();
var triangle = new Shape();
```

- Kötü kullanımda görüldüğü gibi oluşturalacak olan şekilin üç boyutlu olacağı kabul edilerek bir yapı kurulmuş fakat iki boyutlu bir üçgen türettiğimiz zaman üçgen objesinin gereksiz bir hacim fonksiyonu bulunmakta.
- Bunu düzeltmek için basit bir şekilde Shape classını ikiye ayırdık ve üçboyutlu objelerin alttaki şartları kullanmasını sağladık böylelikle iki boyutlu oluşturulacak objelerin gereksiz yere içerisinde fonksiyon barındırmasından kurtulmuş olduk.

### The Dependency Inversion Principle

> - High-level modules should not depend on low-level modules. Both should depend on abstractions.
> - Abstractions should not depend on details. Details should depend on abstractions.

Online bir mağazanız olduğunu düşünün ve ödeme işlemleri için x API'ını kullanıyorsunuz ve marketiniz x API'ına doğrudan bağlı bir gün yeni bir API ile çalışmak istediğinizde yada hazırda kullandığınız API içeriği değiştiren bir güncelleme getirirse sizin mağazanızı baştan yeniliklere düzenlemeniz ve eski kodlarınızı yeniden yazmanız gerekir.Çözüm ise çok basit eğer araya bir ödeme alma modülü hazırlarsanız ve bu modülü sisteminizin ve API larınızın arasına koyarsanız hem istediğiniz kadar API ekleyebilirsiniz hem de değişikliğe neden olan güncellemeler size çok zahmetli işler çıkarmaz.

```javascript
//BAD

class Store {
  constructor(user) {
    this.xAPI = new XAPI(user);
  }

  purchaseBike(quantity) {
    this.xAPI.makePayment(200 * quantity);
  }

  purchaseHelmet(quantity) {
    this.xAPI.makePayment(15 * quantity);
  }
}

const store = new Store("User");

store.purchaseBike(1);
store.purchaseHelmet(2);

//GOOD

class Store {
  constructor(paymentProcessor) {
    this.paymentProcessor = paymentProcessor;
  }

  purchaseBike(quantity) {
    this.paymentProcessor.pay(200 * quantity);
  }

  purchaseHelmet(quantity) {
    this.paymentProcessor.pay(15 * quantity);
  }
}

class XAPIPaymentProcessor {
  constructor(user) {
    this.user = user;
    this.xAPI = new XAPI(user);
  }

  pay(amountInDollars) {
    this.xAPI.makePayment(amountInDollars);
  }
}

const store = new Store(new XAPIPaymentProcessor("User"));

store.purchaseBike(1);
store.purchaseHelmet(2);
```

- Yukarıdaki kod verilen örneğin kodudur.

**[Başa Git](#table-of-contents)**