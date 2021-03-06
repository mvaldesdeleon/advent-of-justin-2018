Willkommen beim *Advent of Justin* 2018! Ich habe schon darüber Witze gemacht
dass das passieren wird, aber jetzt ist es wohl tatsächlich soweit.

Für den ersten Tag habe ich mir vorgenommen euch eines meiner schon etwas
älteren Lieblingsprojekte vorzustellen: Simple-JSON. Hierbei handelt es sich um
eine Library die ich ursprünglich im Juli 2017 gebaut habe, mit der Erwartung
dass es nur eine Demo wird. Ich konnte damals noch nicht ahnen dass die Library
ziemlich beliebt werden würde um eine einfache Möglichkeit für die automatische
(De)serialisierung von JSON/Foreign zu haben. Als ich dann damit anfing,
PureScript für die Arbeit zu verwenden habe ich auch gleich damit begonnen
diese Library zu verwenden.

Was mir an dieser Library so gut gefällt ist nicht unbedingt einmal der
JSON-Teil, aber dass man damit gut demonstrieren kann dass man Typen verwenden
kann um Werte abzuleiten. Das ist auch der Grund warum ich PureScript lieber
benutze als jede andere Sprache die nach JS kompiliert und was ihr in den
meisten meiner PureScript-Posts sehen werdet.

## "Writing a JSON decoder using Purescript's RowToList"

In diesem Post erkläre ich genauer was eigentlich ein `Record` ist und wie die
Row Type-Informationen als iterierbare Datenstruktur auf Typebene verwendet
werden können um Decoder und Encoder für JS-Werte abzuleiten:

<https://qiita.com/kimagure/items/d8a0681ae05b605c5abe>

Früher in diesem Jahr habe ich begonnen etwas Aufwand in die Dokumentation
einiger meiner Libraries zu stecken. Daher gibt es jetzt diese Dokumentation
für Simple-JSON: <https://purescript-simple-json.readthedocs.io/en/latest/index.html>.
Alles was ein Nutzer dieser Library braucht ist dort zu finden, sogar mit einem
Leitfaden wie man Generics-Rep benutzt um seine eigenen Encodings für
Summen-/Produkttypen zu schreiben.

Hier ein Auszug aus der Quickstart-Seite:

```hs
import Simple.JSON as JSON

type MyRecordAlias =
  { apple :: String
  , banana :: Array Int
  }

testJSON1 :: String
testJSON1 = """
{ "apple": "Hello"
, "banana": [ 1, 2, 3 ]
}
"""

main = do
  case JSON.readJSON testJSON1 of
    Right (r :: MyRecordAlias) -> do
      assertEqual { expected: r.apple, actual: "Hello"}
      assertEqual { expected: r.banana, actual: [ 1, 2, 3 ] }
    Left e -> do
      assertEqual { expected: "failed", actual: show e }
```

## P.S.

The erste Post des *Advent of Justin* ist etwas länger geraten als geplant.
Die nächsten Posts werden kürzer, aber hoffentlich lest ihr dann mehrere davon.

---

Bienvenidos al [Adviento](https://es.wikipedia.org/wiki/Calendario_de_Adviento) de Justin 2018! Había bromeado sobre hacer esto, pero parece que finalmente va a ser realidad.

Para el primer día me gustaría presentar a un viejo favorito: Simple-JSON. Esta es una librería que hice en Julio del 2017, con la expectativa de que seria tan solo una demo. Poco podía saber entonces que esta librería se volvería relativamente popular como una forma atractiva de obtener serialización y deserialización automática de JSON/Foreign, y yo mismo me encontré utilizándola cuando comencé a usar PureScript en el trabajo.

Lo que más me gusta de esta librería ni siquiera es la parte sobre JSON, sino que demuestra que podemos usar tipos para derivar valores a utilizar. Esto es lo que me hace seguir usando PureScript por encima de cualquier otro lenguaje que compile a JS, y lo que verán resaltado en la mayoría de mis posts sobre PureScript.

## "Escribiendo un decoder JSON usando RowToList en PureScript"

En este post presento exactamente qué es un Record, y cómo la información sobre la _fila_ de tipos puede ser transformada en una estructura de datos iterable a nivel de tipos para derivar encoders y decoders de valores de JS:

<https://qiita.com/kimagure/items/d8a0681ae05b605c5abe>

Hacia principios del año, comencé a dedicarle un poco de esfuerzo a documentar algunas de mis librerías. Gracias de ese esfuerzo, ahora tengo la siguiente documentación para Simple-JSON: <https://purescript-simple-json.readthedocs.io/en/latest/index.html>. Todo lo que un usuario de la librería debería necesitar esta ahí, incluyendo una guía sobre como usar Generics-Rep para escribir tus propios encodings para tipos suma o producto.

Este es un extracto de la guía de comienzo rápido:

```hs
import Simple.JSON as JSON

type MyRecordAlias =
  { apple :: String
  , banana :: Array Int
  }

testJSON1 :: String
testJSON1 = """
{ "apple": "Hello"
, "banana": [ 1, 2, 3 ]
}
"""

main = do
  case JSON.readJSON testJSON1 of
    Right (r :: MyRecordAlias) -> do
      assertEqual { expected: r.apple, actual: "Hello"}
      assertEqual { expected: r.banana, actual: [ 1, 2, 3 ] }
    Left e -> do
      assertEqual { expected: "failed", actual: show e }
```

## P.D.

Bueno, el primer post del Adviento de Justin termino siendo un poco mas largo de lo planeado. Los próximos posts serán mas cortos, así que espero que leas más de estos.

---

Welcome to the Advent of Justin 2018! I've joked about making this happen, but I guess now it's actually happening.

For the first day, I figured I would introduce an old favorite: Simple-JSON. This is a library that I first made in July 2017, with some expectation that it would just be a demo. Little did I know, this library actually became fairly popular as a nice way to get automatic de/serialization of JSON/Foreign, and I found myself immediately putting this library to work when beginning to use PureScript for work.

The thing that I like so much about this library isn't really even the JSON part, but that it shows that you can readily use types to derive values to put to use. This is what makes me keep using PureScript over any other language that compiles to JS, and what you'll see featured in most of my posts about PureScript.

## "Writing a JSON decoder using Purescript's RowToList"

In this post, I go through what exactly a `Record` is, and how the row type information can be turned into a type-level iterable data structure to derive decoders and encoders for JS values:

<https://qiita.com/kimagure/items/d8a0681ae05b605c5abe>

Earlier this year, I started putting some effort into documentation of some of my libraries. From that effort, I have these docs for Simple-JSON now: <https://purescript-simple-json.readthedocs.io/en/latest/index.html>. Everything a user of this library should need is just about here, with even a guide for how to use Generics-Rep to write your own encodings for sum/product types.

Here's an excerpt from the quickstart page:

```hs
import Simple.JSON as JSON

type MyRecordAlias =
  { apple :: String
  , banana :: Array Int
  }

testJSON1 :: String
testJSON1 = """
{ "apple": "Hello"
, "banana": [ 1, 2, 3 ]
}
"""

main = do
  case JSON.readJSON testJSON1 of
    Right (r :: MyRecordAlias) -> do
      assertEqual { expected: r.apple, actual: "Hello"}
      assertEqual { expected: r.banana, actual: [ 1, 2, 3 ] }
    Left e -> do
      assertEqual { expected: "failed", actual: show e }
```

## P.S.

So the first post of the Advent of Justin ended up being a little longer than planned. The next posts will be shorter, but hopefully you'll read through some more of these.
