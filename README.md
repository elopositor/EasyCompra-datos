# EasyCompra · datos

Catálogo de alimentación de cuatro supermercados españoles, con precios y datos
nutricionales, en JSON. Se regenera **automáticamente cada día a las 06:00 UTC**.

Este repositorio contiene **solo los datos**. El código que los genera —scrapers,
API y app Android— está en **[elopositor/EasyCompra](https://github.com/elopositor/EasyCompra)**.

## Ficheros

| Fichero | Contenido |
|---|---|
| `index.json` | Manifiesto: fecha del último sync, ficheros disponibles y número de productos. Léelo primero. |
| `carrefour.json` | Productos de Carrefour |
| `dia.json` | Productos de Dia |
| `lidl.json` | Productos de Lidl |
| `mercadona.json` | Productos de Mercadona |

## Uso

```
https://raw.githubusercontent.com/elopositor/EasyCompra-datos/main/index.json
https://raw.githubusercontent.com/elopositor/EasyCompra-datos/main/mercadona.json
```

## Formato

Cada fichero es una lista de productos con esta forma:

```json
{
  "supermarket": "Mercadona",
  "external_id": "20221",
  "id": "mercadona_20221",
  "name": "Yogur natural edulcorado Hacendado 0% MG",
  "brand": "Hacendado",
  "photo_url": "https://…",
  "unit_price": 1.05,
  "reference_price": 1.4,
  "reference_format": "kg",
  "ean": "8480000202215",
  "ingredients": "Leche fresca pasteurizada desnatada…",
  "allergens": "Contiene leche y sus derivados…",
  "contains_nata": false,
  "energy_kcal_100g": 45,
  "fat_100g": 0.2,
  "saturated_fat_100g": 0.1,
  "carbohydrates_100g": 6.2,
  "sugars_100g": 5.1,
  "proteins_100g": 4.4,
  "salt_100g": 0.13,
  "share_url": "https://…"
}
```

Garantías del formato, para que un cliente pueda confiar en ellas:

- Los campos de precio y nutrición son **siempre número o `null`**, nunca texto.
- `contains_nata` es siempre booleano.
- `supermarket`, `external_id`, `id` y `name` siempre vienen informados.
- Pueden aparecer campos nuevos en el futuro: ignora los que no conozcas.

`unit_price` es el precio del envase y `reference_price` el precio por
`reference_format` (kg o L), que es el que sirve para comparar formatos distintos.

La cobertura nutricional es parcial: depende de que el supermercado facilite el
código de barras y de que el producto esté en OpenFoodFacts. Hoy Dia y Mercadona
traen nutrición; Carrefour y Lidl, de momento, no.

## Procedencia y uso

Datos recogidos de las webs públicas de Carrefour, Dia, Lidl y Mercadona, y
enriquecidos con [OpenFoodFacts](https://es.openfoodfacts.org/) (licencia ODbL).
Pertenecen a sus respectivos titulares y se publican aquí para uso personal y no
comercial. Los precios pueden estar desactualizados o contener errores: no son
una fuente oficial y no sirven como referencia de compra.
