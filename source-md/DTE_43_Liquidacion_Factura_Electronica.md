# DTE 43 - Liquidacion Factura Electronica

Campos extraídos desde `DTE_v10.xsd` + restricciones reutilizadas desde `SiiTypes_v10.xsd`.

## Cómo leer este archivo

- **Requerido** se obtiene de `minOccurs` o `use="required"`.
- **Mínimo / Máximo** refleja restricciones explícitas del XSD: `minInclusive`, `maxInclusive`, `minLength`, `maxLength` o `length`.
- **Largo** solo se llena cuando el XSD fija un largo exacto.
- **Enumeración / patrón** muestra valores cerrados o regex cuando existen.
- **Notas** incluye `totalDigits`, `fractionDigits`, documentación del tipo y valores fijos (`fixed`) cuando aplica.

## Notas

- Este archivo corresponde específicamente al **TipoDTE 43 (Liquidacion Factura Electronica)**.
- La estructura base proviene de la rama **Liquidacion** del `choice` principal del `DTE_v10.xsd`.
- El campo `TipoDTE` fue acotado en esta documentación al valor **43**.
- Las reglas de “requerido / opcional” aquí reflejan lo que exige el **XSD**. Si el SII tiene validaciones de negocio adicionales por tipo de documento, esas no siempre quedan expresadas en el esquema.

## Campos

