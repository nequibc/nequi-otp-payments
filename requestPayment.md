# Servicio para realizar un pago con OTP

Este servicio permite realizar un pago con código OTP generado por un usuario desde Nequi. El valor del pago es acreditado al comercio que consume este servicio.

## Características del servicio

- Es un servicio HTTPS REST
- Para la autentificación se utiliza el método [OAuth 2.0](https://oauth.net/2/). (Ver [guía](./authentication.md))
- Se debe consumir mediante el método POST

Las urls para el consumo del servicio son:

- QA: [https://api.sandbox.nequi.com/otp-payments/v1/requestPayment](https://api.sandbox.nequi.com/otp-payments/v1/requestPayment)
- PDN: [https://api.nequi.com/otp-payments/v1/requestPayment](https://api.nequi.com/otp-payments/v1/requestPayment)

## Request

    {
       "traceId": "99a2a169-6a3d-4d7e-80e4-7eb02948d2b2",
       "code": "NIT_1",
       "value": "10",
       "token": "654321",
       "terminalId": "5468"
    }

| **Campo** | **Tipo** | **Descripción** |
-- | -- | --
| traceId | string | Identificador único para trazabilidad |
| code | string | Código del comercio formado por TIPO_ID. Para pruebas utilizar valor por defecto NIT_1 |
| value | string | Valor de la transacción |
| token | string | Código a validar |
| terminalId | string | Campo opcional, hace referencia al identificador de la caja o terminal donde se realiza el pago |  

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
| traceId | string | Identificador único para trazabilidad |
| response | boolean | Indica si la transacción fue exitosa o fallida |
| message | string | Mensaje del servicio |
| messageDetail | string | Detalle de la operación |
| verificationCode | string | Código de verificación de la transacción |

### Códigos de respuesta

| **Código HTTP** | **message** | **messageDetail** |
| -- | -- | -- |
| 200 | OK | La solicitud se ejecutó correctamente |
| 400 | Bad Request |La solicitud no se puede procesar, problemas con la estructura de la solicitud o el saldo del cliente es insuficiente para realizar el pago |
| 403 | Access Denied |Consumo del servicio denegado para el comercio |
| 404 | Not Found |Código OTP no encontrado |
| 500 | Internal server error | Se presentó una falla en la operación del servicio, no se pudo procesar la solicitud |

Made with ♥ by [Nequi](https://nequi.com)
