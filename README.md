# Pagos con OTP

A continuación se detalla el proceso para integrarse con el estadar para pagos con OTP de Nequi.

Esta integración le permite a cualquier comercio recibir pagos de clientes Nequi mediante un OTP generado dentro de la aplicación, este OTP debe ser entregado al comercio para que este realice un pago por determinado valor mediante un API.

El estandar esta compuesto por tres servicios REST usando mensajeria JSON y utlizando un mecanismo de autenticación basado en [OAuth 2.0](https://oauth.net/2/)

Para realizar su integración siga las instrucciones detalladas para cada servicio, pero antes inicie con la [autenticacíón](./authentication.md).

## Servicios expuestos

- [Realizar un pago](./requestPayment.md)
- [Cancelar un pago](./cancelPayment.md)
- [Reversar un pago](./reversePayment.md)

En caso de tener dudas o inconvenientes para integrarse ingrese en nuestro canal de slack para desarrolladores en el siguiente [enlace](https://join.slack.com/t/nequidev/shared_invite/enQtMzc1Njc3NzU5MTExLTgyYmZkMmM1ODlhMmVhM2MyMDkyMGUwMTNiOTZkZTEyYzAwOTFkOGQ2ZTBlMTZmOTg1YzA1NTliOGVkM2ZjZjM).

Made with ♥ by [Nequi](https://nequi.com)
