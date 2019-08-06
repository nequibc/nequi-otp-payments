# Autenticación para el consumo de los servicios

Los servicios expuestos en este API estan autenticados mediante el mecanismo de [OAuth 2.0](https://oauth.net/2/).

Para poder consumirlos necesitará obtener un token de acceso y enviarlo en la cabecera **Authorization** precedido de la palabra *Bearer*.

Para obtener el token primero necesitará de un App client id y un App client secret que puede solicitar en el siguiente [enlace](https://join.slack.com/t/nequidev/shared_invite/enQtMzc1Njc3NzU5MTExLTgyYmZkMmM1ODlhMmVhM2MyMDkyMGUwMTNiOTZkZTEyYzAwOTFkOGQ2ZTBlMTZmOTg1YzA1NTliOGVkM2ZjZjM), luego deberá consumir el servicio de autenticación expuesto en el siguiente host segun el ambiente requerido:

- QA: [https://oauth.sandbox.nequi.com](https://oauth.sandbox.nequi.com)
- PDN: [https://oauth.nequi.com](https://oauth.nequi.com)

Agregar al host el siguiente path: _/oauth2/token?grant_type=client_credentials_

Y enviar en la cabecera **Content-Type** el valor _application/x-www-form-urlencoded_

Además, este servicio debe ser consumido mediante el método HTTP **POST** usando el mecanismo de autenticación **Basic** siendo el App client id el username y el App client secret el password.

## Response

A continuación se presenta un ejemplo de la respuesta de este servicio:

    {
        "access_token": "eyJraWQiOiJuZVhiaFBIVkREV3IxXC9sZTl2YVdVQ0laNHlrSHZsUkF0bjFGajBRSVU3WT0iLCJhbGciOiJSUzI1NiJ9.eyJzdWIiOiI1azY1N2gxOTBicG9xajE3cGZ1ZXN0a3FrcSIsInRva2VuX3VzZSI6ImFjY2VzcyIsInNjb3BlIjoib3RoZXJcL290aGVyIiwiYXV0aF90aW1lIjoxNTY1MDYyMTM1LCJpc3MiOiJodHRwczpcL1wvY29nbml0by1pZHAudXMtZWFzdC0xLmFtYXpvbmF3cy5jb21cL3VzLWVhc3QtMV9tNm9tT0JxQ1kiLCJleHAiOjE1NjUwNjU3MzUsImlhdCI6MTU2NTA2MjEzNSwidmVyc2lvbiI6MiwianRpIjoiYmQ2NGZlY2EtMTIxOS00NDhmLTkxN2UtMmUyYmU0NDgwNWE3IiwiY2xpZW50X2lkIjoiNWs2NTdoMTkwYnBvcWoxN3BmdWVzdGtxa3EifQ.IryJj8pCqcW9vJ-V-FVjA8f9AXFuKeVsOMA0GD61r4hkmgC-DRkNhcpFTqfqwFcxUk_7NVhEvIzCDelaI_hdODr6s1MuhVLWSa1PoompU1ZEDrQn2L5aR-rfdNaRH7mWI4DR_xRjIghoWOMgKPfkz1KgZx1FmeXZaD3cCFcxLb7zIR_aWC9az5s3tpoFPMjBXY_NtNOL6RmRZPJqlQJ0CwB9qPsvNDFStoSIxTqLOuvwF7vIJBt-3Nf5IjSRDP1KVUEYSe2RlmTxEcsrCU1QOQKUMhuejhE9_EHF7BPqBGeJWu3OXtNKwad_cimoWHyfAmGFHhggyoe1E3DXDSuWYg",
        "expires_in": 3600,
        "token_type": "Bearer"
    }

| **Campo** | **Tipo** | **Descripción** |
-- | -- | --
| access_token | string | Token para el consumo de los servicios |
| expires_in | number | Segundos restantes para la expiración del token |
| token_type | string | Tipo de token |

Si tiene dudas con este mecanismo de autenticación puede revisar la documentación de [OAuth 2.0](https://oauth.net/2/) o escribirnos en nuestro canal de [Slack](https://join.slack.com/t/nequidev/shared_invite/enQtMzc1Njc3NzU5MTExLTgyYmZkMmM1ODlhMmVhM2MyMDkyMGUwMTNiOTZkZTEyYzAwOTFkOGQ2ZTBlMTZmOTg1YzA1NTliOGVkM2ZjZjM).

Made with ♥ by [Nequi](https://nequi.com)
