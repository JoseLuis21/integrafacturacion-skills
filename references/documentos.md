# Tipos de documento y fuentes SII

Usa esta referencia para decidir qué archivo consultar según `code_sii`.

## Mapa principal

| code_sii | Documento | Markdown SII | JSON razonable |
|---|---|---|---|
| `33` | Factura Electrónica | `../source-md/DTE_33_Factura_Electronica.md` | `../examples-json/DTE_33_Factura_Electronica_solo_afecto.json` y `../examples-json/DTE_33_Factura_Electronica_mixto_afecto_exento.json` |
| `34` | Factura Electrónica Exenta | `../source-md/DTE_34_Factura_Electronica_Exenta_No_Afecta.md` | `../examples-json/DTE_34_Factura_Electronica_Exenta.json` |
| `39` | Boleta Electrónica | `../source-md/BOLETA_39_Boleta_Electronica.md` | `../examples-json/BOLETA_39_solo_afecto.json` y `../examples-json/BOLETA_39_mixto_afecto_exento.json` |
| `41` | Boleta Exenta Electrónica | `../source-md/BOLETA_41_Boleta_Exenta_Electronica.md` | `../examples-json/BOLETA_41_Exenta.json` |
| `43` | Liquidación Factura Electrónica | `../source-md/DTE_43_Liquidacion_Factura_Electronica.md` | `../examples-json/DTE_43_Liquidacion_Factura_Electronica_solo_afecto.json` y `../examples-json/DTE_43_Liquidacion_Factura_Electronica_mixto_afecto_exento.json` |
| `46` | Factura de Compra Electrónica | `../source-md/DTE_46_Factura_de_Compra_Electronica.md` | `../examples-json/DTE_46_Factura_de_Compra_Electronica_solo_afecto.json` y `../examples-json/DTE_46_Factura_de_Compra_Electronica_mixto_afecto_exento.json` |
| `52` | Guía de Despacho Electrónica | `../source-md/DTE_52_Guia_de_Despacho_Electronica.md` | `../examples-json/DTE_52_Guia_de_Despacho_Electronica_solo_afecto.json` y `../examples-json/DTE_52_Guia_de_Despacho_Electronica_mixto_afecto_exento.json` |
| `56` | Nota de Débito Electrónica | `../source-md/DTE_56_Nota_de_Debito_Electronica.md` | `../examples-json/DTE_56_Nota_de_Debito_Electronica_solo_afecto.json` y `../examples-json/DTE_56_Nota_de_Debito_Electronica_mixto_afecto_exento.json` |
| `61` | Nota de Crédito Electrónica | `../source-md/DTE_61_Nota_de_Credito_Electronica.md` | `../examples-json/DTE_61_Nota_de_Credito_Electronica_solo_afecto.json` y `../examples-json/DTE_61_Nota_de_Credito_Electronica_mixto_afecto_exento.json` |

## Uso recomendado

### Si el usuario pide payload mínimo

Usa el ejemplo del Postman como base y reduce a:
- `Encabezado.IdDoc`
- `Encabezado.Emisor`
- `Encabezado.Receptor`
- `Encabezado.Totales`
- `Detalle`

### Si el usuario pide payload realista

Usa uno de los JSON razonables de negocio.

### Si el usuario pide validación de campos

Abre el markdown SII del tipo correspondiente y responde con:
- campos requeridos
- opcionales relevantes
- restricciones de tipo, longitud o enumeración

## Nota importante

Los markdown de este proyecto fueron limpiados para excluir `TED`, firma y bloques criptográficos. Úsalos como referencia de datos del documento, no como guía de timbrado o firma XML.
