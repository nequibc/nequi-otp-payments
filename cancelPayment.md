# Servicio para cancelar un pago con OTP

Este servicio permite realizar la cancelación de un pago con OTP que se haya realizado en el mismo día.

## Características del servicio

- Es un servicio HTTPS REST
- Para la autentificación se utiliza el método [OAuth 2.0](https://oauth.net/2/). (Ver [guía](./authentication.md))
- Se debe consumir mediante el método POST

Las urls para el consumo del servicio son:

- QA: [https://api.sandbox.nequi.com/otp-payments/v1/requestCancel](https://api.sandbox.nequi.com/otp-payments/v1/requestCancel)
- PDN: [https://api.nequi.com/otp-payments/v1/requestCancel](https://api.nequi.com/otp-payments/v1/requestCancel)

## Request

    {
        "traceId": "99a2a169-6a3d-4d7e-80e4-7eb02948d2b2",
        "value": "10",
        "code": "NIT_1"
    }

| **Campo** | **Tipo** | **Descripción** |
-- | -- | --
| traceId | string | Identificador único de la transacción a cancelar |
| code | string | Código del comercio formado por TIPO_ID. Para pruebas utilizar valor por defecto NIT_1 |
| value | string | Valor de la transacción |

## Response

    {
        "traceId": "99a2a169-6a3d-4d7e-80e4-7eb02948d2b2",
        "response": true,
        "message": "Success",
        "messageDetail": "La solicitud se ejecutó correctamente y se obtuvo una respuesta positiva",
        "verificationCode" : "350-10011-0111121"
    }

| **Campo** | **Tipo** | **Descripción** |
-- | -- | --
| traceId | string | Identificador único de la transacción a cancelar |
| response | boolean | Indica si la transacción exitosa o fallida |
| message | string | Mensaje del servicio |
| messageDetail | string | Detalle de la operación |
| verificationCode | string | Código de verificación de la transacción |

### Códigos de respuesta

| **Código** | **Mensaje** | **Descripción** |
| -- | -- | -- |
| 200 | OK | La solicitud se ejecutó correctamente |
| 400 | Bad Request | La solicitud no se puede procesar, problemas con la estructura de la solicitud o el saldo del cliente es insuficiente para realizar el pago |
| 403 | Access Denied |Consumo del servicio denegado para el comercio |
| 404 | Not found | No se encuentra transacción asociada al traceId enviado|
| 500 | Internal server error | Se presentó una falla en la operación del servicio, no se pudo procesar la solicitud |

Made with ♥ by [Nequi](https://nequi.com)