| Ruta | Tipo XSD | Requerido | Ocurrencias | Base | Mínimo | Máximo | Largo | Enumeración / patrón | Descripción | Notas |
|---|---|---|---|---|---|---|---|---|---|---|
| DTE | SiiDte:DTEDefType | Sí | 1..1 | - | - | - | - | - | - | - |
| DTE/@version | xs:decimal | Sí | - | - | - | - | - | - | - | valor fijo: 1.0 |
| DTE/Liquidacion | anonymous | Sí | 1..1 | - | - | - | - | - | [DTE choice opción 2: Liquidacion] Informacion Tributaria de Liquidaciones | - |
| DTE/Liquidacion/@ID | xs:ID | Sí | - | - | - | - | - | - | [DTE choice opción 2: Liquidacion] | - |
| DTE/Liquidacion/Encabezado | anonymous | Sí | 1..1 | - | - | - | - | - | [DTE choice opción 2: Liquidacion] Identificacion y Totales del Documento | - |
| DTE/Liquidacion/Encabezado/IdDoc | anonymous | Sí | 1..1 | - | - | - | - | - | [DTE choice opción 2: Liquidacion] Identificacion del DTE | - |
| DTE/Liquidacion/Encabezado/IdDoc/TipoDTE | SiiDte:LIQType | Sí | 1..1 | xs:positiveInteger | - | - | - | 43 | Tipo de DTE (Liquidacion Factura Electronica) | Tipo específico documentado: 43 = Liquidacion Factura Electronica |
| DTE/Liquidacion/Encabezado/IdDoc/Folio | SiiDte:FolioType | Sí | 1..1 | xs:positiveInteger | - | - | - | - | [DTE choice opción 2: Liquidacion] Folio del Documento Electronico | totalDigits=10; Folio de DTE - 10 digitos |
| DTE/Liquidacion/Encabezado/IdDoc/FchEmis | SiiDte:FechaType | Sí | 1..1 | xs:date | 2000-01-01 | 2050-12-31 | - | - | [DTE choice opción 2: Liquidacion] Fecha Emision Contable del DTE (AAAA-MM-DD) | Fecha entre 2000-01-01 y 2050-12-31 |
| DTE/Liquidacion/Encabezado/IdDoc/IndServicio | anonymous | No | 0..1 | xs:positiveInteger | - | - | - | 1, 2, 3 | [DTE choice opción 2: Liquidacion] Indica si Transaccion Corresponde a la Prestacion de un Servicio | - |
| DTE/Liquidacion/Encabezado/IdDoc/MntBruto | anonymous | No | 0..1 | xs:integer | - | - | - | 1 | [DTE choice opción 2: Liquidacion] Indica el Uso de Montos Brutos en Detalle | - |
| DTE/Liquidacion/Encabezado/IdDoc/TpoTranCompra | SiiDte:TipoTransCOMPRA | No | 0..1 | xs:positiveInteger | 1 | 7 | - | 1, 2, 3, 4, 5, 6, 7 | [DTE choice opción 2: Liquidacion] Tipo de Transacción para el comprador \| Indica el Uso de Montos Brutos en Detalle | Tipo de Transacción para el comprador |
| DTE/Liquidacion/Encabezado/IdDoc/TpoTranVenta | SiiDte:TipoTransVENTA | No | 0..1 | xs:positiveInteger | 1 | 4 | - | 1, 2, 3, 4 | [DTE choice opción 2: Liquidacion] Tipo de Transacción para el vendedor \| Indica el Uso de Montos Brutos en Detalle | Tipo de Transacción para el vendedor |
| DTE/Liquidacion/Encabezado/IdDoc/FmaPago | anonymous | No | 0..1 | xs:positiveInteger | - | - | - | 1, 2, 3 | [DTE choice opción 2: Liquidacion] Forma de Pago del DTE | - |
| DTE/Liquidacion/Encabezado/IdDoc/FchCancel | SiiDte:FechaType | No | 0..1 | xs:date | 2000-01-01 | 2050-12-31 | - | - | [DTE choice opción 2: Liquidacion] Fecha de Cancelacion del DTE (AAAA-MM-DD) | Fecha entre 2000-01-01 y 2050-12-31 |
| DTE/Liquidacion/Encabezado/IdDoc/MntCancel | SiiDte:MontoType | No | 0..1 | xs:nonNegativeInteger | - | - | - | - | [DTE choice opción 2: Liquidacion] Monto Cancelado al emitirse el documento | totalDigits=18; Monto de 18 digitos |
| DTE/Liquidacion/Encabezado/IdDoc/SaldoInsol | SiiDte:MontoType | No | 0..1 | xs:nonNegativeInteger | - | - | - | - | [DTE choice opción 2: Liquidacion] Saldo Insoluto al emitirse el documento | totalDigits=18; Monto de 18 digitos |
| DTE/Liquidacion/Encabezado/IdDoc/MntPagos | anonymous | No | 0..30 | - | - | - | - | - | [DTE choice opción 2: Liquidacion] Tabla de Montos de Pago | - |
| DTE/Liquidacion/Encabezado/IdDoc/MntPagos/FchPago | SiiDte:FechaType | Sí | 1..1 | xs:date | 2000-01-01 | 2050-12-31 | - | - | [DTE choice opción 2: Liquidacion] Fecha de Pago (AAAA-MM-DD) | Fecha entre 2000-01-01 y 2050-12-31 |
| DTE/Liquidacion/Encabezado/IdDoc/MntPagos/MntPago | SiiDte:MontoType | Sí | 1..1 | xs:nonNegativeInteger | - | - | - | - | [DTE choice opción 2: Liquidacion] Monto de Pago | totalDigits=18; Monto de 18 digitos |
| DTE/Liquidacion/Encabezado/IdDoc/MntPagos/GlosaPagos | anonymous | No | 0..1 | xs:string | - | 40 | - | - | [DTE choice opción 2: Liquidacion] | - |
| DTE/Liquidacion/Encabezado/IdDoc/PeriodoDesde | SiiDte:FechaType | No | 0..1 | xs:date | 2000-01-01 | 2050-12-31 | - | - | [DTE choice opción 2: Liquidacion] Periodo de Facturacion - Desde (AAAA-MM-DD) | Fecha entre 2000-01-01 y 2050-12-31 |
| DTE/Liquidacion/Encabezado/IdDoc/PeriodoHasta | SiiDte:FechaType | No | 0..1 | xs:date | 2000-01-01 | 2050-12-31 | - | - | [DTE choice opción 2: Liquidacion] Periodo Facturacion - Hasta (AAAA-MM-DD) | Fecha entre 2000-01-01 y 2050-12-31 |
| DTE/Liquidacion/Encabezado/IdDoc/MedioPago | SiiDte:MedioPagoType | No | 0..1 | xs:string | - | - | - | CH, LT, EF, PE, TC, CF, OT | [DTE choice opción 2: Liquidacion] Medio de Pago | Medios de Pago |
| DTE/Liquidacion/Encabezado/IdDoc/TpoCtaPago | anonymous | No | 0..1 | xs:string | 5 | 10 | - | AHORRO, CORRIENTE, VISTA | [DTE choice opción 2: Liquidacion] Tipo Cuenta de Pago | - |
| DTE/Liquidacion/Encabezado/IdDoc/NumCtaPago | anonymous | No | 0..1 | xs:string | - | 20 | - | - | [DTE choice opción 2: Liquidacion] Número de la cuenta del pago | - |
| DTE/Liquidacion/Encabezado/IdDoc/BcoPago | anonymous | No | 0..1 | xs:string | - | 40 | - | - | [DTE choice opción 2: Liquidacion] Banco donde se realiza el pago | - |
| DTE/Liquidacion/Encabezado/IdDoc/TermPagoCdg | anonymous | No | 0..1 | xs:string | - | 4 | - | - | [DTE choice opción 2: Liquidacion] Codigo del Termino de Pago Acordado | - |
| DTE/Liquidacion/Encabezado/IdDoc/TermPagoGlosa | anonymous | No | 0..1 | xs:string | - | 100 | - | - | [DTE choice opción 2: Liquidacion] Términos del Pago - glosa | - |
| DTE/Liquidacion/Encabezado/IdDoc/TermPagoDias | anonymous | No | 0..1 | xs:positiveInteger | - | - | - | - | [DTE choice opción 2: Liquidacion] Dias de Acuerdo al Codigo de Termino de Pago | totalDigits=3 |
| DTE/Liquidacion/Encabezado/IdDoc/FchVenc | SiiDte:FechaType | No | 0..1 | xs:date | 2000-01-01 | 2050-12-31 | - | - | [DTE choice opción 2: Liquidacion] Fecha de Vencimiento del Pago (AAAA-MM-DD) | Fecha entre 2000-01-01 y 2050-12-31 |
| DTE/Liquidacion/Encabezado/Emisor | anonymous | Sí | 1..1 | - | - | - | - | - | [DTE choice opción 2: Liquidacion] Datos del Emisor | - |
| DTE/Liquidacion/Encabezado/Emisor/RUTEmisor | SiiDte:RUTType | Sí | 1..1 | xs:string | 3 | 10 | - | [0-9]+-([0-9]\|K) | [DTE choice opción 2: Liquidacion] RUT del Emisor del DTE | Rol Unico Tributario (99..99-X) |
| DTE/Liquidacion/Encabezado/Emisor/RznSoc | anonymous | Sí | 1..1 | xs:string | 1 | 100 | - | - | [DTE choice opción 2: Liquidacion] Nombre o Razon Social del Emisor | - |
| DTE/Liquidacion/Encabezado/Emisor/GiroEmis | anonymous | Sí | 1..1 | xs:string | 1 | 80 | - | - | [DTE choice opción 2: Liquidacion] Giro Comercial del Emisor Relevante para el DTE | - |
| DTE/Liquidacion/Encabezado/Emisor/Telefono | anonymous | No | 0..2 | SiiDte:FonoType | - | 20 | - | - | [DTE choice opción 2: Liquidacion] Telefono Emisor | - |
| DTE/Liquidacion/Encabezado/Emisor/CorreoEmisor | SiiDte:MailType | No | 0..1 | xs:string | - | 80 | - | - | [DTE choice opción 2: Liquidacion] Correo Elect. de contacto en empresa del receptor | Dirección email |
| DTE/Liquidacion/Encabezado/Emisor/Acteco | anonymous | Sí | 1..4 | xs:positiveInteger | - | - | - | - | [DTE choice opción 2: Liquidacion] Codigo de Actividad Economica del Emisor Relevante para el DTE | totalDigits=6 |
| DTE/Liquidacion/Encabezado/Emisor/Sucursal | anonymous | No | 0..1 | xs:string | - | 20 | - | - | [DTE choice opción 2: Liquidacion] Sucursal que Emite el DTE | - |
| DTE/Liquidacion/Encabezado/Emisor/CdgSIISucur | anonymous | No | 0..1 | xs:positiveInteger | - | - | - | - | [DTE choice opción 2: Liquidacion] Codigo de Sucursal Entregado por el SII | totalDigits=9 |
| DTE/Liquidacion/Encabezado/Emisor/DirOrigen | anonymous | Sí | 1..1 | xs:string | - | 70 | - | - | [DTE choice opción 2: Liquidacion] Direccion de Origen | - |
| DTE/Liquidacion/Encabezado/Emisor/CmnaOrigen | SiiDte:ComunaType | No | 0..1 | xs:string | - | 20 | - | - | [DTE choice opción 2: Liquidacion] Comuna de Origen | Comuna |
| DTE/Liquidacion/Encabezado/Emisor/CiudadOrigen | SiiDte:CiudadType | No | 0..1 | xs:string | - | 20 | - | - | [DTE choice opción 2: Liquidacion] Ciudad de Origen | Ciudad |
| DTE/Liquidacion/Encabezado/Emisor/CdgVendedor | anonymous | No | 0..1 | xs:string | - | 60 | - | - | [DTE choice opción 2: Liquidacion] Codigo del Vendedor | - |
| DTE/Liquidacion/Encabezado/Receptor | anonymous | Sí | 1..1 | - | - | - | - | - | [DTE choice opción 2: Liquidacion] Datos del Receptor | - |
| DTE/Liquidacion/Encabezado/Receptor/RUTRecep | SiiDte:RUTType | Sí | 1..1 | xs:string | 3 | 10 | - | [0-9]+-([0-9]\|K) | [DTE choice opción 2: Liquidacion] RUT del Receptor del DTE | Rol Unico Tributario (99..99-X) |
| DTE/Liquidacion/Encabezado/Receptor/CdgIntRecep | anonymous | No | 0..1 | xs:string | - | 20 | - | - | [DTE choice opción 2: Liquidacion] Codigo Interno del Receptor | - |
| DTE/Liquidacion/Encabezado/Receptor/RznSocRecep | SiiDte:RznSocLargaType | Sí | 1..1 | xs:string | - | 100 | - | - | [DTE choice opción 2: Liquidacion] Nombre o Razon Social del Receptor | Razón Social (max 100) |
| DTE/Liquidacion/Encabezado/Receptor/GiroRecep | anonymous | Sí | 1..1 | xs:string | - | 40 | - | - | [DTE choice opción 2: Liquidacion] Giro Comercial del Receptor | - |
| DTE/Liquidacion/Encabezado/Receptor/Contacto | anonymous | No | 0..1 | xs:string | - | 80 | - | - | [DTE choice opción 2: Liquidacion] Glosa con nombre o teléfono de contacto en empresa del receptor | - |
| DTE/Liquidacion/Encabezado/Receptor/CorreoRecep | SiiDte:MailType | No | 0..1 | xs:string | - | 80 | - | - | [DTE choice opción 2: Liquidacion] Correo Elect. de contacto en empresa del receptor | Dirección email |
| DTE/Liquidacion/Encabezado/Receptor/DirRecep | anonymous | Sí | 1..1 | xs:string | - | 70 | - | - | [DTE choice opción 2: Liquidacion] Direccion en la Cual se Envian los Productos o se Prestan los Servicios | - |
| DTE/Liquidacion/Encabezado/Receptor/CmnaRecep | SiiDte:ComunaType | Sí | 1..1 | xs:string | - | 20 | - | - | [DTE choice opción 2: Liquidacion] Comuna de Recepcion | Comuna |
| DTE/Liquidacion/Encabezado/Receptor/CiudadRecep | SiiDte:CiudadType | No | 0..1 | xs:string | - | 20 | - | - | [DTE choice opción 2: Liquidacion] Ciudad de Recepcion | Ciudad |
| DTE/Liquidacion/Encabezado/Receptor/DirPostal | anonymous | No | 0..1 | xs:string | - | 70 | - | - | [DTE choice opción 2: Liquidacion] Direccion Postal | - |
| DTE/Liquidacion/Encabezado/Receptor/CmnaPostal | SiiDte:ComunaType | No | 0..1 | xs:string | - | 20 | - | - | [DTE choice opción 2: Liquidacion] Comuna Postal | Comuna |
| DTE/Liquidacion/Encabezado/Receptor/CiudadPostal | SiiDte:CiudadType | No | 0..1 | xs:string | - | 20 | - | - | [DTE choice opción 2: Liquidacion] Ciudad Postal | Ciudad |
| DTE/Liquidacion/Encabezado/Totales | anonymous | Sí | 1..1 | - | - | - | - | - | [DTE choice opción 2: Liquidacion] Montos Totales del DTE | - |
| DTE/Liquidacion/Encabezado/Totales/MntNeto | SiiDte:ValorType | No | 0..1 | xs:integer | - | - | - | - | [DTE choice opción 2: Liquidacion] Monto Neto del DTE | totalDigits=18; Monto de 18 digitos - Positivo o Negativo |
| DTE/Liquidacion/Encabezado/Totales/MntExe | SiiDte:ValorType | No | 0..1 | xs:integer | - | - | - | - | [DTE choice opción 2: Liquidacion] Monto Exento del DTE | totalDigits=18; Monto de 18 digitos - Positivo o Negativo |
| DTE/Liquidacion/Encabezado/Totales/TasaIVA | SiiDte:PctType | No | 0..1 | xs:decimal | 0.01 | 999.99 | - | - | [DTE choice opción 2: Liquidacion] Tasa de IVA | totalDigits=5; fractionDigits=2; Monto de Porcentaje ( 3 y 2) |
| DTE/Liquidacion/Encabezado/Totales/IVA | SiiDte:ValorType | No | 0..1 | xs:integer | - | - | - | - | [DTE choice opción 2: Liquidacion] Monto de IVA del DTE | totalDigits=18; Monto de 18 digitos - Positivo o Negativo |
| DTE/Liquidacion/Encabezado/Totales/IVAProp | SiiDte:ValorType | No | 0..1 | xs:integer | - | - | - | - | [DTE choice opción 2: Liquidacion] Monto del IVA propio | totalDigits=18; Monto de 18 digitos - Positivo o Negativo |
| DTE/Liquidacion/Encabezado/Totales/IVATerc | SiiDte:ValorType | No | 0..1 | xs:integer | - | - | - | - | [DTE choice opción 2: Liquidacion] Monto del IVA de Terceros | totalDigits=18; Monto de 18 digitos - Positivo o Negativo |
| DTE/Liquidacion/Encabezado/Totales/ImptoReten | anonymous | No | 0..20 | - | - | - | - | - | [DTE choice opción 2: Liquidacion] Impuestos y Retenciones Adicionales | - |
| DTE/Liquidacion/Encabezado/Totales/ImptoReten/TipoImp | SiiDte:ImpAdicDTEType | Sí | 1..1 | xs:string | - | 3 | - | 14, 15, 16, 17, 18, 19, 23, 24, 25, 26, 27, 28, 30, 31, 32, 33, 34, 35, 36, 37 ... (44 valores) | [DTE choice opción 2: Liquidacion] Tipo de Impuesto o Retencion Adicional | Tipo de Impuesto o Retencion Adicional de los DTE |
| DTE/Liquidacion/Encabezado/Totales/ImptoReten/TasaImp | SiiDte:PctType | No | 0..1 | xs:decimal | 0.01 | 999.99 | - | - | [DTE choice opción 2: Liquidacion] Tasa de Impuesto o Retencion | totalDigits=5; fractionDigits=2; Monto de Porcentaje ( 3 y 2) |
| DTE/Liquidacion/Encabezado/Totales/ImptoReten/MontoImp | SiiDte:ValorType | Sí | 1..1 | xs:integer | - | - | - | - | [DTE choice opción 2: Liquidacion] Monto del Impuesto o Retencion | totalDigits=18; Monto de 18 digitos - Positivo o Negativo |
| DTE/Liquidacion/Encabezado/Totales/Comisiones | anonymous | No | 0..1 | - | - | - | - | - | [DTE choice opción 2: Liquidacion] Comisiones y otros cargos es obligatoria para Liquidaciones Factura | - |
| DTE/Liquidacion/Encabezado/Totales/Comisiones/ValComNeto | SiiDte:ValorType | No | 0..1 | xs:integer | - | - | - | - | [DTE choice opción 2: Liquidacion] Valor Neto Comisiones y Otros Cargos | totalDigits=18; Monto de 18 digitos - Positivo o Negativo |
| DTE/Liquidacion/Encabezado/Totales/Comisiones/ValComExe | SiiDte:ValorType | No | 0..1 | xs:integer | - | - | - | - | [DTE choice opción 2: Liquidacion] Val. Comis. y Otros Cargos no Afectos o Exentos | totalDigits=18; Monto de 18 digitos - Positivo o Negativo |
| DTE/Liquidacion/Encabezado/Totales/Comisiones/ValComIVA | SiiDte:ValorType | No | 0..1 | xs:integer | - | - | - | - | [DTE choice opción 2: Liquidacion] Valor IVA Comisiones y Otros Cargos | totalDigits=18; Monto de 18 digitos - Positivo o Negativo |
| DTE/Liquidacion/Encabezado/Totales/MntTotal | SiiDte:ValorType | Sí | 1..1 | xs:integer | - | - | - | - | [DTE choice opción 2: Liquidacion] Monto Total del DTE | totalDigits=18; Monto de 18 digitos - Positivo o Negativo |
| DTE/Liquidacion/Encabezado/Totales/MontoPeriodo | SiiDte:ValorType | No | 0..1 | xs:integer | - | - | - | - | [DTE choice opción 2: Liquidacion] Total de Ventas o Servicios del Periodo | totalDigits=18; Monto de 18 digitos - Positivo o Negativo |
| DTE/Liquidacion/Encabezado/Totales/SaldoAnterior | SiiDte:ValorType | No | 0..1 | xs:integer | - | - | - | - | [DTE choice opción 2: Liquidacion] Saldo Anterior - Puede ser Negativo o Positivo | totalDigits=18; Monto de 18 digitos - Positivo o Negativo |
| DTE/Liquidacion/Encabezado/Totales/VlrPagar | SiiDte:ValorType | No | 0..1 | xs:integer | - | - | - | - | [DTE choice opción 2: Liquidacion] Valor a Pagar Total del documento | totalDigits=18; Monto de 18 digitos - Positivo o Negativo |
| DTE/Liquidacion/Detalle | anonymous | Sí | 1..60 | - | - | - | - | - | [DTE choice opción 2: Liquidacion] Detalle de Itemes del Documento | - |
| DTE/Liquidacion/Detalle/NroLinDet | anonymous | Sí | 1..1 | xs:positiveInteger | - | 99 | - | - | [DTE choice opción 2: Liquidacion] Numero Secuencial de Linea | - |
| DTE/Liquidacion/Detalle/CdgItem | anonymous | No | 0..5 | - | - | - | - | - | [DTE choice opción 2: Liquidacion] Codificacion del Item | - |
| DTE/Liquidacion/Detalle/CdgItem/TpoCodigo | anonymous | Sí | 1..1 | xs:string | - | 10 | - | - | [DTE choice opción 2: Liquidacion] Tipo de Codificacion | - |
| DTE/Liquidacion/Detalle/CdgItem/VlrCodigo | anonymous | Sí | 1..1 | xs:string | - | 35 | - | - | [DTE choice opción 2: Liquidacion] Valor del Codigo de Item, para la Codificacion Particular | - |
| DTE/Liquidacion/Detalle/TpoDocLiq | anonymous | Sí | 1..1 | xs:string | 1 | 3 | - | - | [DTE choice opción 2: Liquidacion] Tipo de Documento que se Liquida | - |
| DTE/Liquidacion/Detalle/IndExe | anonymous | No | 0..1 | xs:positiveInteger | - | - | - | 1, 2, 3, 4, 5, 6 | [DTE choice opción 2: Liquidacion] Indicador de Exencion/Facturacion | - |
| DTE/Liquidacion/Detalle/NmbItem | anonymous | Sí | 1..1 | xs:string | - | 80 | - | - | [DTE choice opción 2: Liquidacion] Nombre del Item | - |
| DTE/Liquidacion/Detalle/DscItem | anonymous | No | 0..1 | xs:string | - | 1000 | - | - | [DTE choice opción 2: Liquidacion] Descripcion del Item | - |
| DTE/Liquidacion/Detalle/QtyRef | SiiDte:Dec12_6Type | No | 0..1 | xs:decimal | 0.000001 | 999999999999.999999 | - | - | [DTE choice opción 2: Liquidacion] Cantidad para la Unidad de Medida de Referencia | totalDigits=18; fractionDigits=6; Monto con 12 Digitos de Cuerpo y 6 Decimales |
| DTE/Liquidacion/Detalle/UnmdRef | anonymous | No | 0..1 | xs:string | - | 4 | - | - | [DTE choice opción 2: Liquidacion] Unidad de Medida de Referencia | - |
| DTE/Liquidacion/Detalle/PrcRef | SiiDte:Dec12_6Type | No | 0..1 | xs:decimal | 0.000001 | 999999999999.999999 | - | - | [DTE choice opción 2: Liquidacion] Precio Unitario de Referencia para Unidad de Referencia | totalDigits=18; fractionDigits=6; Monto con 12 Digitos de Cuerpo y 6 Decimales |
| DTE/Liquidacion/Detalle/QtyItem | SiiDte:Dec12_6Type | No | 0..1 | xs:decimal | 0.000001 | 999999999999.999999 | - | - | [DTE choice opción 2: Liquidacion] Cantidad del Item | totalDigits=18; fractionDigits=6; Monto con 12 Digitos de Cuerpo y 6 Decimales |
| DTE/Liquidacion/Detalle/Subcantidad | anonymous | No | 0..5 | - | - | - | - | - | [DTE choice opción 2: Liquidacion] Distribucion de la Cantidad | - |
| DTE/Liquidacion/Detalle/Subcantidad/SubQty | SiiDte:Dec12_6Type | Sí | 1..1 | xs:decimal | 0.000001 | 999999999999.999999 | - | - | [DTE choice opción 2: Liquidacion] Cantidad Distribuida | totalDigits=18; fractionDigits=6; Monto con 12 Digitos de Cuerpo y 6 Decimales |
| DTE/Liquidacion/Detalle/Subcantidad/SubCod | anonymous | Sí | 1..1 | xs:string | - | 35 | - | - | [DTE choice opción 2: Liquidacion] Codigo Descriptivo de la Subcantidad | - |
| DTE/Liquidacion/Detalle/FchElabor | SiiDte:FechaType | No | 0..1 | xs:date | 2000-01-01 | 2050-12-31 | - | - | [DTE choice opción 2: Liquidacion] Fecha Elaboracion del Item | Fecha entre 2000-01-01 y 2050-12-31 |
| DTE/Liquidacion/Detalle/FchVencim | SiiDte:FechaType | No | 0..1 | xs:date | 2000-01-01 | 2050-12-31 | - | - | [DTE choice opción 2: Liquidacion] Fecha Vencimiento del Item | Fecha entre 2000-01-01 y 2050-12-31 |
| DTE/Liquidacion/Detalle/UnmdItem | anonymous | No | 0..1 | xs:string | - | 4 | - | - | [DTE choice opción 2: Liquidacion] Unidad de Medida | - |
| DTE/Liquidacion/Detalle/PrcItem | SiiDte:Dec12_6Type | No | 0..1 | xs:decimal | 0.000001 | 999999999999.999999 | - | - | [DTE choice opción 2: Liquidacion] Precio Unitario del Item en Pesos | totalDigits=18; fractionDigits=6; Monto con 12 Digitos de Cuerpo y 6 Decimales |
| DTE/Liquidacion/Detalle/CodImpAdic | SiiDte:ImpAdicDTEType | No | 0..2 | xs:string | - | 3 | - | 14, 15, 16, 17, 18, 19, 23, 24, 25, 26, 27, 28, 30, 31, 32, 33, 34, 35, 36, 37 ... (44 valores) | [DTE choice opción 2: Liquidacion] Codigo de Impuesto Adicional o Retencion | Tipo de Impuesto o Retencion Adicional de los DTE |
| DTE/Liquidacion/Detalle/MontoItem | SiiDte:ValorType | Sí | 1..1 | xs:integer | - | - | - | - | [DTE choice opción 2: Liquidacion] Monto por Linea de Detalle. Corresponde al Monto Neto, a menos que MntBruto Indique lo Contrario | totalDigits=18; Monto de 18 digitos - Positivo o Negativo |
| DTE/Liquidacion/SubTotInfo | anonymous | No | 0..20 | - | - | - | - | - | [DTE choice opción 2: Liquidacion] Subtotales Informativos | - |
| DTE/Liquidacion/SubTotInfo/NroSTI | anonymous | Sí | 1..1 | xs:positiveInteger | - | 99 | - | - | [DTE choice opción 2: Liquidacion] Número de Subtotal | - |
| DTE/Liquidacion/SubTotInfo/GlosaSTI | anonymous | Sí | 1..1 | xs:string | - | 40 | - | - | [DTE choice opción 2: Liquidacion] Glosa | - |
| DTE/Liquidacion/SubTotInfo/OrdenSTI | anonymous | No | 0..1 | xs:positiveInteger | - | 99 | - | - | [DTE choice opción 2: Liquidacion] Ubicación para Impresión | - |
| DTE/Liquidacion/SubTotInfo/SubTotNetoSTI | SiiDte:Dec16_2Type | No | 0..1 | xs:decimal | 0.01 | 9999999999999999.99 | - | - | [DTE choice opción 2: Liquidacion] Valor Neto del Subtotal | totalDigits=18; fractionDigits=2; Monto con 16 Digitos de Cuerpo y 2 Decimales |
| DTE/Liquidacion/SubTotInfo/SubTotIVASTI | SiiDte:Dec16_2Type | No | 0..1 | xs:decimal | 0.01 | 9999999999999999.99 | - | - | [DTE choice opción 2: Liquidacion] Valor del IVA del Subtotal | totalDigits=18; fractionDigits=2; Monto con 16 Digitos de Cuerpo y 2 Decimales |
| DTE/Liquidacion/SubTotInfo/SubTotAdicSTI | SiiDte:Dec16_2Type | No | 0..1 | xs:decimal | 0.01 | 9999999999999999.99 | - | - | [DTE choice opción 2: Liquidacion] Valor de los Impuestos adicionales o específicos del Subtotal | totalDigits=18; fractionDigits=2; Monto con 16 Digitos de Cuerpo y 2 Decimales |
| DTE/Liquidacion/SubTotInfo/SubTotExeSTI | SiiDte:Dec16_2Type | No | 0..1 | xs:decimal | 0.01 | 9999999999999999.99 | - | - | [DTE choice opción 2: Liquidacion] Valor no Afecto o Exento del Subtotal | totalDigits=18; fractionDigits=2; Monto con 16 Digitos de Cuerpo y 2 Decimales |
| DTE/Liquidacion/SubTotInfo/ValSubtotSTI | SiiDte:Dec16_2Type | No | 0..1 | xs:decimal | 0.01 | 9999999999999999.99 | - | - | [DTE choice opción 2: Liquidacion] Valor de la línea de subtotal | totalDigits=18; fractionDigits=2; Monto con 16 Digitos de Cuerpo y 2 Decimales |
| DTE/Liquidacion/SubTotInfo/LineasDeta | anonymous | No | 0..60 | xs:positiveInteger | - | - | - | - | [DTE choice opción 2: Liquidacion] TABLA de Líneas de Detalle que se agrupan en el Subtotal | - |
| DTE/Liquidacion/Referencia | anonymous | No | 0..40 | - | - | - | - | - | [DTE choice opción 2: Liquidacion] Identificacion de otros documentos Referenciados por Documento | - |
| DTE/Liquidacion/Referencia/NroLinRef | anonymous | Sí | 1..1 | xs:positiveInteger | - | 99 | - | - | [DTE choice opción 2: Liquidacion] Numero Secuencial de Linea de Referencia | - |
| DTE/Liquidacion/Referencia/TpoDocRef | anonymous | Sí | 1..1 | xs:string | 1 | 3 | - | - | [DTE choice opción 2: Liquidacion] Tipo de Documento de Referencia | - |
| DTE/Liquidacion/Referencia/IndGlobal | anonymous | No | 0..1 | xs:nonNegativeInteger | - | - | - | 1 | [DTE choice opción 2: Liquidacion] Indica que se esta Referenciando un Conjunto de Documentos | totalDigits=1 |
| DTE/Liquidacion/Referencia/FolioRef | SiiDte:FolioRType | Sí | 1..1 | xs:string | 1 | 18 | - | - | [DTE choice opción 2: Liquidacion] Folio del Documento de Referencia | Folio de Referencia - 18 digitos (incluye el cero) |
| DTE/Liquidacion/Referencia/FchRef | SiiDte:FechaType | Sí | 1..1 | xs:date | 2000-01-01 | 2050-12-31 | - | - | [DTE choice opción 2: Liquidacion] Fecha de la Referencia | Fecha entre 2000-01-01 y 2050-12-31 |
| DTE/Liquidacion/Referencia/CodRef | anonymous | No | 0..1 | xs:positiveInteger | - | - | - | 1, 2, 3 | [DTE choice opción 2: Liquidacion] Tipo de Uso de la Referencia | - |
| DTE/Liquidacion/Referencia/RazonRef | anonymous | No | 0..1 | xs:string | - | 90 | - | - | [DTE choice opción 2: Liquidacion] Razon Explicita por la que se Referencia el Documento | - |
| DTE/Liquidacion/Comisiones | anonymous | No | 0..20 | - | - | - | - | - | [DTE choice opción 2: Liquidacion] Comisiones y otros cargos es obligatoria para Liquidaciones Factura | - |
| DTE/Liquidacion/Comisiones/NroLinCom | anonymous | Sí | 1..1 | xs:positiveInteger | - | 20 | - | - | [DTE choice opción 2: Liquidacion] Numero Secuencial de Linea | totalDigits=2 |
| DTE/Liquidacion/Comisiones/TipoMovim | anonymous | Sí | 1..1 | xs:string | 1 | 1 | - | C, O | [DTE choice opción 2: Liquidacion] C (comisión) u O (otros cargos) | - |
| DTE/Liquidacion/Comisiones/Glosa | anonymous | Sí | 1..1 | xs:string | 1 | 60 | - | - | [DTE choice opción 2: Liquidacion] Especificación de la comisión u otro cargo | - |
| DTE/Liquidacion/Comisiones/TasaComision | SiiDte:PctType | No | 0..1 | xs:decimal | 0.01 | 999.99 | - | - | [DTE choice opción 2: Liquidacion] Valor porcentual de la comisión u otro cargo | totalDigits=5; fractionDigits=2; Monto de Porcentaje ( 3 y 2) |
| DTE/Liquidacion/Comisiones/ValComNeto | SiiDte:ValorType | Sí | 1..1 | xs:integer | - | - | - | - | [DTE choice opción 2: Liquidacion] Valor Neto Comisiones y Otros Cargos | totalDigits=18; Monto de 18 digitos - Positivo o Negativo |
| DTE/Liquidacion/Comisiones/ValComExe | SiiDte:ValorType | Sí | 1..1 | xs:integer | - | - | - | - | [DTE choice opción 2: Liquidacion] Val. Comis. y Otros Cargos no Afectos o Exentos | totalDigits=18; Monto de 18 digitos - Positivo o Negativo |
| DTE/Liquidacion/Comisiones/ValComIVA | SiiDte:ValorType | No | 0..1 | xs:integer | - | - | - | - | [DTE choice opción 2: Liquidacion] Valor IVA Comisiones y Otros Cargos | totalDigits=18; Monto de 18 digitos - Positivo o Negativo |