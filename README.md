PS D:\Universidad\Programacion Middleware\middleware-pe21> # (a) Sin API key -> esperado: 401
>> curl http://localhost:3000/health
>> 
curl : {"error":"API key inválida o ausente"}
En línea: 2 Carácter: 1
+ curl http://localhost:3000/health
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation:  
   (System.Net.HttpWebRequest:HttpWebRequest) [  
  Invoke-WebRequest], WebException
    + FullyQualifiedErrorId : WebCmdletWebRespon 
   seException,Microsoft.PowerShell.Commands.In  
  vokeWebRequestCommand
PS D:\Universidad\Programacion Middleware\middleware-pe21> # (b) Con clave válida -> esperado: 200
>> curl -H "x-api-key: secreto-demo" http://localhost:3000/health
>> 
Invoke-WebRequest : No se puede enlazar el 
parámetro 'Headers'. No se puede convertir el 
valor "x-api-key: secreto-demo" de tipo 
"System.String" al tipo 
"System.Collections.IDictionary".
En línea: 2 Carácter: 9
+ curl -H "x-api-key: secreto-demo" 
http://localhost:3000/health
+         ~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: ( 
   :) [Invoke-WebRequest], ParameterBindingExce  
  ption
    + FullyQualifiedErrorId : CannotConvertArgum 
   entNoMessage,Microsoft.PowerShell.Commands.I  
  nvokeWebRequestCommand
 
PS D:\Universidad\Programacion Middleware\middleware-pe21> # (c) Ruta inexistente -> esperado: 404
>> curl -H "x-api-key: secreto-demo" http://localhost:3000/noexiste
>> 
Invoke-WebRequest : No se puede enlazar el 
parámetro 'Headers'. No se puede convertir el 
valor "x-api-key: secreto-demo" de tipo 
"System.String" al tipo 
"System.Collections.IDictionary".
En línea: 2 Carácter: 9
+ curl -H "x-api-key: secreto-demo" 
http://localhost:3000/noexiste
+         ~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: ( 
   :) [Invoke-WebRequest], ParameterBindingExce  
  ption
    + FullyQualifiedErrorId : CannotConvertArgum 
   entNoMessage,Microsoft.PowerShell.Commands.I  
  nvokeWebRequestCommand
 
PS D:\Universidad\Programacion Middleware\middleware-pe21> 


PS D:\Universidad\Programacion Middleware\middleware-pe21> Invoke-RestMethod -Method POST "http://localhost:3000/v1/inscripciones" `
>>   -Headers @{ "x-api-key" = "secreto-demo" } `
>>   -ContentType "application/json" `
>>   -Body '{"estudianteId":"uuid-123","materias":["LTI_05A_458"],"periodoId":"2026-1"}'

version estudianteId materias      periodoId
------- ------------ --------      ---------
v1      uuid-123     {LTI_05A_458} 2026-1   


PS D:\Universidad\Programacion Middleware\middleware-pe21> Invoke-RestMethod -Method POST "http://localhost:3000/v2/inscripciones" `
>>   -Headers @{ "x-api-key" = "secreto-demo" } `
>>   -ContentType "application/json" `
>>   -Body '{"estudianteId":"uuid-123","materias":["LTI_05A_458"],"periodoId":"2026-1","payment_method":"scholarship"}'


version        : v2
estudianteId   : uuid-123
materias       : {LTI_05A_458}
periodoId      : 2026-1
payment_method : scholarship



PS D:\Universidad\Programacion Middleware\middleware-pe21> Invoke-RestMethod -Method POST "http://localhost:3000/v2/inscripciones" `
>>   -Headers @{ "x-api-key" = "secreto-demo" } `
>>   -ContentType "application/json" `
>>   -Body '{"estudianteId":"uuid-123","materias":["LTI_05A_458"],"periodoId":"2026-1"}'
Invoke-RestMethod : {"error":"Campos requeridos: estudianteId, materias, periodoId, 
payment_method"}
En línea: 1 Carácter: 1
+ Invoke-RestMethod -Method POST "http://localhost:3000/v2/inscripcione ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (System.Net.HttpWebRequest:HttpWebRequest 
   ) [Invoke-RestMethod], WebException
    + FullyQualifiedErrorId : WebCmdletWebResponseException,Microsoft.PowerShell.Commands 
   .InvokeRestMethodCommand
PS D:\Universidad\Programacion Middleware\middleware-pe21> 
PS D:\Universidad\Programacion Middleware\middleware-pe21> Invoke-RestMethod -Method POST "http://localhost:3000/v2/inscripciones" `
>>   -Headers @{ "x-api-key" = "secreto-demo" } `
>>   -ContentType "application/json" `
>>   -Body '{"estudianteId":"uuid-123","materias":["LTI_05A_458"],"periodoId":"2026-1","payment_method":"cash"}'
Invoke-RestMethod : {"error":"payment_method inválido. Valores: debit, credit, 
scholarship"}
En línea: 1 Carácter: 1
+ Invoke-RestMethod -Method POST "http://localhost:3000/v2/inscripcione ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (System.Net.HttpWebRequest:HttpWebRequest 
   ) [Invoke-RestMethod], WebException
    + FullyQualifiedErrorId : WebCmdletWebResponseException,Microsoft.PowerShell.Commands 
   .InvokeRestMethodCommand
PS D:\Universidad\Programacion Middleware\middleware-pe21> 